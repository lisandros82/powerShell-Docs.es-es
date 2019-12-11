---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Script
ms.openlocfilehash: e09e86011fa7dbb2a4d7f28b5032b4328b6f6ec2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953072"
---
# <a name="dsc-script-resource"></a>Recurso de DSC Script

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso **Script** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para ejecutar bloques de script de Windows PowerShell en nodos de destino. El recurso **Script** utiliza las propiedades **GetScript** , **SetScript** y **TestScript** que contienen bloques de scripts que se definen para realizar las operaciones de estado DSC correspondientes.

## <a name="syntax"></a>Sintaxis

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> Los bloques **GetScript**, **TestScript** y **SetScript** se almacenan como cadenas.

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|GetScript |Un bloque de scripts que devuelve el estado actual del nodo. |
|SetScript |Un bloque de scripts que usa DSC para aplicar el cumplimiento cuando el nodo no está en el estado deseado. |
|TestScript |Un bloque de scripts que determina si el nodo está en el estado deseado. |
|Credential |Indica las credenciales que se usan para ejecutar este script, si se necesitan credenciales. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

### <a name="additional-information"></a>Información adicional

#### <a name="getscript"></a>GetScript

DSC no utiliza la salida de **GetScript**. El cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) ejecuta **GetScript** para recuperar el estado actual de un nodo. Un valor devuelto no es necesario de **GetScript**. Si especifica un valor devuelto, debe ser una tabla hash que contenga una tecla **Result** cuyo valor sea una cadena.

#### <a name="testscript"></a>TestScript

DSC ejecuta **TestScript** para determinar si se debe ejecutar **SetScript**. Si **SetScript** devuelve `$false`, DSC ejecuta **SetScript** para devolver al nodo al estado deseado. Debe devolver un valor booleano. Un resultado de `$true` indica que el nodo es compatible y que **SetScript** no debe ejecutar.

El cmdlet [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) ejecuta **TestScript** para recuperar el cumplimiento de los nodos con los recursos **Script**.
Pero, en este caso, **SetScript** no se ejecuta, con independencia de lo que devuelva el bloque **TestScript**.

> [!NOTE]
> Toda la salida de su **TestScript** es parte de su valor devuelto. PowerShell interpreta la salida no suprimida como distinta de cero, lo que significa que **TestScript** devolverá `$true`, con independencia del estado del nodo. Esto da como resultado resultados impredecibles, falsos positivos y dificulta la resolución de problemas.

#### <a name="setscript"></a>SetScript

**SetScript** modifica el nodo para aplicar el estado deseado. Se invoca mediante el DSC si el bloque de scripts **TestScript** devuelve `$false`. **SetScript** no debe tener ningún valor devuelto.

## <a name="examples"></a>Ejemplos

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Ejemplo 1: Escribir texto de ejemplo con un recurso de Script

En este ejemplo se comprueba la existencia de `C:\TempFolder\TestFile.txt` en cada nodo. Si no existe, se crea mediante el `SetScript`. El `GetScript` devuelve el contenido del archivo y su valor devuelto no se utiliza.

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Ejemplo 2: Comparar la información de versión con un recurso de Script

En este ejemplo se recupera la información de la versión *compatible* de un archivo de texto en el equipo de creación y la almacena en la variable `$version`. Al generar el archivo MOF del nodo, DSC reemplaza las variables de `$using:version` en cada bloque de scripts con el valor de la variable `$version`.
Durante la ejecución, la versión *compatible* se almacena en un archivo de texto en cada nodo y se compara y actualiza en ejecuciones posteriores.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```