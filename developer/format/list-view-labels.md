---
title: (Etiquetas) de la vista de lista | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 2bb62ab3e4fa1db9b3af8c82eb9035aa4f3e31c0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860131"
---
# <a name="list-view-labels"></a><span data-ttu-id="0e67e-102">Vista de lista (Labels)</span><span class="sxs-lookup"><span data-stu-id="0e67e-102">List View (Labels)</span></span>

<span data-ttu-id="0e67e-103">En este ejemplo se muestra cómo implementar una vista de lista que muestra una etiqueta personalizada para cada fila de la lista.</span><span class="sxs-lookup"><span data-stu-id="0e67e-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="0e67e-104">¿Esta vista de lista muestra las propiedades de la [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto devuelto por la [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0e67e-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="0e67e-105">Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="0e67e-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="0e67e-106">En este ejemplo se muestra cómo implementar una vista de lista que muestra una etiqueta personalizada para cada fila de la lista.</span><span class="sxs-lookup"><span data-stu-id="0e67e-106">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="0e67e-107">¿Esta vista de lista muestra las propiedades de la [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto devuelto por la [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0e67e-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="0e67e-108">Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="0e67e-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="0e67e-109">Para cargar este archivo de formato</span><span class="sxs-lookup"><span data-stu-id="0e67e-109">To load this formatting file</span></span>

1. <span data-ttu-id="0e67e-110">Copie el XML de la sección de ejemplo de este tema en un archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="0e67e-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="0e67e-111">Guarde el archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="0e67e-111">Save the text file.</span></span> <span data-ttu-id="0e67e-112">No olvide agregar el `format.ps1xml` extensión al archivo para identificarlo como un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="0e67e-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="0e67e-113">Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="0e67e-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="0e67e-114">Este archivo de formato define la presentación de un objeto que ya está definido por un archivo de formato de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e67e-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="0e67e-115">Debe usar el `prependPath` parámetro cuando se ejecuta el cmdlet, y no se puede cargar este formato de archivo como un módulo.</span><span class="sxs-lookup"><span data-stu-id="0e67e-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0e67e-116">Demostraciones</span><span class="sxs-lookup"><span data-stu-id="0e67e-116">Demonstrates</span></span>

<span data-ttu-id="0e67e-117">Este archivo de formato muestra los elementos XML siguientes:</span><span class="sxs-lookup"><span data-stu-id="0e67e-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="0e67e-118">El [nombre](./name-element-for-view-format.md) (elemento) para la vista.</span><span class="sxs-lookup"><span data-stu-id="0e67e-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="0e67e-119">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define los objetos que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="0e67e-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="0e67e-120">El [ListControl](./listcontrol-element-format.md) elemento que define qué propiedad se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="0e67e-120">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="0e67e-121">El [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento que define lo que se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="0e67e-121">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="0e67e-122">El [etiqueta](./label-element-for-listitem-for-listcontrol-format.md) elemento que define lo que se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="0e67e-122">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="0e67e-123">El [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento que define la propiedad que se muestra.</span><span class="sxs-lookup"><span data-stu-id="0e67e-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="0e67e-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0e67e-124">Example</span></span>

<span data-ttu-id="0e67e-125">El código XML siguiente define una vista de lista que muestra una etiqueta personalizada en cada fila.</span><span class="sxs-lookup"><span data-stu-id="0e67e-125">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="0e67e-126">En este caso, la etiqueta incluye el nombre de propiedad con cada letra en mayúscula y la palabra "property".</span><span class="sxs-lookup"><span data-stu-id="0e67e-126">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="0e67e-127">En cada fila, se muestra el nombre de la propiedad seguido del valor de la propiedad.</span><span class="sxs-lookup"><span data-stu-id="0e67e-127">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
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

<span data-ttu-id="0e67e-128">¿El ejemplo siguiente muestra cómo Windows PowerShell muestra el [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de carga este archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="0e67e-128">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="0e67e-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="0e67e-129">See Also</span></span>

[<span data-ttu-id="0e67e-130">Ejemplos de archivos de formato</span><span class="sxs-lookup"><span data-stu-id="0e67e-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="0e67e-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e67e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
