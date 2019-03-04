---
title: Cmdlets de proveedor | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854771"
---
# <a name="provider-cmdlets"></a>Cmdlets de proveedor

Los cmdlets que el usuario puede ejecutar para administrar un almacén de datos se conocen como cmdlets de proveedor. Para admitir estos cmdlets, debe sobrescribir algunos de los métodos definidos por las clases de proveedor base e interfaces.

## <a name="provider-cmdlets"></a>Cmdlets de proveedor

Estos son los cmdlets de proveedor que se pueden ejecutar por el usuario:

### <a name="psdrive-cmdlets"></a>Cmdlets de PSDrive

- `Get-PSDrive`: Este cmdlet devuelve que las unidades de Windows PowerShell en la sesión actual. No es necesario sobrescribir los métodos para admitir este cmdlet.

- `New-PSDrive`: Este cmdlet permite al usuario crear unidades de Windows PowerShell para acceder al almacén de datos. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) y [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) métodos.

- `Remove-PSDrive`: Este cmdlet permite al usuario quitar las unidades de Windows PowerShell que obtener acceso al almacén de datos. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método.

### <a name="item-cmdlets"></a>Cmdlets de elemento

- `Clear-Item`: Este cmdlet permite al usuario quitar el valor de un elemento en el almacén de datos. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) y [ System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) métodos.

- `Copy-Item`: Este cmdlet permite al usuario copiar un elemento de una ubicación a otra. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) y [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) métodos.

- `Get-Item`: Este cmdlet permite al usuario recuperar datos del almacén de datos. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) y [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) métodos.

- `Get-ChildItem`: Este cmdlet permite al usuario recuperar los elementos secundarios del elemento primario. Para admitir este cmdlet, sobrescribir los métodos siguientes:

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: Este cmdlet permite al usuario que realice la acción predeterminada especificada por el elemento. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) y [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) métodos.

- `Move-Item`: Este cmdlet permite al usuario mover un elemento de una ubicación a otra ubicación. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) y [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)métodos s.

- `New-ItemProperty`: Este cmdlet permite al usuario crear un nuevo elemento en el almacén de datos.

- `Remove-Item`: Este cmdlet permite al usuario quitar elementos del almacén de datos. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) y [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) métodos.

- `Rename-Item`: Este cmdlet permite al usuario cambiar el nombre de elementos en el almacén de datos. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) y [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) métodos.

- `Set-Item`: Este cmdlet permite al usuario que actualice los valores de elementos en el almacén de datos. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) y [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) métodos.

### <a name="item-content-cmdlets"></a>Cmdlets de contenido del elemento

- `Add-Content`: Este cmdlet permite al usuario agregar contenido a un elemento.

- `Clear-Content`: Este cmdlet permite al usuario eliminar el contenido de un elemento sin eliminar el elemento. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) y [ System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) métodos.

- `Get-Content`: Este cmdlet permite al usuario recuperar el contenido de un elemento. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) y [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) métodos. El [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método devuelve un [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interfaz que define los métodos usados para leer el contenido.

- `Set-Content`: Este cmdlet permite al usuario actualizar el contenido de un elemento. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) y [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) métodos. El [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método devuelve un [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interfaz que define los métodos usados para escribir el contenido.

### <a name="item-property-cmdlets"></a>Cmdlets de la propiedad de elemento

- `Clear-ItemProperty`: Este cmdlet permite al usuario eliminar el valor de una propiedad. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) y [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) métodos.

- `Copy-ItemProperty`: Este cmdlet permite al usuario copiar una propiedad y su valor desde una ubicación a otra. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) y [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) métodos.

- `Get-ItemProperty`: Este cmdlet recupera las propiedades de un elemento. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) y [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) métodos.

- `Move-ItemProperty`: Este cmdlet permite al usuario mover una propiedad y su valor desde una ubicación a otra. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) y [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) métodos.

- `New-ItemProperty`: Este cmdlet permite al usuario crear una nueva propiedad y establecer su valor. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) y [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) métodos.

- `Remove-ItemProperty`: Este cmdlet permite al usuario eliminar una propiedad y su valor. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) y [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) métodos.

- `Rename-ItemProperty`: Este cmdlet permite al usuario cambiar el nombre de una propiedad. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) y [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) métodos.

- `Set-ItemProperty`: Este cmdlet permite al usuario actualizar las propiedades de un elemento. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) y [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) métodos.

### <a name="location-cmdlets"></a>Cmdlets de ubicación

- `Get-Location`: Recupera información sobre la ubicación de trabajo actual. No es necesario sobrescribir los métodos para admitir este cmdlet.

- `Pop-Location`: Este cmdlet cambia la ubicación actual a la última ubicación insertada en la pila. No es necesario sobrescribir los métodos para admitir este cmdlet.

- `Push-Location`: Este cmdlet agrega la ubicación actual a la parte superior de una lista de ubicaciones (una "pila"). No es necesario sobrescribir los métodos para admitir este cmdlet.

- `Set-Location`: Este cmdlet establece la ubicación de trabajo actual en una ubicación especificada. No es necesario sobrescribir los métodos para admitir este cmdlet.

### <a name="path-cmdlets"></a>Cmdlets de ruta de acceso

- `Join-Path`: Este cmdlet permite al usuario combinar un segmento de ruta de acceso primaria y secundaria para crear una ruta de acceso interna del proveedor. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método.

- `Convert-Path`: Este cmdlet convierte una ruta de acceso de una ruta de acceso de Windows PowerShell en una ruta de acceso del proveedor de Windows PowerShell.

- `Split-Path`: Devuelve la parte especificada de una ruta de acceso.

- `Resolve-Path`: Resuelve los caracteres comodín en una ruta de acceso y muestra el contenido de la ruta de acceso.

- `Test-Path`: Este cmdlet se determina si existen todos los elementos de una ruta de acceso. Para admitir este cmdlet, sobrescribir el [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) y [ System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) métodos.

### <a name="psprovider-cmdlets"></a>Cmdlets de PSProvider

- `Get-PSProvider`: Este cmdlet devuelve información sobre los proveedores disponibles en la sesión. No es necesario sobrescribir los métodos para admitir este cmdlet.