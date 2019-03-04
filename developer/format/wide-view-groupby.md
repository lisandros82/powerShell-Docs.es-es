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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861631"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="89d40-102">Vista amplia (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="89d40-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="89d40-103">¿En este ejemplo se muestra cómo implementar una vista amplia que muestra los grupos de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) los objetos devueltos por la `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="89d40-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="89d40-104">Para obtener más información acerca de los componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="89d40-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="89d40-105">Para cargar este archivo de formato</span><span class="sxs-lookup"><span data-stu-id="89d40-105">To load this formatting file</span></span>

1. <span data-ttu-id="89d40-106">Copie el XML de la sección de ejemplo de este tema en un archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="89d40-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="89d40-107">Guarde el archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="89d40-107">Save the text file.</span></span> <span data-ttu-id="89d40-108">No olvide agregar el `format.ps1xml` extensión al archivo para identificarlo como un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="89d40-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="89d40-109">Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="89d40-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="89d40-110">Este archivo de formato define la presentación de un objeto que ya está definido por un archivos de formato de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89d40-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="89d40-111">Debe usar el `prependPath` parámetro cuando se ejecuta el cmdlet, y no se puede cargar este formato de archivo como un módulo.</span><span class="sxs-lookup"><span data-stu-id="89d40-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="89d40-112">Demostraciones</span><span class="sxs-lookup"><span data-stu-id="89d40-112">Demonstrates</span></span>

<span data-ttu-id="89d40-113">Este archivo de formato muestra los elementos XML siguientes:</span><span class="sxs-lookup"><span data-stu-id="89d40-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="89d40-114">El [nombre](./name-element-for-view-format.md) (elemento) para la vista.</span><span class="sxs-lookup"><span data-stu-id="89d40-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="89d40-115">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define los objetos que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="89d40-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="89d40-116">El [GroupBy](./groupby-element-for-view-format.md) elemento que define cuándo se muestra un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="89d40-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="89d40-117">El [WideItem](./wideitem-element-for-widecontrol-format.md) elemento que define qué propiedad se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="89d40-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="89d40-118">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="89d40-118">Example</span></span>

<span data-ttu-id="89d40-119">El código XML siguiente define una vista amplia que muestra los grupos de objetos.</span><span class="sxs-lookup"><span data-stu-id="89d40-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="89d40-120">Cada nuevo grupo se inicia cuando el valor de la [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) los cambios de propiedad.</span><span class="sxs-lookup"><span data-stu-id="89d40-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

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

<span data-ttu-id="89d40-121">¿El ejemplo siguiente muestra cómo Windows PowerShell muestra el [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de carga este archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="89d40-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="89d40-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="89d40-122">See Also</span></span>

[<span data-ttu-id="89d40-123">Ejemplos de archivos de formato</span><span class="sxs-lookup"><span data-stu-id="89d40-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="89d40-124">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="89d40-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
