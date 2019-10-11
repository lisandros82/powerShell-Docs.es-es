---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC File
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954682"
---
# <a name="dsc-file-resource"></a>Recurso de DSC File

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso **File** de Desired State Configuration (DSC) de Windows PowerShell ofrece un mecanismo para administrar archivos y carpetas en el nodo de destino. Las propiedades **DestinationPath** y **SourcePath** deben ser accesibles para el nodo de destino.

## <a name="syntax"></a>Sintaxis

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|DestinationPath |La ubicación, en el nodo de destino, que quiere comprobar es **Present** o **Absent** con **Ensure**. |
|Atributos |El estado deseado de los atributos del archivo o directorio de destino. Los valores válidos son _Archive_, _Hidden_, _ReadOnly_ y _System_. |
|Checksum |El tipo de suma de comprobación para determinar si dos archivos son iguales. Los valores válidos son: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. |
|Contenido |Solo es válido cuando se usa con el tipo **Type** **File**. Indica que los contenidos de **Ensure** son **Present** o **Absent** del archivo de destino. |
|Credential |Las credenciales necesarias para acceder a recursos, como archivos de origen. |
|Force |Anula las operaciones de acceso que provocarían un error (por ejemplo, sobrescribir un archivo o eliminar un directorio que no está vacío). El valor predeterminado es `$false`. |
|Recurse |Solo es válido cuando se usa con el tipo **Type** **Directory**. Realiza la operación de estado forma recursiva en todos los subdirectorios. El valor predeterminado es `$false`. |
|SourcePath |La ruta de acceso de la que se copiará el recurso de archivo o carpeta. |
|Tipo |El tipo de recurso que se está configurando. Los valores válidos son **Directory** y **File**. El valor predeterminado es **File**. |
|MatchSource |Determina si el recurso debe supervisar los nuevos archivos agregados al directorio de origen después de la copia inicial. Un valor de `$true` indica que, después de la copia inicial, los nuevos archivos de origen deben copiarse en el destino. Si se establece en `$false`, el recurso almacena en caché el contenido del directorio de origen y omite los archivos agregados después de la copia inicial. El valor predeterminado es `$false`. |

> [!WARNING]
> Si no especifica un valor para **Credential** o **PSRunAsCredential**, el recurso usará la cuenta de equipo del nodo de destino para tener acceso a **SourcePath**. Cuando **SourcePath** es un recurso compartido de UNC, podría provocar un error de "Acceso denegado". Asegúrese de los permisos se establecen en consecuencia, o use las propiedades **Credential** o **PSRunAsCredential** para especificar la cuenta que debe usarse.

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina si el archivo y **Contents** deben existir o no en **Destination**. Establezca esta propiedad en **Present** para asegurarse de que el archivo exista. Establézcala en **Absent** para asegurarse de que no exista. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

### <a name="additional-information"></a>Información adicional

- Cuando se especifica solo un **DestinationPath**, el recurso comprueba que la ruta de acceso existe, si es **Present**, o no existe, si es **Absent**.
- Cuando se especifica**SourcePath** y un **DestinationPath** con un valor **Type** de **Directory**, el recurso copia el directorio de origen en la ruta de acceso de destino. Las propiedades **Recurse**, **Force** y **MatchSource** cambian el tipo de operación de copia realizada, mientras que **Credential** determina qué cuenta se usa para tener acceso al directorio de origen.
- Si especificó un valor de **ReadOnly** para la propiedad **Attributes** junto con un **DestinationPath**, **Ensure** **Present** crearía la ruta de acceso especificada, mientras que **Contents** establecería el contenido del archivo. Un **Ensure** **Absent** omitiría la propiedad **Attributes** completamente y quitaría cualquier archivo en la ruta especificada.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se copia un directorio y sus subdirectorios de un servidor de extracción a un nodo de destino utilizando el archivo de recursos. Si la operación se realiza correctamente, el recurso de registro escribe un mensaje de confirmación en el registro de eventos.

El directorio de origen es una ruta de acceso UNC (`\\PullServer\DemoSource`) compartida desde el servidor de extracción. La propiedad **Recurse** garantiza que también se copian todos los subdirectorios.

> [!IMPORTANT]
> El LCM en el nodo de destino se ejecuta en el contexto de la cuenta sistema local de forma predeterminada. Para conceder acceso a **SourcePath**, asigne los permisos adecuados a la cuenta de equipo del nodo de destino. **Credential** y **PSDSCRunAsCredential** cambian el contexto que usa el LCM para tener acceso a **SourcePath**. Aun será necesario que conceda acceso a la cuenta que se usará para tener acceso a **SourcePath**.

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