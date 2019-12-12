---
title: Vista de lista (básica) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362814"
---
# <a name="list-view-basic"></a><span data-ttu-id="91811-102">Vista de lista (Basic)</span><span class="sxs-lookup"><span data-stu-id="91811-102">List View (Basic)</span></span>

<span data-ttu-id="91811-103">En este ejemplo se muestra cómo implementar una vista de lista básica que muestra [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos devueltos por el cmdlet [Get-Service](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="91811-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="91811-104">Para obtener más información sobre los componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="91811-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="91811-105">Para cargar este archivo de formato</span><span class="sxs-lookup"><span data-stu-id="91811-105">To load this formatting file</span></span>

1. <span data-ttu-id="91811-106">Copie el XML de la sección de ejemplo de este tema en un archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="91811-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="91811-107">Guarde el archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="91811-107">Save the text file.</span></span> <span data-ttu-id="91811-108">Asegúrese de agregar la extensión de `format.ps1xml` al archivo para identificarlo como un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="91811-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="91811-109">Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="91811-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="91811-110">Este archivo de formato define la presentación de un objeto que ya está definido por un archivo de formato de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91811-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="91811-111">Debe usar el parámetro `prependPath` al ejecutar el cmdlet y no puede cargar este archivo de formato como un módulo.</span><span class="sxs-lookup"><span data-stu-id="91811-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="91811-112">Demuestra</span><span class="sxs-lookup"><span data-stu-id="91811-112">Demonstrates</span></span>

<span data-ttu-id="91811-113">Este archivo de formato muestra los siguientes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="91811-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="91811-114">Elemento [Name](./name-element-for-view-format.md) de la vista.</span><span class="sxs-lookup"><span data-stu-id="91811-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="91811-115">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) que define qué objetos se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="91811-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="91811-116">Elemento [ListControl](./listcontrol-element-format.md) que define la propiedad que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="91811-116">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="91811-117">Elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) que define lo que se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="91811-117">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="91811-118">El elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) que define la propiedad que se muestra.</span><span class="sxs-lookup"><span data-stu-id="91811-118">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="91811-119">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="91811-119">Example</span></span>

<span data-ttu-id="91811-120">En el código XML siguiente se define una vista de lista que muestra cuatro propiedades de [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) (objeto).</span><span class="sxs-lookup"><span data-stu-id="91811-120">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="91811-121">En cada fila, se muestra el nombre de la propiedad seguido del valor de la propiedad.</span><span class="sxs-lookup"><span data-stu-id="91811-121">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
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
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

<span data-ttu-id="91811-122">En el ejemplo siguiente se muestra cómo Windows PowerShell muestra [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de cargar este archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="91811-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="91811-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="91811-123">See Also</span></span>

[<span data-ttu-id="91811-124">Ejemplos de archivos de formato</span><span class="sxs-lookup"><span data-stu-id="91811-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="91811-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="91811-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
