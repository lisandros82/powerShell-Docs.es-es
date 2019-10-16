---
title: Vista amplia (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367954"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="bcb90-102">Vista amplia (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="bcb90-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="bcb90-103">En este ejemplo se muestra cómo implementar una vista amplia que muestra grupos de [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos devueltos por el cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="bcb90-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="bcb90-104">Para obtener más información sobre los componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="bcb90-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="bcb90-105">Para cargar este archivo de formato</span><span class="sxs-lookup"><span data-stu-id="bcb90-105">To load this formatting file</span></span>

1. <span data-ttu-id="bcb90-106">Copie el XML de la sección de ejemplo de este tema en un archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="bcb90-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="bcb90-107">Guarde el archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="bcb90-107">Save the text file.</span></span> <span data-ttu-id="bcb90-108">Asegúrese de agregar la extensión `format.ps1xml` al archivo para identificarlo como un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="bcb90-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="bcb90-109">Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="bcb90-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="bcb90-110">Este archivo de formato define la presentación de un objeto que ya está definido por los archivos de formato de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bcb90-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="bcb90-111">Debe usar el parámetro `prependPath` al ejecutar el cmdlet y no puede cargar este archivo de formato como un módulo.</span><span class="sxs-lookup"><span data-stu-id="bcb90-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="bcb90-112">Demuestra</span><span class="sxs-lookup"><span data-stu-id="bcb90-112">Demonstrates</span></span>

<span data-ttu-id="bcb90-113">Este archivo de formato muestra los siguientes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="bcb90-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="bcb90-114">Elemento [Name](./name-element-for-view-format.md) de la vista.</span><span class="sxs-lookup"><span data-stu-id="bcb90-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="bcb90-115">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) que define qué objetos se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="bcb90-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="bcb90-116">El elemento [GroupBy](./groupby-element-for-view-format.md) que define cuándo se muestra un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="bcb90-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="bcb90-117">El elemento [WideItem](./wideitem-element-for-widecontrol-format.md) que define la propiedad que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="bcb90-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="bcb90-118">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bcb90-118">Example</span></span>

<span data-ttu-id="bcb90-119">En el código XML siguiente se define una vista amplia que muestra grupos de objetos.</span><span class="sxs-lookup"><span data-stu-id="bcb90-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="bcb90-120">Cada nuevo grupo se inicia cuando cambia el valor de la propiedad [System. ServiceProcess. ServiceController. serviceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .</span><span class="sxs-lookup"><span data-stu-id="bcb90-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="bcb90-121">En el ejemplo siguiente se muestra cómo Windows PowerShell muestra [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de cargar este archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="bcb90-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="bcb90-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="bcb90-122">See Also</span></span>

[<span data-ttu-id="bcb90-123">Ejemplos de archivos de formato</span><span class="sxs-lookup"><span data-stu-id="bcb90-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="bcb90-124">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bcb90-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
