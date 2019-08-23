---
title: Tipos de proveedor | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 0a9bfe5dd0978ffce66db1b18ef4d82be6c1a7f2
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986649"
---
# <a name="provider-types"></a>Tipos de proveedor

Los proveedores definen su funcionalidad básica cambiando el modo en que los cmdlets de proveedor, que proporciona PowerShell, realizan sus acciones. Por ejemplo, los proveedores pueden usar la funcionalidad predeterminada del `Get-Item` cmdlet o pueden cambiar el funcionamiento de dicho cmdlet al recuperar elementos del almacén de datos. La funcionalidad del proveedor que se describe en este documento incluye la funcionalidad definida al sobrescribir métodos de interfaces y clases base específicas del proveedor.

> [!NOTE]
> Para ver las características de proveedor predefinidas por PowerShell, consulte [capacidades del proveedor](/previous-versions//ee126189(v=vs.85)).

## <a name="drive-enabled-providers"></a>Proveedores habilitados para unidad

Los proveedores habilitados para unidad especifican las unidades predeterminadas disponibles para el usuario y permiten al usuario agregar o quitar unidades. En la mayoría de los casos, los proveedores de son proveedores habilitados para unidad porque requieren alguna unidad predeterminada para tener acceso al almacén de datos. Sin embargo, al escribir su propio proveedor, es posible que desee permitir que el usuario cree y quite unidades.

Para crear un proveedor habilitado para la unidad, la clase del proveedor debe derivar de la clase [System. Management. Automation. Provider. DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) u otra clase que derive de esa clase. La clase **System. Management. Automation. Provider. DriveCmdletProvider** define los siguientes métodos para implementar las unidades predeterminadas del proveedor y `New-PSDrive` admite `Remove-PSDrive` los cmdlets y. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método al que llama el motor de PowerShell para invocar el `NewDrive` cmdlet, como `New-PSDrive` el método para el cmdlet, y opcionalmente puede sobrescribir un `NewDriveDynamicParameters` segundo método, como , para agregar parámetros dinámicos al cmdlet.

- El método [System. Management. Automation. Provider. DriveCmdletProvider. InitializeDefaultDrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) define las unidades predeterminadas que están disponibles para el usuario cada vez que se usa el proveedor.

- Los métodos [System. Management. Automation. Provider. DriveCmdletProvider. NewDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) y [System. Management. Automation. Provider. DriveCmdletProvider. NewDriveDynamicParameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) definen cómo el proveedor admite el `New-PSDrive`cmdlet Provider. Este cmdlet permite al usuario crear unidades para tener acceso al almacén de datos.

- El método [System. Management. Automation. Provider. DriveCmdletProvider. RemoveDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) define cómo el proveedor admite `Remove-PSDrive` el cmdlet Provider. Este cmdlet permite al usuario quitar unidades del almacén de datos.

## <a name="item-enabled-providers"></a>Proveedores habilitados para elementos

Los proveedores habilitados para elementos permiten al usuario obtener, establecer o borrar los elementos del almacén de datos. Un "elemento" es un elemento del almacén de datos al que el usuario puede tener acceso o administrar de forma independiente. Para crear un proveedor habilitado para elementos, la clase de proveedor debe derivar de la clase [System. Management. Automation. Provider. ItemCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) u otra clase que derive de esa clase.

La clase **System. Management. Automation. Provider. ItemCmdletProvider** define los siguientes métodos para implementar cmdlets específicos de proveedor. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método al que llama el motor de PowerShell para invocar el `ClearItem` cmdlet, como `Clear-Item` el método para el cmdlet, y opcionalmente puede sobrescribir un `ClearItemDynamicParameters` segundo método, como , para agregar parámetros dinámicos al cmdlet.

- Los métodos [System. Management. Automation. Provider. ItemCmdletProvider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) y [System. Management. Automation. Provider. ItemCmdletProvider. ClearItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) definen cómo el proveedor admite el `Clear-Item`cmdlet Provider. Este cmdlet permite al usuario quitar el valor de un elemento en el almacén de datos.

- Los métodos [System. Management. Automation. Provider. ItemCmdletProvider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) y [System. Management. Automation. Provider. ItemCmdletProvider. GetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) definen cómo el proveedor `Get-Item` admite el cmdlet Provider. Este cmdlet permite al usuario recuperar datos del almacén de datos.

- Los métodos [System. Management. Automation. Provider. ItemCmdletProvider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) y [System. Management. Automation. Provider. ItemCmdletProvider. SetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) definen cómo el proveedor `Set-Item` admite el cmdlet Provider. Este cmdlet permite al usuario actualizar los valores de los elementos del almacén de datos.

- Los métodos [System. Management. Automation. Provider. Itemcmdletprovider. InvokeDefaultAction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) y [System. Management. Automation. Provider. Itemcmdletprovider. InvokeDefaultActionDynamicParameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters) definen cómo el proveedor admite el `Invoke-Item` cmdlet Provider. Este cmdlet permite al usuario realizar la acción predeterminada especificada por el elemento.

- Los métodos [System. Management. Automation. Provider. ItemCmdletProvider. ItemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) y [System. Management. Automation. Provider. ItemCmdletProvider. ItemExistsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) definen cómo el proveedor admite el `Test-Path`cmdlet Provider. Este cmdlet permite al usuario determinar si existen todos los elementos de una ruta de acceso.

Además de los métodos que se usan para implementar cmdlets de proveedor, la clase **System. Management. Automation. Provider. ItemCmdletProvider** también define los siguientes métodos:

- El método [System. Management. Automation. Provider. ItemCmdletProvider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) permite al usuario usar caracteres comodín al especificar la ruta de acceso del proveedor.

- [System. Management. Automation. Provider. ItemCmdletProvider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) se usa para determinar si una ruta de acceso es sintácticamente válida y semánticamente válida para el proveedor.

## <a name="container-enabled-providers"></a>Proveedores habilitados para contenedores

Los proveedores habilitados para contenedores permiten al usuario administrar elementos que son contenedores. Un contenedor es un grupo de elementos secundarios con un elemento primario común. Para crear un proveedor habilitado para contenedores, la clase de proveedor debe derivar de la clase [System. Management. Automation. Provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) u otra clase que derive de esa clase.

> [!IMPORTANT]
> Los proveedores habilitados para contenedores no pueden tener acceso a los almacenes de datos que contienen contenedores anidados. Si un elemento secundario de un contenedor es otro contenedor, debe implementar un proveedor habilitado para la navegación.

La clase **System. Management. Automation. Provider. ContainerCmdletProvider** define los siguientes métodos para implementar cmdlets específicos de proveedor. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método al que llama el motor de PowerShell para invocar el `CopyItem` cmdlet, como `Copy-Item` el método para el cmdlet, y opcionalmente puede sobrescribir un `CopyItemDynamicParameters` segundo método, como , para agregar parámetros dinámicos al cmdlet.

- Los métodos [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) y [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) definen cómo el proveedor admite el `Copy-Item` cmdlet Provider. Este cmdlet permite al usuario copiar un elemento de una ubicación a otra.

- Los métodos [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) y [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) definen cómo el proveedor admite el `Get-ChildItem` cmdlet Provider. Este cmdlet permite al usuario recuperar los elementos secundarios del elemento primario.

- Los métodos [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildNames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) y [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildNamesDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) definen cómo el proveedor admite el `Get-ChildItem` cmdlet Provider si `Name` se especifica su parámetro.

- Los métodos [System. Management. Automation. Provider. ContainerCmdletProvider. newitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) y [System. Management. Automation. Provider. ContainerCmdletProvider. NewItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) definen cómo el proveedor admite el `New-Item` cmdlet Provider. Este cmdlet permite al usuario crear nuevos elementos en el almacén de datos.

- Los métodos [System. Management. Automation. Provider. ContainerCmdletProvider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) y [System. Management. Automation. Provider. ContainerCmdletProvider. RemoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) definen el modo en que el proveedor admite el `Remove-Item` cmdlet Provider. Este cmdlet permite al usuario quitar elementos del almacén de datos.

- Los métodos [System. Management. Automation. Provider. ContainerCmdletProvider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) y [System. Management. Automation. Provider. ContainerCmdletProvider. RenameItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) definen cómo el proveedor admite el `Rename-Item` cmdlet Provider. Este cmdlet permite al usuario cambiar el nombre de los elementos en el almacén de datos.

Además de los métodos que se usan para implementar cmdlets de proveedor, la clase **System. Management. Automation. Provider. ContainerCmdletProvider** también define los siguientes métodos:

- La clase de proveedor puede usar el método [System. Management. Automation. Provider. ContainerCmdletProvider. HasChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) para determinar si un elemento tiene elementos secundarios.

- La clase de proveedor puede usar el método [System. Management. Automation. Provider. ContainerCmdletProvider. ConvertPath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) para crear una nueva ruta de acceso específica del proveedor a partir de una ruta de acceso especificada.

## <a name="navigation-enabled-providers"></a>Proveedores habilitados para la navegación

Los proveedores habilitados para la navegación permiten al usuario desplazar elementos en el almacén de datos. Para crear un proveedor habilitado para la navegación, la clase del proveedor debe derivar de la clase [System. Management. Automation. Provider. NavigationCmdletProvider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

La clase **System. Management. Automation. Provider. NavigationCmdletProvider** define los siguientes métodos para implementar cmdlets específicos de proveedor. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método al que llama el motor de PowerShell para invocar el `MoveItem` cmdlet, como `Move-Item` el método para el cmdlet, y opcionalmente puede sobrescribir un `MoveItemDynamicParameters` segundo método, como , para agregar parámetros dinámicos al cmdlet.

- Los métodos [System. Management. Automation. Provider. NavigationCmdletProvider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) y [System. Management. Automation. Provider. NavigationCmdletProvider. MoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) definen el modo en que el proveedor admite el `Move-Item` cmdlet Provider. Este cmdlet permite al usuario trasladar un elemento de una ubicación del almacén a otra ubicación.

- El método [System. Management. Automation. Provider. NavigationCmdletProvider. MakePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) define cómo el proveedor admite `Join-Path` el cmdlet Provider. Este cmdlet permite al usuario combinar un segmento de ruta de acceso principal y secundario para crear una ruta de acceso interna del proveedor.

Además de los métodos que se usan para implementar cmdlets de proveedor, la clase **System. Management. Automation. Provider. NavigationCmdletProvider** también define los siguientes métodos:

- El método [System. Management. Automation. Provider. NavigationCmdletProvider. GetChildName](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) extrae el nombre del nodo secundario de una ruta de acceso.

- El método [System. Management. Automation. Provider. NavigationCmdletProvider. GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) extrae la parte primaria de una ruta de acceso.

- El método [System. Management. Automation. Provider. NavigationCmdletProvider. IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) determina si el elemento es un elemento contenedor. En este contexto, un contenedor es un grupo de elementos secundarios bajo un elemento primario común.

- El método [System. Management. Automation. Provider. NavigationCmdletProvider. NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) devuelve una ruta de acceso a un elemento relativo a una ruta de acceso base especificada.

## <a name="content-enabled-providers"></a>Proveedores habilitados para el contenido

Los proveedores habilitados para el contenido permiten al usuario borrar, obtener o establecer el contenido de los elementos de un almacén de datos.
Por ejemplo, el proveedor FileSystem permite borrar, obtener y establecer el contenido de los archivos en el sistema de archivos. Para crear un proveedor habilitado para el contenido, la clase del proveedor debe implementar los métodos de la interfaz [System. Management. Automation. Provider. IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

La interfaz **System. Management. Automation. Provider. IContentCmdletProvider** define los siguientes métodos para implementar cmdlets específicos de proveedor. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método al que llama el motor de PowerShell para invocar el `ClearContent` cmdlet, como `Clear-Content` el método para el cmdlet, y opcionalmente puede sobrescribir un `ClearContentDynamicParameters` segundo método, como , para agregar parámetros dinámicos al cmdlet.

- Los métodos [System. Management. Automation. Provider. IContentCmdletProvider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) y [System. Management. Automation. Provider. IContentCmdletProvider. ClearContentDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) definen el modo en que el proveedor lo admite. el `Clear-Content` cmdlet Provider. Este cmdlet permite al usuario eliminar el contenido de un elemento sin eliminar el elemento.

- Los métodos [System. Management. Automation. Provider. IContentCmdletProvider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) y [System. Management. Automation. Provider. IContentCmdletProvider. GetContentReaderDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) definen cómo el proveedor admite el `Get-Content` cmdlet Provider. Este cmdlet permite al usuario recuperar el contenido de un elemento. El `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader` método devuelve una interfaz [System. Management. Automation. Provider. IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader) que define los métodos que se usan para leer el contenido.

- Los métodos [System. Management. Automation. Provider. IContentCmdletProvider. GetContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) y [System. Management. Automation. Provider. IContentCmdletProvider. GetContentWriterDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) definen cómo el proveedor admite el `Set-Content` cmdlet Provider. Este cmdlet permite al usuario actualizar el contenido de un elemento. El `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter` método devuelve una interfaz [System. Management. Automation. Provider. IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) que define los métodos que se usan para escribir el contenido.

## <a name="property-enabled-providers"></a>Proveedores habilitados para propiedades

Los proveedores habilitados para propiedades permiten al usuario administrar las propiedades de los elementos del almacén de datos.
Para crear un proveedor habilitado para propiedades, la clase de proveedor debe implementar los métodos de [System. Management. Automation. Provider. IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) y [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)interfaces. En la mayoría de los casos, para admitir un cmdlet de proveedor debe sobrescribir el método al que llama el motor de PowerShell para invocar el `ClearProperty` cmdlet, como el método para el cmdlet Clear-Property y, opcionalmente, puede sobrescribir un segundo método `ClearPropertyDynamicParameters` , como , para agregar parámetros dinámicos al cmdlet.

La interfaz **System. Management. Automation. Provider. IPropertyCmdletProvider** define los siguientes métodos para implementar cmdlets específicos de proveedor:

- Los métodos [System. Management. Automation. Provider. IPropertyCmdletProvider. ClearProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) y [System. Management. Automation. Provider. IPropertyCmdletProvider. ClearPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) definen cómo el proveedor admite el `Clear-ItemProperty` cmdlet Provider. Este cmdlet permite al usuario eliminar el valor de una propiedad.

- Los métodos [System. Management. Automation. Provider. IPropertyCmdletProvider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) y [System. Management. Automation. Provider. IPropertyCmdletProvider. GetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) definen el modo en que el proveedor lo admite. el `Get-ItemProperty` cmdlet Provider. Este cmdlet permite al usuario recuperar la propiedad de un elemento.

- Los métodos [System. Management. Automation. Provider. IPropertyCmdletProvider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) y [System. Management. Automation. Provider. IPropertyCmdletProvider. SetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) definen el modo en que el proveedor lo admite. el `Set-ItemProperty` cmdlet Provider. Este cmdlet permite al usuario actualizar las propiedades de un elemento.

  La interfaz **System. Management. Automation. Provider. IDynamicPropertyCmdletProvider** define los siguientes métodos para implementar cmdlets específicos de proveedor:

- Los métodos [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. CopyProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) y [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. CopyPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) definen cómo el proveedor admite `Copy-ItemProperty` el cmdlet Provider. Este cmdlet permite al usuario copiar una propiedad y su valor de una ubicación a otra.

- Los métodos [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. MoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) y [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. MovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) definen cómo el proveedor admite `Move-ItemProperty` el cmdlet Provider. Este cmdlet permite al usuario desplace una propiedad y su valor de una ubicación a otra.

- Los métodos [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. NewProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) y [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. NewPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) definen cómo el proveedor admite `New-ItemProperty` el cmdlet Provider. Este cmdlet permite al usuario crear una nueva propiedad y establecer su valor.

- Los métodos [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) y [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RemovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) definen cómo el proveedor es compatible `Remove-ItemProperty` con el cmdlet. Este cmdlet permite al usuario eliminar una propiedad y su valor.

- Los métodos [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RenameProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) y [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RenamePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) definen cómo el proveedor es compatible `Rename-ItemProperty` con el cmdlet. Este cmdlet permite al usuario cambiar el nombre de una propiedad.

## <a name="see-also"></a>Vea también

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[Escribir un proveedor de Windows PowerShell](./writing-a-windows-powershell-provider.md)
