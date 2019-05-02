---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC File
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077337"
---
# <a name="dsc-file-resource"></a>Recurso de DSC File

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

El recurso File de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar archivos y carpetas en el nodo de destino. Las propiedades **DestinationPath** y **SourcePath** deben ser accesibles para el nodo de destino.

## <a name="syntax"></a>Sintaxis

```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad       |Descripción                                                                   |Requerido|Valor predeterminado|
|---------------|------------------------------------------------------------------------------|--------|-------|
|DestinationPath|La ubicación, en el nodo de destino, que desea comprobar es `Present` o `Absent`.|Sí|No|
|Atributos     |El estado deseado de los atributos del archivo o directorio de destino. Los valores válidos son **Archive**, **Hidden**, **ReadOnly** y **System**.|No|Ninguno|
|Checksum      |El tipo de suma de comprobación para determinar si dos archivos son iguales. Los valores válidos son: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|No|Se compara solo el nombre de archivo o directorio.|
|Contenido       |Solo es válido cuando se usa con el tipo `File`. Indica que los contenidos de Ensure son `Present` o `Absent` del archivo de destino. |No|Ninguno|
|Credential     |Las credenciales necesarias para acceder a recursos, como archivos de origen.|No|La cuenta de equipo del nodo de destino. (*Ver nota*)|
|Ensure         |El estado deseado del directorio o archivo de destino. |No|**Presente**|
|Force          |Anula las operaciones de acceso que provocarían un error (por ejemplo, sobrescribir un archivo o eliminar un directorio que no está vacío).|No|`$false`|
|Recurse        |Solo es válido cuando se usa con el tipo `Directory`. Realiza la operación de estado forma recursiva en todos los subdirectorios.|No|`$false`|
|DependsOn      |Establece una dependencia en los recursos especificados. Este recurso solo se ejecutará después de la ejecución correcta de los recursos dependientes. Puede especificar los recursos dependientes utilizando la sintaxis `"[ResourceType]ResourceName"`. Consulte [about_DependsOn](../../../configurations/resource-depends-on.md)|No|Ninguno|
|SourcePath     |La ruta de acceso de la que se copiará el recurso de archivo o carpeta.|No|Ninguno|
|Tipo           |El tipo de recurso que se está configurando. Los valores válidos son `Directory` y `File`.|No|`File`|
|MatchSource    |Determina si el recurso debe supervisar los nuevos archivos agregados al directorio de origen después de la copia inicial. Un valor de `$true` indica que, después de la copia inicial, los nuevos archivos de origen deben copiarse en el destino. Si se establece en `$False`, el recurso almacena en caché el contenido del directorio de origen y omite los archivos agregados después de la copia inicial.|No|`$false`|

> [!WARNING]
> Si no especifica un valor para `Credential` o `PSRunAsCredential` (PS V.5), el recurso usará la cuenta de equipo del nodo de destino para tener acceso a `SourcePath`.  Cuando el `SourcePath` es un recurso compartido de UNC, podría provocar un error de "Acceso denegado". Asegúrese de los permisos se establecen en consecuencia, o use las propiedades `Credential` o `PSRunAsCredential` para especificar la cuenta que debe usarse.

## <a name="present-vs-absent"></a>Present o Absent

Cada recurso de DSC realiza diferentes operaciones basadas en el valor especificado para la propiedad `Ensure`. Los valores que especifique para las propiedades anteriores determinan la operación de estado realizada.

### <a name="existence"></a>Existencia

Cuando se especifica solo un `DestinationPath`, el recurso comprueba que la ruta de acceso existe (`Present`) o no existe (`Absent`).

### <a name="copy-operations"></a>Operaciones de copia

Cuando se especifica un `SourcePath` y un `DestinationPath` con un `Type` valor **Directory**, el recurso copia el directorio de origen en la ruta de acceso de destino. Las propiedades `Recurse`, `Force` y `MatchSource` cambian el tipo de operación de copia realizada, mientras que `Credential` determina qué cuenta se usa para tener acceso al directorio de origen.

### <a name="limitations"></a>Limitaciones

Si especificó un valor de `ReadOnly` para la propiedad `Attributes` junto con `DestinationPath`, `Ensure = "Present"` crearía la ruta de acceso especificada, mientras que `Contents` establecería el contenido del archivo.  Una operación de estado `Absent` omitiría la propiedad `Attributes` completamente y quitaría cualquier archivo en la ruta especificada.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se copia un directorio y sus subdirectorios de un servidor de extracción a un nodo de destino utilizando el archivo de recursos. Si la operación se realiza correctamente, el recurso de registro escribe un mensaje de confirmación en el registro de eventos.

El directorio de origen es una ruta de acceso UNC (`\\PullServer\DemoSource`) compartida desde el servidor de extracción. La propiedad `Recurse` garantiza que también se copian todos los subdirectorios.

> [!IMPORTANT]
> El LCM en el nodo de destino se ejecuta en el contexto de la cuenta sistema local de forma predeterminada. Para conceder acceso a **SourcePath**, asigne los permisos adecuados a la cuenta de equipo del nodo de destino. **Credential** y **PSDSCRunAsCredential** (v5) cambian el contexto que usa el LCM para tener acceso a **SourcePath**. Aun será necesario que conceda acceso a la cuenta que se usará para tener acceso a **SourcePath**.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

Para obtener más detalles sobre el uso de **credenciales** en DSC, consulte la información sobre [ejecutar como usuario](../../../configurations/runAsUser.md) o las [credenciales en datos de configuración](../../../configurations/configDataCredentials.md).
