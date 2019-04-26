---
title: Diseñar el proveedor de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 711a85e9b2eade7b9095d7560f53610e709e380a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081825"
---
# <a name="designing-your-windows-powershell-provider"></a>Diseño del proveedor de Windows PowerShell

Debe implementar un proveedor de Windows PowerShell si su producto o la configuración se expone un conjunto de datos almacenados, como una base de datos que el usuario desea navegan o examinan. Además, si su producto proporciona un contenedor, incluso si no es un contenedor de varios niveles, tiene sentido implementar un proveedor de Windows PowerShell. Por ejemplo, puede implementar un proveedor de contenedores de Windows PowerShell si el verbo del cmdlet copia, mover, cambiar el nombre nuevo o quitar como una operación en los datos de configuración o el producto tiene sentido.

## <a name="windows-powershell-paths-identify-your-provider"></a>El proveedor de identidades de las rutas de acceso de Windows PowerShell

El tiempo de ejecución de Windows PowerShell usa las rutas de acceso de Windows PowerShell para tener acceso al proveedor de Windows PowerShell adecuado. Cuando un cmdlet especifica una de estas rutas de acceso, el runtime sabe qué proveedor se utiliza para tener acceso al almacén de datos asociados. Estas rutas de acceso incluyen rutas de acceso completa a la unidad, rutas de acceso completo del proveedor, las rutas de acceso directo del proveedor y las rutas de acceso interna del proveedor. Cada proveedor de Windows PowerShell debe admitir una o varias de estas rutas de acceso.

Para obtener más información acerca de las rutas de acceso de Windows PowerShell, vea cómo Windows PowerShell funciona.

### <a name="defining-a-drive-qualified-path"></a>Definir una ruta de acceso completa a la unidad

Para permitir al usuario tener acceso a datos ubicados en una unidad física, el proveedor de Windows PowerShell debe admitir una ruta de acceso completa a la unidad. Esta ruta de acceso comienza con el nombre de la unidad seguido de dos puntos (:), por ejemplo, mydrive:\abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Definir una ruta de acceso de proveedor

Para permitir que el tiempo de ejecución de Windows PowerShell inicializar y anular la inicialización del proveedor, el proveedor de Windows PowerShell debe admitir una ruta de acceso de proveedor. Por ejemplo, FileSystem::\\\uncshare\abc\bar es la ruta de acceso completo del proveedor para el proveedor de sistema de archivos proporcionado por Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Definir una ruta de acceso directo del proveedor

Para permitir el acceso remoto a su proveedor de Windows PowerShell, debe admitir una ruta de acceso directo del proveedor para pasar directamente al proveedor de Windows PowerShell para la ubicación actual. Por ejemplo, puede usar el proveedor de Windows PowerShell del registro \\\server\regkeypath como una ruta de acceso directo del proveedor.

### <a name="defining-a-provider-internal-path"></a>Definir una ruta de acceso interna del proveedor

Para permitir que el cmdlet de proveedor obtener acceso a datos mediante interfaces de programación de aplicaciones (API) de que no sean de Windows PowerShell, el proveedor de Windows PowerShell debe admitir una ruta de acceso interna del proveedor. Esta ruta de acceso se indica después de la "::" en la ruta de acceso de proveedor. Por ejemplo, la ruta de acceso interna del proveedor para el proveedor de filesystem de Windows PowerShell es \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>Cambiar los datos almacenados

Al invalidar los métodos que modifican el almacén de datos subyacente, llame siempre a la [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) que cambia método con la versión más actualizada del elemento método. La infraestructura del proveedor determina si el objeto de elemento debe pasarse a la canalización, por ejemplo, cuando el usuario especifica el parámetro - PassThru. Si al recuperar el elemento más reciente es una operación costosa (en cuanto al rendimiento), puede probar la propiedad Context.PassThru para determinar si realmente necesita escribir el elemento resultante.

## <a name="choose-a-base-class-for-your-provider"></a>Elija una clase Base para el proveedor

Windows PowerShell proporciona una serie de clases base que puede usar para implementar su propio proveedor de Windows PowerShell. Al diseñar un proveedor, elija la clase base, que se describe en esta sección, que es más adecuada para sus requisitos.

Cada clase base del proveedor de Windows PowerShell hace que un conjunto de cmdlets disponibles. En esta sección se describe los cmdlets, pero no describe sus parámetros.

Con el estado de sesión, el tiempo de ejecución de Windows PowerShell realiza varios cmdlets de ubicación disponibles en ciertos proveedores de Windows PowerShell, como el `Get-Location`, `Set-Location`, `Pop-Location`, y `Push-Location` cmdlets. Puede usar el `Get-Help` para obtener información sobre estos cmdlets de ubicación.

### <a name="cmdletprovider-base-class"></a>Clase Base CmdletProvider

El [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) clase define un proveedor básico de Windows PowerShell. Esta clase es compatible con la declaración del proveedor y proporciona una serie de propiedades y métodos que están disponibles para todos los proveedores de Windows PowerShell. La clase se invoca mediante el `Get-PSProvider` cmdlet para enumerar todos los proveedores disponibles para una sesión. La implementación de este cmdlet es proporcionada por el estado de sesión.

> [!NOTE]
> Proveedores de Windows PowerShell están disponibles para todos los ámbitos de idioma de Windows PowerShell.

### <a name="drivecmdletprovider-base-class"></a>Clase Base DriveCmdletProvider

El [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase define un proveedor de la unidad de Windows PowerShell que admite operaciones de adición de nuevas unidades, quitar las unidades existentes e inicializar las unidades de forma predeterminada. Por ejemplo, el proveedor FileSystem de Windows PowerShell proporcionado inicializa las unidades para todos los volúmenes se montan como discos duros y unidades de dispositivo de CD/DVD.

Esta clase se deriva de la [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) clase base. En la tabla siguiente se enumera los cmdlets que expone esta clase. Además de los enumerados, el `Get-PSDrive` cmdlet (expuesto por el estado de sesión) es un cmdlet relacionado que se usa para recuperar las unidades disponibles.

|Cmdlet|Definición|
|------------|----------------|
|`New-PSDrive`|Crea una nueva unidad para la sesión y transmite la información de la unidad.|
|`Remove-PSDrive`|Quita una unidad de la sesión.|

### <a name="itemcmdletprovider-base-class"></a>Clase Base ItemCmdletProvider

El [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase define un proveedor de elementos de Windows PowerShell que realiza operaciones en los elementos individuales del almacén de datos y no supone ningún contenedor o funciones de navegación. Esta clase se deriva de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase base. En la tabla siguiente se enumera los cmdlets que expone esta clase.

|Cmdlet|Definición|
|------------|----------------|
|`Clear-Item`|Borra el contenido actual de elementos en la ubicación especificada y lo reemplaza con el valor "Borrar" especificado por el proveedor. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|
|`Get-Item`|Recupera elementos de la ubicación especificada y transmite los objetos resultantes.|
|`Invoke-Item`|Invoca la acción predeterminada para el elemento situado en la ruta de acceso especificada.|
|`Set-Item`|Establece un elemento en la ubicación especificada con el valor indicado. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|
|`Resolve-Path`|Resuelve los caracteres comodín para una ruta de acceso de Windows PowerShell y la información de ruta de acceso de secuencias.|
|`Test-Path`|Comprueba la ruta de acceso especificada y devuelve `true` si existe y `false` en caso contrario. Este cmdlet se implementa para admitir la `IsContainer` parámetro para el [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.|

### <a name="containercmdletprovider-base-class"></a>Clase Base ContainerCmdletProvider

El [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase define un proveedor de contenedor de Windows PowerShell que expone un contenedor para elementos de almacén de datos, al usuario. Tenga en cuenta que un proveedor de contenedores de Windows PowerShell puede usarse solo cuando hay un contenedor (no hay contenedores anidados) con los elementos en ella. Si no hay contenedores anidados, a continuación, debe implementar un proveedor de navegación de Windows PowerShell.

Esta clase se deriva de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase base. La siguiente tabla define los cmdlets implementados por esta clase.

|Cmdlet|Definición|
|------------|----------------|
|`Copy-Item`|Copia los elementos de una ubicación a otra. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|
|`Get-Childitem`|Recupera los elementos secundarios en la ubicación especificada y transmite como objetos.|
|`New-Item`|Crea nuevos elementos en la ubicación especificada y transmite el objeto resultante.|
|`Remove-Item`|Quita elementos de la ubicación especificada.|
|`Rename-Item`|Cambia el nombre de un elemento en la ubicación especificada. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|

### <a name="navigationcmdletprovider-base-class"></a>Clase Base NavigationCmdletProvider

El [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase define un proveedor de navegación de Windows PowerShell que realiza operaciones para los elementos que usan más de un contenedor. Esta clase se deriva de la [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase base. La tabla siguiente se enumeran los cmdlets que expone esta clase.

|Cmdlet|Definición|
|------------|----------------|
|Combine-Path|Combina dos rutas de acceso en una única ruta de acceso, con un delimitador específico del proveedor entre las rutas de acceso. Este cmdlet transmite las cadenas.|
|`Move-Item`|Mueve los elementos a la ubicación especificada. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|

Un cmdlet relacionado es el cmdlet de ruta de acceso de análisis básico proporcionado por Windows PowerShell. Este cmdlet puede usarse para analizar una ruta de acceso de Windows PowerShell para admitir la `Parent` parámetro. Transmite la cadena de ruta de acceso primaria.

## <a name="select-provider-interfaces-to-support"></a>Seleccionar Interfaces del proveedor de soporte técnico

Además de derivar de una de las clases de base de Windows PowerShell, el proveedor de Windows PowerShell puede admitir otras funcionalidades mediante la derivación de una o varias de las siguientes interfaces de proveedor. En esta sección define las interfaces y los cmdlets que admite cada uno. No describen los parámetros de los cmdlets de interfaz compatible. Información de parámetros del cmdlet está disponible en línea con el `Get-Command` y `Get-Help` cmdlets.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

El [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaz define un proveedor de contenido que realiza operaciones en el contenido de un elemento de datos. En la tabla siguiente se enumera los cmdlets expuestos por esta interfaz.

|Cmdlet|Definición|
|------------|----------------|
|`Add-Content`|Anexa las longitudes de los valores indicados en el contenido del elemento especificado. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|
|`Clear-Content`|Establece el contenido del elemento especificado en el valor "Borrar". Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|
|`Get-Content`|Recupera el contenido de los elementos especificados y transmite los objetos resultantes.|
|`Set-Content`|Reemplaza el contenido existente para los elementos especificados. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

El [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfaz define un proveedor de Windows PowerShell de propiedades que realiza operaciones en las propiedades de elementos en el almacén de datos. En la tabla siguiente se enumera los cmdlets expuestos por esta interfaz.

> [!NOTE]
> El `Path` parámetro sobre estos cmdlets indica una ruta de acceso a un elemento en lugar de identificar una propiedad.

|Cmdlet|Definición|
|------------|----------------|
|`Clear-ItemProperty`|Establece las propiedades de los elementos especificados en el valor "Borrar". Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|
|`Get-ItemProperty`|Recupera las propiedades de los elementos especificados y transmite los objetos resultantes.|
|`Set-ItemProperty`|Establece las propiedades de los elementos especificados con los valores indicados. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

El [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfaz, derivado de [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), define una proveedor que especifica los parámetros dinámicos de sus cmdlets compatibles. Este tipo de proveedor controla las operaciones para el que se pueden definir propiedades en tiempo de ejecución, por ejemplo, una nueva operación de propiedad. Estas operaciones no son posibles en estáticamente después de definir las propiedades de elementos. En la tabla siguiente se enumera los cmdlets expuestos por esta interfaz.

|Cmdlet|Definición|
|------------|----------------|
|`Copy-ItemProperty`|Copia una propiedad del elemento especificado a otro elemento. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|
|`Move-ItemProperty`|Mueve una propiedad del elemento especificado a otro elemento. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|
|`New-ItemProperty`|Crea una propiedad en los elementos especificados y transmite los objetos resultantes.|
|`Remove-ItemProperty`|Quita una propiedad para los elementos especificados.|
|`Rename-ItemProperty`|Cambia el nombre de una propiedad de los elementos especificados. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que su `PassThru` se especifica el parámetro.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

El [System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) interfaz agrega funcionalidad de descriptor de seguridad a un proveedor. Esta interfaz permite al usuario obtener y establecer información de descriptor de seguridad de un elemento en el almacén de datos. En la tabla siguiente se enumera los cmdlets expuestos por esta interfaz.

|Cmdlet|Definición|
|------------|----------------|
|`Get-Acl`|Recupera la información contenida en una lista de control de acceso (ACL), que forma parte de un descriptor de seguridad que se usa para proteger los recursos del sistema operativo, por ejemplo, un archivo o un objeto.|
|`Set-Acl`|Establece la información de una ACL. Es en forma de una instancia de [System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) en los elementos designados para la ruta de acceso especificada. Este cmdlet puede establecer la información sobre archivos, claves y subclaves del registro, o cualquier otro elemento de proveedor, si el proveedor de Windows PowerShell es compatible con la configuración de información de seguridad.|

## <a name="see-also"></a>Véase también

[Creación de proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Cómo funciona Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)