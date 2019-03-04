---
title: Vista amplia (Basic) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860111"
---
# <a name="wide-view-basic"></a><span data-ttu-id="76f01-102">Vista amplia (Basic)</span><span class="sxs-lookup"><span data-stu-id="76f01-102">Wide View (Basic)</span></span>

<span data-ttu-id="76f01-103">¿En este ejemplo se muestra cómo implementar una vista amplia básica que muestra la [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) los objetos devueltos por la `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="76f01-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="76f01-104">Para obtener más información acerca de los componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="76f01-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="76f01-105">Para cargar este archivo de formato</span><span class="sxs-lookup"><span data-stu-id="76f01-105">To load this formatting file</span></span>

1. <span data-ttu-id="76f01-106">Copie el XML de la sección de ejemplo de este tema en un archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="76f01-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="76f01-107">Guarde el archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="76f01-107">Save the text file.</span></span> <span data-ttu-id="76f01-108">No olvide agregar el `format.ps1xml` extensión al archivo para identificarlo como un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="76f01-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="76f01-109">Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="76f01-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="76f01-110">Este archivo de formato define la presentación de un objeto que ya está definido por un archivo de formato de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76f01-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="76f01-111">Debe usar el `prependPath` parámetro cuando se ejecuta el cmdlet, y no se puede cargar este formato de archivo como un módulo.</span><span class="sxs-lookup"><span data-stu-id="76f01-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="76f01-112">Demostraciones</span><span class="sxs-lookup"><span data-stu-id="76f01-112">Demonstrates</span></span>

<span data-ttu-id="76f01-113">Este archivo de formato muestra los elementos XML siguientes:</span><span class="sxs-lookup"><span data-stu-id="76f01-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="76f01-114">El [nombre](./name-element-for-view-format.md) (elemento) para la vista.</span><span class="sxs-lookup"><span data-stu-id="76f01-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="76f01-115">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define los objetos que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="76f01-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="76f01-116">El [WideItem](./wideitem-element-for-widecontrol-format.md) elemento que define qué propiedad se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="76f01-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="76f01-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="76f01-117">Example</span></span>

<span data-ttu-id="76f01-118">El código XML siguiente define una vista amplia que muestra el valor de la [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) propiedad.</span><span class="sxs-lookup"><span data-stu-id="76f01-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

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

<span data-ttu-id="76f01-119">¿El ejemplo siguiente muestra cómo Windows PowerShell muestra el [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de carga este archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="76f01-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="76f01-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="76f01-120">See Also</span></span>

[<span data-ttu-id="76f01-121">Ejemplos de archivos de formato</span><span class="sxs-lookup"><span data-stu-id="76f01-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="76f01-122">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="76f01-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
