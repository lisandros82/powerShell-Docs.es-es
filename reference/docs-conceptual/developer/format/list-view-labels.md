---
title: Vista de lista (etiquetas) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362794"
---
# <a name="list-view-labels"></a>Vista de lista (Labels)

Este ejemplo muestra cómo implementar una vista de lista que muestra una etiqueta personalizada para cada fila de la lista. Esta vista de lista muestra las propiedades de [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objeto devuelto por el cmdlet [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) . Para obtener más información sobre los componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Para cargar este archivo de formato

1. Copie el XML de la sección de ejemplo de este tema en un archivo de texto.

2. Guarde el archivo de texto. Asegúrese de agregar la extensión `format.ps1xml` al archivo para identificarlo como un archivo de formato.

3. Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Este archivo de formato define la presentación de un objeto que ya está definido por un archivo de formato de Windows PowerShell. Debe usar el parámetro `prependPath` al ejecutar el cmdlet y no puede cargar este archivo de formato como un módulo.

## <a name="demonstrates"></a>Demuestra

Este archivo de formato muestra los siguientes elementos XML:

- Elemento [Name](./name-element-for-view-format.md) de la vista.

- El elemento [ViewSelectedBy](./viewselectedby-element-format.md) que define qué objetos se muestran en la vista.

- Elemento [ListControl](./listcontrol-element-format.md) que define la propiedad que se muestra en la vista.

- Elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) que define lo que se muestra en una fila de la vista de lista.

- Elemento de [etiqueta](./label-element-for-listitem-for-listcontrol-format.md) que define lo que se muestra en una fila de la vista de lista.

- El elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) que define la propiedad que se muestra.

## <a name="example"></a>Ejemplo

En el código XML siguiente se define una vista de lista que muestra una etiqueta personalizada en cada fila. En este caso, la etiqueta incluye el nombre de la propiedad con cada letra en mayúsculas y la palabra "Property". En cada fila, se muestra el nombre de la propiedad seguido del valor de la propiedad.

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

En el ejemplo siguiente se muestra cómo Windows PowerShell muestra [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de cargar este archivo de formato.

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
