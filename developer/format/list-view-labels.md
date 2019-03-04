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
# <a name="list-view-labels"></a>Vista de lista (Labels)

En este ejemplo se muestra cómo implementar una vista de lista que muestra una etiqueta personalizada para cada fila de la lista. ¿Esta vista de lista muestra las propiedades de la [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto devuelto por la [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).
En este ejemplo se muestra cómo implementar una vista de lista que muestra una etiqueta personalizada para cada fila de la lista. ¿Esta vista de lista muestra las propiedades de la [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto devuelto por la [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet. Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Para cargar este archivo de formato

1. Copie el XML de la sección de ejemplo de este tema en un archivo de texto.

2. Guarde el archivo de texto. No olvide agregar el `format.ps1xml` extensión al archivo para identificarlo como un archivo de formato.

3. Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Este archivo de formato define la presentación de un objeto que ya está definido por un archivo de formato de Windows PowerShell. Debe usar el `prependPath` parámetro cuando se ejecuta el cmdlet, y no se puede cargar este formato de archivo como un módulo.

## <a name="demonstrates"></a>Demostraciones

Este archivo de formato muestra los elementos XML siguientes:

- El [nombre](./name-element-for-view-format.md) (elemento) para la vista.

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define los objetos que se muestran en la vista.

- El [ListControl](./listcontrol-element-format.md) elemento que define qué propiedad se muestra la vista.

- El [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento que define lo que se muestra en una fila de la vista de lista.

- El [etiqueta](./label-element-for-listitem-for-listcontrol-format.md) elemento que define lo que se muestra en una fila de la vista de lista.

- El [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento que define la propiedad que se muestra.

## <a name="example"></a>Ejemplo

El código XML siguiente define una vista de lista que muestra una etiqueta personalizada en cada fila. En este caso, la etiqueta incluye el nombre de propiedad con cada letra en mayúscula y la palabra "property". En cada fila, se muestra el nombre de la propiedad seguido del valor de la propiedad.

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

¿El ejemplo siguiente muestra cómo Windows PowerShell muestra el [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de carga este archivo de formato.

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

## <a name="see-also"></a>Véase también

[Ejemplos de archivos de formato](./examples-of-formatting-files.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
