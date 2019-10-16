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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359984"
---
# <a name="provider-cmdlets"></a>Cmdlets de proveedor

Los cmdlets que el usuario puede ejecutar para administrar un almacén de datos se conocen como cmdlets de proveedor. Para admitir estos cmdlets, debe sobrescribir algunos de los métodos definidos por las clases e interfaces de proveedor base.

## <a name="provider-cmdlets"></a>Cmdlets de proveedor

Estos son los cmdlets de proveedor que puede ejecutar el usuario:

### <a name="psdrive-cmdlets"></a>Cmdlets de PSDrive

- `Get-PSDrive`: este cmdlet devuelve las unidades de Windows PowerShell en la sesión actual. No es necesario sobrescribir ningún método para admitir este cmdlet.

- `New-PSDrive`: este cmdlet permite al usuario crear unidades de Windows PowerShell para tener acceso al almacén de datos. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Drivecmdletprovider. newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) y [System. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

- `Remove-PSDrive`: este cmdlet permite al usuario quitar las unidades de Windows PowerShell que tienen acceso al almacén de datos. Para admitir este cmdlet, sobrescriba el método [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .

### <a name="item-cmdlets"></a>Cmdlets de elemento

- `Clear-Item`: este cmdlet permite al usuario quitar el valor de un elemento en el almacén de datos. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Itemcmdletprovider. Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) y [System. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

- `Copy-Item`: este cmdlet permite al usuario copiar un elemento de una ubicación a otra. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Containercmdletprovider. Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) y [System. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

- `Get-Item`: este cmdlet permite al usuario recuperar datos del almacén de datos. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Itemcmdletprovider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) y [System. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

- `Get-ChildItem`: este cmdlet permite al usuario recuperar los elementos secundarios del elemento primario. Para admitir este cmdlet, sobrescriba los métodos siguientes:

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: este cmdlet permite al usuario realizar la acción predeterminada especificada por el elemento. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) y [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

- `Move-Item`: este cmdlet permite al usuario trasladar un elemento de una ubicación a otra. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) y [System. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s.

- `New-ItemProperty`: este cmdlet permite al usuario crear un nuevo elemento en el almacén de datos.

- `Remove-Item`: este cmdlet permite al usuario quitar elementos del almacén de datos. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) y [System. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

- `Rename-Item`: este cmdlet permite al usuario cambiar el nombre de los elementos en el almacén de datos. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Containercmdletprovider. Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) y [System. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .

- `Set-Item`: este cmdlet permite al usuario actualizar los valores de los elementos del almacén de datos. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Itemcmdletprovider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) y [System. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .

### <a name="item-content-cmdlets"></a>Cmdlets de contenido de elemento

- `Add-Content`: este cmdlet permite al usuario agregar contenido a un elemento.

- `Clear-Content`: este cmdlet permite al usuario eliminar contenido de un elemento sin eliminar el elemento. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) y [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) .

- `Get-Content`: este cmdlet permite al usuario recuperar el contenido de un elemento. Para admitir este cmdlet, sobrescriba [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) y [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) modalidades. El método [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) devuelve una interfaz [System. Management. Automation. Provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) que define los métodos que se usan para leer el contenido.

- `Set-Content`: este cmdlet permite al usuario actualizar el contenido de un elemento. Para admitir este cmdlet, sobrescriba [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) y [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) modalidades. El método [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) devuelve una interfaz [System. Management. Automation. Provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) que define los métodos que se usan para escribir el contenido.

### <a name="item-property-cmdlets"></a>Cmdlets de propiedades de elementos

- `Clear-ItemProperty`: este cmdlet permite al usuario eliminar el valor de una propiedad. Para admitir este cmdlet, sobrescriba [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) y [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) modalidades.

- `Copy-ItemProperty`: este cmdlet permite al usuario copiar una propiedad y su valor de una ubicación a otra. Para admitir este cmdlet, sobrescriba [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) y [ Métodos System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) .

- `Get-ItemProperty`: este cmdlet recupera las propiedades de un elemento. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) y [System. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

- `Move-ItemProperty`: este cmdlet permite al usuario desplace una propiedad y su valor de una ubicación a otra. Para admitir este cmdlet, sobrescriba [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) y [ Métodos System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) .

- `New-ItemProperty`: este cmdlet permite al usuario crear una nueva propiedad y establecer su valor. Para admitir este cmdlet, sobrescriba [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) y [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)métodos.

- `Remove-ItemProperty`: este cmdlet permite al usuario eliminar una propiedad y su valor. Para admitir este cmdlet, sobrescriba [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) y [ Métodos System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

- `Rename-ItemProperty`: este cmdlet permite al usuario cambiar el nombre de una propiedad. Para admitir este cmdlet, sobrescriba [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) y [ Métodos System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .

- `Set-ItemProperty`: este cmdlet permite al usuario actualizar las propiedades de un elemento. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) y [System. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

### <a name="location-cmdlets"></a>Cmdlets de ubicación

- `Get-Location`: recupera información sobre la ubicación de trabajo actual. No es necesario sobrescribir ningún método para admitir este cmdlet.

- `Pop-Location`: este cmdlet cambia la ubicación actual a la última ubicación insertada en la pila. No es necesario sobrescribir ningún método para admitir este cmdlet.

- `Push-Location`: este cmdlet agrega la ubicación actual a la parte superior de una lista de ubicaciones (una "pila"). No es necesario sobrescribir ningún método para admitir este cmdlet.

- `Set-Location`: este cmdlet establece la ubicación de trabajo actual en una ubicación especificada. No es necesario sobrescribir ningún método para admitir este cmdlet.

### <a name="path-cmdlets"></a>Cmdlets de ruta de acceso

- `Join-Path`: este cmdlet permite al usuario combinar un segmento de ruta de acceso principal y secundario para crear una ruta de acceso interna del proveedor. Para admitir este cmdlet, sobrescriba el método [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

- `Convert-Path`: este cmdlet convierte una ruta de acceso de una ruta de acceso de Windows PowerShell en una ruta de acceso del proveedor de Windows PowerShell.

- `Split-Path`: devuelve la parte especificada de una ruta de acceso.

- `Resolve-Path`: resuelve los caracteres comodín en una ruta de acceso y muestra el contenido de la ruta de acceso.

- `Test-Path`: este cmdlet determina si existen todos los elementos de una ruta de acceso. Para admitir este cmdlet, sobrescriba los métodos [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) y [System. Management. Automation. Provider. Itemcmdletprovider. Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) .

### <a name="psprovider-cmdlets"></a>Cmdlets de PSProvider

- `Get-PSProvider`: este cmdlet devuelve información acerca de los proveedores disponibles en la sesión. No es necesario sobrescribir ningún método para admitir este cmdlet.