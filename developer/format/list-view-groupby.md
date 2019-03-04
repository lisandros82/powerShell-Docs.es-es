---
title: (GroupBy) de la vista de lista | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: ad7ea457fe0f67bfa41f6bf81f36d4b2e4a76cb3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860151"
---
# <a name="list-view-groupby"></a><span data-ttu-id="94c2b-102">Vista de lista (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="94c2b-102">List View (GroupBy)</span></span>

<span data-ttu-id="94c2b-103">En este ejemplo se muestra cómo implementar una vista de lista que separa las filas de la lista en grupos.</span><span class="sxs-lookup"><span data-stu-id="94c2b-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="94c2b-104">¿Esta vista de lista muestra las propiedades de la [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) los objetos devueltos por la [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94c2b-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="94c2b-105">Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="94c2b-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="94c2b-106">En este ejemplo se muestra cómo implementar una vista de lista que separa las filas de la lista en grupos.</span><span class="sxs-lookup"><span data-stu-id="94c2b-106">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="94c2b-107">¿Esta vista de lista muestra las propiedades de la [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) los objetos devueltos por la [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94c2b-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="94c2b-108">Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="94c2b-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="94c2b-109">Para cargar este archivo de formato</span><span class="sxs-lookup"><span data-stu-id="94c2b-109">To load this formatting file</span></span>

1. <span data-ttu-id="94c2b-110">Copie el XML de la sección de ejemplo de este tema en un archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="94c2b-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="94c2b-111">Guarde el archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="94c2b-111">Save the text file.</span></span> <span data-ttu-id="94c2b-112">No olvide agregar el `format.ps1xml` extensión al archivo para identificarlo como un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="94c2b-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="94c2b-113">Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="94c2b-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="94c2b-114">Este archivo de formato define la presentación de un objeto que ya está definido por un archivo de formato de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94c2b-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="94c2b-115">Debe usar el `prependPath` parámetro cuando se ejecuta el cmdlet, y no se puede cargar este formato de archivo como un módulo.</span><span class="sxs-lookup"><span data-stu-id="94c2b-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="94c2b-116">Demostraciones</span><span class="sxs-lookup"><span data-stu-id="94c2b-116">Demonstrates</span></span>

<span data-ttu-id="94c2b-117">Este archivo de formato muestra los elementos XML siguientes:</span><span class="sxs-lookup"><span data-stu-id="94c2b-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="94c2b-118">El [nombre](./name-element-for-view-format.md) (elemento) para la vista.</span><span class="sxs-lookup"><span data-stu-id="94c2b-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="94c2b-119">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define los objetos que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="94c2b-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="94c2b-120">El [GroupBy](./viewselectedby-element-format.md) elemento que define cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="94c2b-120">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="94c2b-121">El [ListControl](./listcontrol-element-format.md) elemento que define qué propiedad se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="94c2b-121">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="94c2b-122">El [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento que define lo que se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="94c2b-122">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="94c2b-123">El [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento que define la propiedad que se muestra.</span><span class="sxs-lookup"><span data-stu-id="94c2b-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="94c2b-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="94c2b-124">Example</span></span>

<span data-ttu-id="94c2b-125">El código XML siguiente define una vista de lista que se inicia un nuevo grupo cada vez que el valor de la [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) los cambios de propiedad.</span><span class="sxs-lookup"><span data-stu-id="94c2b-125">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="94c2b-126">Cuando se inicia cada grupo, se muestra una etiqueta personalizada que incluye el nuevo valor de la propiedad.</span><span class="sxs-lookup"><span data-stu-id="94c2b-126">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
      <ListControl>
        <ListEntries>
          <ListEntry>
            <ListItems>
              <ListItem>
                <PropertyName>Name</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>DisplayName</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>ServiceType</PropertyName>
              </ListItem>
            </ListItems>
          </ListEntry>
        </ListEntries>
      </ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="94c2b-127">¿El ejemplo siguiente muestra cómo Windows PowerShell muestra el [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de carga este archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="94c2b-127">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="94c2b-128">Las líneas en blanco agregadas antes y después de la etiqueta del grupo se agregan automáticamente mediante Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94c2b-128">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="94c2b-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="94c2b-129">See Also</span></span>

[<span data-ttu-id="94c2b-130">Ejemplos de archivos de formato</span><span class="sxs-lookup"><span data-stu-id="94c2b-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="94c2b-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="94c2b-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
