---
title: Tipos de proveedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 37689571eb1650e5991af2e7002cd037ae99dd68
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057967"
---
# <a name="provider-types"></a>Tipos de proveedor

Proveedores de definen su funcionalidad básica cambiando cómo los cmdlets de proveedor (proporcionados por Windows PowerShell) realizan sus acciones. Por ejemplo, los proveedores pueden usar la funcionalidad predeterminada de la `Get-Item` cmdlet, o bien pueden cambiar el funcionamiento de ese cmdlet cuando se recuperan los elementos del almacén de datos. La funcionalidad de proveedor descrita en este tema incluye funcionalidad definida por sobrescribir los métodos de interfaces y clases base del proveedor específico.

> [!NOTE]
> Para las características del proveedor que previamente se definen mediante Windows PowerShell, consulte [las capacidades del proveedor](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6).

## <a name="drive-enabled-providers"></a>Proveedores de unidad

Proveedores de unidad especifican las unidades de predeterminado disponible para el usuario y permitir que el usuario agregar o quitar unidades. En la mayoría de los casos, los proveedores son proveedores de unidad habilitada porque requieren algunos unidad predeterminada para acceder al almacén de datos. Sin embargo, al escribir su propio proveedor podría o no quiera permitir al usuario crear y quitar unidades.

Para crear un proveedor de la unidad habilitada, debe derivar la clase de proveedor de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase u otra clase que derive de esa clase. El [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase define los siguientes métodos para implementar las unidades de valor predeterminado del proveedor y que admiten la `New-PSDrive` y `Remove-PSDrive` cmdlets. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método que llama el motor de Windows PowerShell para invocar el cmdlet, como el `NewDrive` método para el `New-PSDrive` cmdlet y, opcionalmente, puede sobrescribir un segundo método, por ejemplo, `NewDriveDynamicParameters`, para agregar los parámetros dinámicos al cmdlet.

- El [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método define las unidades de predeterminados que están disponibles para el usuario cada vez que se utiliza el proveedor.

- El [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) y [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) métodos define cómo el proveedor admita las `New-PSDrive` cmdlet de proveedor. Este cmdlet permite al usuario crear unidades de disco al tener acceso al almacén de datos.

- El [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método define cómo el proveedor admita las `Remove-PSDrive` cmdlet de proveedor. Este cmdlet permite al usuario quitar las unidades del almacén de datos.

## <a name="item-enabled-providers"></a>Proveedores de elemento

Proveedores de elemento permiten al usuario obtener, establecer o borrar los elementos en el almacén de datos. Un "elemento" es un elemento del almacén de datos que el usuario puede acceder o administrar de forma independiente. Para crear un proveedor de elemento habilitado, debe derivar la clase de proveedor de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase u otra clase que derive de esa clase.

El [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase define los métodos siguientes para la implementación de cmdlets de proveedor específico. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método que llama el motor de Windows PowerShell para invocar el cmdlet, como el `ClearItem` método para el `Clear-Item` cmdlet y, opcionalmente, puede sobrescribir un segundo método, por ejemplo, `ClearItemDynamicParameters`, para agregar los parámetros dinámicos al cmdlet.

- El [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) y [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) métodos definir cómo su proveedor admite el `Clear-Item` cmdlet de proveedor. Este cmdlet permite al usuario quitar del valor de un elemento en el almacén de datos.

- El [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) y [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) los métodos definen cómo admite el proveedor la `Get-Item` cmdlet de proveedor. Este cmdlet permite al usuario recuperar datos del almacén de datos.

- El [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) y [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) los métodos definen cómo admite el proveedor la `Set-Item` cmdlet de proveedor. Este cmdlet permite al usuario que actualice los valores de elementos en el almacén de datos.

- El [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) y [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) métodos definir cómo su proveedor admite el `Invoke-Item` cmdlet de proveedor. Este cmdlet permite al usuario que realice la acción predeterminada especificada por el elemento.

- El [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) y [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) métodos definir cómo su proveedor admite el `Test-Path` cmdlet de proveedor. Este cmdlet permite al usuario determinar si existen todos los elementos de una ruta de acceso.

  Además de los métodos utilizados para implementar los cmdlets de proveedor, el [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase también define los métodos siguientes:

- El [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) método permite al usuario usar caracteres comodín al especificar la ruta de acceso del proveedor.

- El [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) se usa para determinar si una ruta de acceso es sintáctica y semánticamente válido para el proveedor.

## <a name="container-enabled-providers"></a>Proveedores de contenedor

Proveedores de contenedor permiten al usuario administrar los elementos que son contenedores. Un contenedor es un grupo de elementos secundarios con un elemento primario común. Para crear un proveedor con contenedores habilitados, debe derivar la clase de proveedor de la [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase u otra clase que derive de esa clase.

> [!IMPORTANT]
> Proveedores de contenedor no pueden tener acceso a almacenes de datos que contienen los contenedores anidados. Si un elemento secundario de un contenedor es otro contenedor, debe implementar un proveedor de navegación habilitado.

El [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase define los métodos siguientes para la implementación de cmdlets de proveedor específico. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método que llama el motor de Windows PowerShell para invocar el cmdlet, como el `CopyItem` método para el `Copy-Item` cmdlet y, opcionalmente, puede sobrescribir un segundo método, por ejemplo, `CopyItemDynamicParameters`, para agregar los parámetros dinámicos al cmdlet.

- El [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) y [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) los métodos definen cómo el proveedor admita las `Copy-Item` cmdlet de proveedor. Este cmdlet permite al usuario copiar un elemento de una ubicación a otra.

- El [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) y [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) los métodos definen cómo el proveedor admita las `Get-ChildItem` cmdlet de proveedor. Este cmdlet permite al usuario recuperar los elementos secundarios del elemento primario.

- El [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) y [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) los métodos definen cómo el proveedor admite la `Get-ChildItem` proveedor cmdlet si su `Name` se especifica el parámetro.

- El [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) y [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) los métodos definen cómo el proveedor admita las `New-Item` cmdlet de proveedor. Este cmdlet permite al usuario crear nuevos elementos en el almacén de datos.

- El [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) y [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) los métodos definen cómo el proveedor admita las `Remove-Item` cmdlet de proveedor. Este cmdlet permite al usuario quitar elementos del almacén de datos.

- El [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) y [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) los métodos definen cómo el proveedor admita las `Rename-Item` cmdlet de proveedor. Este cmdlet permite al usuario cambiar el nombre de elementos en el almacén de datos.

  Además de los métodos utilizados para implementar los cmdlets de proveedor, el [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase también define los métodos siguientes:

- El [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método puede utilizarse por la clase de proveedor para determinar si un elemento tiene elementos secundarios.

- El [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) método puede utilizarse por la clase de proveedor para crear una nueva ruta de acceso específica del proveedor desde una ruta de acceso especificada.

## <a name="navigation-enabled-providers"></a>Proveedores de navegación

Proveedores de exploración permiten al usuario mover elementos en el almacén de datos. Para crear un proveedor de navegación habilitado, debe derivar la clase de proveedor de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase.

El [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase define los métodos siguientes para la implementación de cmdlets de proveedor específico. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método que llama el motor de Windows PowerShell para invocar el cmdlet, como el `MoveItem` método para el `Move-Item` cmdlet y, opcionalmente, puede sobrescribir un segundo método, por ejemplo, `MoveItemDynamicParameters`, para agregar los parámetros dinámicos al cmdlet.

- El [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) y [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) los métodos definen cómo el proveedor admita las `Move-Item` cmdlet de proveedor. Este cmdlet permite al usuario mover un elemento de una ubicación en el almacén a otra ubicación.

- El [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método define cómo el proveedor admita las `Join-Path` cmdlet de proveedor. Este cmdlet permite al usuario combinar un segmento de ruta de acceso primaria y secundaria para crear una ruta de acceso interna del proveedor.

  Además de los métodos utilizados para implementar los cmdlets de proveedor, el [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase también define los métodos siguientes:

- El [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) método extrae el nombre del nodo secundario de una ruta de acceso.

- El [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) método extrae la parte principal de una ruta de acceso.

- El [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) método determina si el elemento es un elemento contenedor. En este contexto, un contenedor es un grupo de elementos secundarios con un elemento primario común.

- El [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) método devuelve una ruta de acceso a un elemento que es relativa a una ruta de acceso base especificada.

## <a name="content-enabled-providers"></a>Proveedores de contenido

Proveedores de contenido permiten al usuario borrar, obtener o establecer el contenido de elementos en un almacén de datos. Por ejemplo, el proveedor FileSystem permite borrar, obtener y establecer el contenido de los archivos del sistema de archivos. Para crear un proveedor de contenido habilitado, la clase de proveedor debe implementar los métodos de la [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaz.

El [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaz define los métodos siguientes para la implementación de cmdlets de proveedor específico. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método que llama el motor de Windows PowerShell para invocar el cmdlet, como el `ClearContent` método para el `Clear-Content` cmdlet y, opcionalmente, puede sobrescribir un segundo método, por ejemplo, `ClearContentDynamicParameters`, para agregar los parámetros dinámicos al cmdlet.

- El [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) y [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)los métodos definen cómo el proveedor admita las `Clear-Content` cmdlet de proveedor. Este cmdlet permite al usuario eliminar el contenido de un elemento sin eliminar el elemento.

- El [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) y [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) los métodos definen cómo el proveedor admita las `Get-Content` cmdlet de proveedor. Este cmdlet permite al usuario recuperar el contenido de un elemento. El [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método devuelve un [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interfaz que define los métodos usados para leer el contenido.

- El [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) y [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) los métodos definen cómo el proveedor admita las `Set-Content` cmdlet de proveedor. Este cmdlet permite al usuario actualizar el contenido de un elemento. El [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método devuelve un [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interfaz que define los métodos usados para escribir el contenido.

## <a name="property-enabled-providers"></a>Proveedores de propiedad

Proveedores de la propiedad habilitada permiten al usuario administrar las propiedades de los elementos en el almacén de datos. Para crear un proveedor de la propiedad habilitada, la clase de proveedor debe implementar los métodos de la [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) y [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfaces. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método que llama el motor de Windows PowerShell para invocar el cmdlet, como el `ClearProperty` método para el cmdlet Clear-propiedad y, opcionalmente, puede sobrescribir un segundo método, por ejemplo, `ClearPropertyDynamicParameters`, para agregar los parámetros dinámicos al cmdlet.

El [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfaz define los métodos siguientes para la implementación de cmdlets de proveedor específico:

- El [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) y [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) los métodos definen cómo el proveedor admita las `Clear-ItemProperty` cmdlet de proveedor. Este cmdlet permite al usuario eliminar el valor de una propiedad.

- El [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) y [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)los métodos definen cómo el proveedor admita las `Get-ItemProperty` cmdlet de proveedor. Este cmdlet permite al usuario recuperar la propiedad de un elemento.

- El [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) y [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)los métodos definen cómo el proveedor admita las `Set-ItemProperty` cmdlet de proveedor. Este cmdlet permite al usuario actualizar las propiedades de un elemento.

  El [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfaz define los métodos siguientes para la implementación de cmdlets de proveedor específico:

- El [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) y [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) los métodos definen cómo el proveedor admita las `Copy-ItemProperty` cmdlet de proveedor. Este cmdlet permite al usuario copiar una propiedad y su valor desde una ubicación a otra.

- El [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) y [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) los métodos definen cómo el proveedor admita las `Move-ItemProperty` cmdlet de proveedor. Este cmdlet permite al usuario mover una propiedad y su valor desde una ubicación a otra.

- El [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) y [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) los métodos definen cómo el proveedor admita las `New-ItemProperty` cmdlet de proveedor. Este cmdlet permite al usuario crear una nueva propiedad y establecer su valor.

- El [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) y [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) los métodos definen cómo el proveedor admita las `Remove-ItemProperty` cmdlet. Este cmdlet permite al usuario eliminar una propiedad y su valor.

- El [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) y [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) los métodos definen cómo el proveedor admita las `Rename-ItemProperty` cmdlet. Este cmdlet permite al usuario cambiar el nombre de una propiedad.

## <a name="see-also"></a>Véase también

[Escribir un proveedor de Windows PowerShell](./writing-a-windows-powershell-provider.md)