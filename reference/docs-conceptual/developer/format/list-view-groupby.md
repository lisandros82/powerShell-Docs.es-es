---
title: Vista de lista (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365144"
---
# <a name="list-view-groupby"></a><span data-ttu-id="9e8b0-102">Vista de lista (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="9e8b0-102">List View (GroupBy)</span></span>

<span data-ttu-id="9e8b0-103">Este ejemplo muestra cómo implementar una vista de lista que separa las filas de la lista en grupos.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="9e8b0-104">Esta vista de lista muestra las propiedades de [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos devueltos por el cmdlet [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) .</span><span class="sxs-lookup"><span data-stu-id="9e8b0-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="9e8b0-105">Para obtener más información sobre los componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="9e8b0-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="9e8b0-106">Para cargar este archivo de formato</span><span class="sxs-lookup"><span data-stu-id="9e8b0-106">To load this formatting file</span></span>

1. <span data-ttu-id="9e8b0-107">Copie el XML de la sección de ejemplo de este tema en un archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="9e8b0-108">Guarde el archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-108">Save the text file.</span></span> <span data-ttu-id="9e8b0-109">Asegúrese de agregar la extensión de `format.ps1xml` al archivo para identificarlo como un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="9e8b0-110">Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="9e8b0-111">Este archivo de formato define la presentación de un objeto que ya está definido por un archivo de formato de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="9e8b0-112">Debe usar el parámetro `prependPath` al ejecutar el cmdlet y no puede cargar este archivo de formato como un módulo.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9e8b0-113">Demuestra</span><span class="sxs-lookup"><span data-stu-id="9e8b0-113">Demonstrates</span></span>

<span data-ttu-id="9e8b0-114">Este archivo de formato muestra los siguientes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="9e8b0-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="9e8b0-115">Elemento [Name](./name-element-for-view-format.md) de la vista.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="9e8b0-116">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) que define qué objetos se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="9e8b0-117">El elemento [GroupBy](./viewselectedby-element-format.md) que define cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="9e8b0-118">Elemento [ListControl](./listcontrol-element-format.md) que define la propiedad que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="9e8b0-119">Elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) que define lo que se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="9e8b0-120">El elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) que define la propiedad que se muestra.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="9e8b0-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9e8b0-121">Example</span></span>

<span data-ttu-id="9e8b0-122">En el código XML siguiente se define una vista de lista que inicia un nuevo grupo siempre que cambia el valor de la propiedad [System. ServiceProcess. ServiceController. status](/dotnet/api/System.ServiceProcess.ServiceController.Status) .</span><span class="sxs-lookup"><span data-stu-id="9e8b0-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="9e8b0-123">Cuando se inicia cada grupo, se muestra una etiqueta personalizada que incluye el nuevo valor de la propiedad.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

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

<span data-ttu-id="9e8b0-124">En el ejemplo siguiente se muestra cómo Windows PowerShell muestra [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de cargar este archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="9e8b0-125">Windows PowerShell agrega automáticamente las líneas en blanco agregadas antes y después de la etiqueta de grupo.</span><span class="sxs-lookup"><span data-stu-id="9e8b0-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9e8b0-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="9e8b0-126">See Also</span></span>

[<span data-ttu-id="9e8b0-127">Ejemplos de archivos de formato</span><span class="sxs-lookup"><span data-stu-id="9e8b0-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="9e8b0-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9e8b0-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
