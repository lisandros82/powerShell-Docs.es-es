---
title: Vista amplia (básica) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367944"
---
# <a name="wide-view-basic"></a><span data-ttu-id="89628-102">Vista amplia (Basic)</span><span class="sxs-lookup"><span data-stu-id="89628-102">Wide View (Basic)</span></span>

<span data-ttu-id="89628-103">En este ejemplo se muestra cómo implementar una vista ampliada básica que muestra [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos devueltos por el cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="89628-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="89628-104">Para obtener más información sobre los componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="89628-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="89628-105">Para cargar este archivo de formato</span><span class="sxs-lookup"><span data-stu-id="89628-105">To load this formatting file</span></span>

1. <span data-ttu-id="89628-106">Copie el XML de la sección de ejemplo de este tema en un archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="89628-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="89628-107">Guarde el archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="89628-107">Save the text file.</span></span> <span data-ttu-id="89628-108">Asegúrese de agregar la extensión `format.ps1xml` al archivo para identificarlo como un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="89628-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="89628-109">Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="89628-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="89628-110">Este archivo de formato define la presentación de un objeto que ya está definido por un archivo de formato de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89628-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="89628-111">Debe usar el parámetro `prependPath` al ejecutar el cmdlet y no puede cargar este archivo de formato como un módulo.</span><span class="sxs-lookup"><span data-stu-id="89628-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="89628-112">Demuestra</span><span class="sxs-lookup"><span data-stu-id="89628-112">Demonstrates</span></span>

<span data-ttu-id="89628-113">Este archivo de formato muestra los siguientes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="89628-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="89628-114">Elemento [Name](./name-element-for-view-format.md) de la vista.</span><span class="sxs-lookup"><span data-stu-id="89628-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="89628-115">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) que define qué objetos se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="89628-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="89628-116">El elemento [WideItem](./wideitem-element-for-widecontrol-format.md) que define la propiedad que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="89628-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="89628-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="89628-117">Example</span></span>

<span data-ttu-id="89628-118">En el código XML siguiente se define una vista amplia que muestra el valor de la propiedad [System. ServiceProcess. ServiceController. ServiceName](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) .</span><span class="sxs-lookup"><span data-stu-id="89628-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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

<span data-ttu-id="89628-119">En el ejemplo siguiente se muestra cómo Windows PowerShell muestra [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de cargar este archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="89628-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="89628-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="89628-120">See Also</span></span>

[<span data-ttu-id="89628-121">Ejemplos de archivos de formato</span><span class="sxs-lookup"><span data-stu-id="89628-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="89628-122">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="89628-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
