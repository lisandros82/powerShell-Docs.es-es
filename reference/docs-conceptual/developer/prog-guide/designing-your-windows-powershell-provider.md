---
title: Diseño del proveedor de Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: bfb29fd5df87ffa9ae270c18ce8bfb0c59ee6f90
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870666"
---
# <a name="designing-your-windows-powershell-provider"></a>Diseño del proveedor de Windows PowerShell

Debe implementar un proveedor de Windows PowerShell si su producto o configuración expone un conjunto de datos almacenados, como una base de datos que el usuario desea explorar o examinar. Además, si el producto proporciona un contenedor, aunque no sea un contenedor multinivel, tiene sentido implementar un proveedor de Windows PowerShell. Por ejemplo, puede que desee implementar un proveedor de contenedores de Windows PowerShell si el verbo de cmdlet Copy, Move, Rename, New o Remove tiene sentido como una operación en los datos de configuración o del producto.

## <a name="windows-powershell-paths-identify-your-provider"></a>Las rutas de Windows PowerShell identifican el proveedor

El tiempo de ejecución de Windows PowerShell usa las rutas de acceso de Windows PowerShell para acceder al proveedor de Windows PowerShell adecuado. Cuando un cmdlet especifica una de estas rutas de acceso, el motor en tiempo de ejecución sabe qué proveedor se debe usar para acceder al almacén de datos asociado. Estas rutas de acceso incluyen rutas de acceso completas de unidad, rutas de acceso calificadas por el proveedor, rutas de acceso directas de proveedor y rutas de acceso internas del proveedor. Cada proveedor de Windows PowerShell debe admitir una o varias de estas rutas de acceso.

Para obtener más información sobre las rutas de Windows PowerShell, vea cómo funciona Windows PowerShell.

### <a name="defining-a-drive-qualified-path"></a>Definir una ruta de acceso calificada para una unidad

Para permitir que el usuario acceda a los datos ubicados en una unidad física, el proveedor de Windows PowerShell debe admitir una ruta de acceso completa a la unidad. Esta ruta de acceso comienza con el nombre de la unidad seguido de dos puntos (:), por ejemplo, unidad: \ abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Definir una ruta de acceso calificada por el proveedor

Para permitir que el tiempo de ejecución de Windows PowerShell inicialice y desinicialice el proveedor, el proveedor de Windows PowerShell debe admitir una ruta de acceso calificada por el proveedor. Por ejemplo, FileSystem::\\\uncshare\abc\bar es la ruta de acceso completa del proveedor del sistema filesystem proporcionado por Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Definir una ruta de acceso directa de proveedor

Para permitir el acceso remoto a su proveedor de Windows PowerShell, debe admitir una ruta de acceso directa de proveedor para pasar directamente al proveedor de Windows PowerShell para la ubicación actual. Por ejemplo, el proveedor de Windows PowerShell del registro puede usar \\\server\regkeypath como una ruta de acceso directa de proveedor.

### <a name="defining-a-provider-internal-path"></a>Definir una ruta de acceso interna del proveedor

Para permitir que el cmdlet de proveedor acceda a los datos mediante interfaces de programación de aplicaciones (API) que no son de Windows PowerShell, el proveedor de Windows PowerShell debe admitir una ruta de acceso interna del proveedor. Esta ruta de acceso se indica después de "::" en la ruta de acceso completa del proveedor. Por ejemplo, la ruta de acceso interna del proveedor para el proveedor de Windows PowerShell de sistema de archivos es \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>Cambiar datos almacenados

Al reemplazar métodos que modifican el almacén de datos subyacente, llame siempre al método [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) con la versión más actualizada del elemento modificado por ese método. La infraestructura del proveedor determina si el objeto de elemento se debe pasar a la canalización, como cuando el usuario especifica el parámetro-PassThru. Si la recuperación del elemento más actualizado es una operación costosa (con el rendimiento), puede probar la propiedad context. PassThru para determinar si realmente necesita escribir el elemento resultante.

## <a name="choose-a-base-class-for-your-provider"></a>Elegir una clase base para el proveedor

Windows PowerShell proporciona una serie de clases base que puede usar para implementar su propio proveedor de Windows PowerShell. Al diseñar un proveedor, elija la clase base, que se describe en esta sección, que sea más adecuada para sus requisitos.

Cada clase base del proveedor de Windows PowerShell pone a disposición un conjunto de cmdlets. En esta sección se describen los cmdlets de, pero no se describen sus parámetros.

Con el estado de sesión, el tiempo de ejecución de Windows PowerShell hace que varios cmdlets de ubicación estén disponibles para ciertos proveedores de Windows PowerShell, como los cmdlets `Get-Location`, `Set-Location`, `Pop-Location`y `Push-Location`. Puede usar el cmdlet `Get-Help` para obtener información acerca de estos cmdlets de ubicación.

### <a name="cmdletprovider-base-class"></a>Clase base CmdletProvider

La clase [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) define un proveedor básico de Windows PowerShell. Esta clase admite la declaración de proveedor y proporciona una serie de propiedades y métodos que están disponibles para todos los proveedores de Windows PowerShell.
El cmdlet `Get-PSProvider` invoca la clase para enumerar todos los proveedores disponibles para una sesión.
La implementación de este cmdlet se proporciona mediante el estado de sesión.

> [!NOTE]
> Los proveedores de Windows PowerShell están disponibles para todos los ámbitos de lenguaje de Windows PowerShell.

### <a name="drivecmdletprovider-base-class"></a>Clase base DriveCmdletProvider

La clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) define un proveedor de unidades de Windows PowerShell que admite operaciones para agregar nuevas unidades, quitar unidades existentes e inicializar las unidades predeterminadas. Por ejemplo, el proveedor FileSystem proporcionado por Windows PowerShell inicializa unidades para todos los volúmenes montados, como unidades de disco duro y unidades de dispositivo CD/DVD.

Esta clase se deriva de la clase base [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . En la tabla siguiente se enumeran los cmdlets expuestos por esta clase. Además de los enumerados, el cmdlet `Get-PSDrive` (expuesto por el estado de sesión) es un cmdlet relacionado que se usa para recuperar las unidades disponibles.

|      Cmdlet      |                             Definición                              |
| ---------------- | ------------------------------------------------------------------- |
| `New-PSDrive`    | Crea una nueva unidad para la sesión y transmite la información de la unidad. |
| `Remove-PSDrive` | Quita una unidad de la sesión.                                   |

### <a name="itemcmdletprovider-base-class"></a>Clase base ItemCmdletProvider

La clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) define un proveedor de elementos de Windows PowerShell que realiza operaciones en los elementos individuales del almacén de datos y no asume ninguna funcionalidad de navegación o contenedor. Esta clase se deriva de la clase base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . En la tabla siguiente se enumeran los cmdlets expuestos por esta clase.

|     Cmdlet     |                                                                                                                                                            Definición                                                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-Item`   | Borra el contenido actual de los elementos que se encuentra en la ubicación especificada y lo reemplaza por el valor "Clear" especificado por el proveedor. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`.                                                                                   |
| `Get-Item`     | Recupera elementos de la ubicación especificada y transmite los objetos resultantes.                                                                                                                                                                                                                                                  |
| `Invoke-Item`  | Invoca la acción predeterminada para el elemento en la ruta de acceso especificada.                                                                                                                                                                                                                                                                   |
| `Set-Item`     | Establece un elemento en la ubicación especificada con el valor indicado. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`.                                                                                                                                                   |
| `Resolve-Path` | Resuelve los caracteres comodín para una ruta de acceso de Windows PowerShell y transmite información de la ruta de acceso.                                                                                                                                                                                                                                              |
| `Test-Path`    | Comprueba la ruta de acceso especificada y devuelve `true` si existe y `false` de lo contrario. Este cmdlet se implementa para admitir el parámetro `IsContainer` para el método [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) . |

### <a name="containercmdletprovider-base-class"></a>Clase base ContainerCmdletProvider

La clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) define un proveedor de contenedores de Windows PowerShell que expone un contenedor, para los elementos del almacén de datos, al usuario. Tenga en cuenta que solo se puede usar un proveedor de contenedores de Windows PowerShell cuando hay un contenedor (sin contenedores anidados) con elementos contenidos en él. Si hay contenedores anidados, debe implementar un proveedor de navegación de Windows PowerShell.

Esta clase se deriva de la clase base [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . En la tabla siguiente se definen los cmdlets implementados por esta clase.

|     Cmdlet      |                                                                        Definición                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Copy-Item`     | Copia los elementos de una ubicación a otra. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`. |
| `Get-Childitem` | Recupera los elementos secundarios en la ubicación especificada y los transmite como objetos.                                                                        |
| `New-Item`      | Crea nuevos elementos en la ubicación especificada y transmite el objeto resultante.                                                                           |
| `Remove-Item`   | Quita los elementos de la ubicación especificada.                                                                                                               |
| `Rename-Item`   | Cambia el nombre de un elemento en la ubicación especificada. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`. |

### <a name="navigationcmdletprovider-base-class"></a>Clase base NavigationCmdletProvider

La clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) define un proveedor de navegación de Windows PowerShell que realiza operaciones para elementos que usan más de un contenedor. Esta clase se deriva de la clase base [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . En la tabla siguiente se enumeran los cmdlets expuestos por esta clase.

|    Cmdlet    |                                                                      Definición                                                                      |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Combinar-ruta de acceso | Combina dos rutas de acceso en una única ruta de acceso, utilizando un delimitador específico del proveedor entre las rutas de acceso. Este cmdlet transmite cadenas.                               |
| `Move-Item`  | Mueve los elementos a la ubicación especificada. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`. |

Un cmdlet relacionado es el cmdlet Parse-path básico proporcionado por Windows PowerShell. Este cmdlet se puede usar para analizar una ruta de acceso de Windows PowerShell para admitir el parámetro `Parent`. Transmite la cadena de ruta de acceso primaria.

## <a name="select-provider-interfaces-to-support"></a>Seleccionar interfaces de proveedor para admitir

Además de derivar de una de las clases base de Windows PowerShell, el proveedor de Windows PowerShell puede admitir otras funciones mediante la derivación de una o varias de las siguientes interfaces de proveedor. En esta sección se definen las interfaces y los cmdlets que admite cada uno. No describe los parámetros de los cmdlets admitidos por la interfaz. La información de parámetros de cmdlet está disponible en línea con los cmdlets `Get-Command` y `Get-Help`.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

La interfaz [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) define un proveedor de contenido que realiza operaciones en el contenido de un elemento de datos. En la tabla siguiente se enumeran los cmdlets expuestos por esta interfaz.

|     Cmdlet      |                                                                                        Definición                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Add-Content`   | Anexa las longitudes de los valores indicados al contenido del elemento especificado. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`. |
| `Clear-Content` | Establece el contenido del elemento especificado en el valor "Clear". Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`.               |
| `Get-Content`   | Recupera el contenido de los elementos especificados y transmite los objetos resultantes.                                                                                                         |
| `Set-Content`   | Reemplaza el contenido existente para los elementos especificados. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`.                     |

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

La interfaz [System. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) define una propiedad proveedor de Windows PowerShell que realiza operaciones en las propiedades de los elementos del almacén de datos. En la tabla siguiente se enumeran los cmdlets expuestos por esta interfaz.

> [!NOTE]
> El parámetro `Path` en estos cmdlets indica una ruta de acceso a un elemento en lugar de identificar una propiedad.

|        Cmdlet        |                                                                                   Definición                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-ItemProperty` | Establece las propiedades de los elementos especificados en el valor "Clear". Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`.      |
| `Get-ItemProperty`   | Recupera las propiedades de los elementos especificados y transmite los objetos resultantes.                                                                                                |
| `Set-ItemProperty`   | Establece las propiedades de los elementos especificados con los valores indicados. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`. |

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

La interfaz [System. Management. Automation. Provider. Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) , derivada de [System. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), define un proveedor que especifica los parámetros dinámicos para sus cmdlets compatibles. Este tipo de proveedor controla las operaciones para las que se pueden definir propiedades en tiempo de ejecución, por ejemplo, una nueva operación de propiedad. Tales operaciones no son posibles en los elementos que tienen propiedades definidas estáticamente.
En la tabla siguiente se enumeran los cmdlets expuestos por esta interfaz.

|        Cmdlet         |                                                                                Definición                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Copy-ItemProperty`   | Copia una propiedad del elemento especificado en otro elemento. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`. |
| `Move-ItemProperty`   | Mueve una propiedad del elemento especificado a otro elemento. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`.  |
| `New-ItemProperty`    | Crea una propiedad en los elementos especificados y transmite los objetos resultantes.                                                                                             |
| `Remove-ItemProperty` | Quita una propiedad de los elementos especificados.                                                                                                                              |
| `Rename-ItemProperty` | Cambia el nombre de una propiedad de los elementos especificados. Este cmdlet no pasa un objeto de salida a través de la canalización a menos que se especifique su parámetro `PassThru`.                 |

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

La interfaz [System. Management. Automation. Provider. Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) agrega la funcionalidad del descriptor de seguridad a un proveedor. Esta interfaz permite al usuario obtener y establecer información del descriptor de seguridad para un elemento en el almacén de datos. En la tabla siguiente se enumeran los cmdlets expuestos por esta interfaz.

|  Cmdlet   |                                                                                                                                                                                                          Definición                                                                                                                                                                                                          |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Get-Acl` | Recupera la información contenida en una lista de control de acceso (ACL), que forma parte de un descriptor de seguridad que se usa para proteger los recursos del sistema operativo, por ejemplo, un archivo o un objeto.                                                                                                                                                                                                                                      |
| `Set-Acl` | Establece la información de una ACL. Está en forma de una instancia de [System. Security. AccessControl. objeto ObjectSecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) en los elementos designados para la ruta de acceso especificada. Este cmdlet puede establecer información sobre archivos, claves y subclaves en el registro, o cualquier otro elemento de proveedor, si el proveedor de Windows PowerShell admite la configuración de la información de seguridad. |

## <a name="see-also"></a>Vea también

[Crear proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Cómo funciona Windows PowerShell](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)