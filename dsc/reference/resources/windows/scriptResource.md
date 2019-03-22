---
ms.date: 08/24/2018
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Script
ms.openlocfilehash: 86dfb74bf52d8907686bb955fd722f4fb8b9131b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054763"
---
# <a name="dsc-script-resource"></a>Recurso de DSC Script

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso **Script** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para ejecutar bloques de script de Windows PowerShell en nodos de destino. El recurso **Script** utiliza las propiedades `GetScript`, `SetScript` y `TestScript` que contienen bloques de scripts que se definen para realizar las operaciones de estado DSC correspondientes.

## <a name="syntax"></a>Sintaxis

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> Los bloques `GetScript`, `TestScript` y `SetScript` se almacenan como cadenas.

## <a name="properties"></a>Propiedades

|Propiedad|Descripción|
|--------|-----------|
|GetScript|Un bloque de scripts que devuelve el estado actual del nodo.|
|SetScript|Un bloque de scripts que usa DSC para aplicar el cumplimiento cuando el nodo no está en el estado deseado.|
|TestScript|Un bloque de scripts que determina si el nodo está en el estado deseado.|
|Credential| Indica las credenciales que se usan para ejecutar este script, si se necesitan credenciales.|
|DependsOn| Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.

### <a name="getscript"></a>GetScript

DSC no utiliza la salida de `GetScript`. El cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) ejecuta `GetScript` para recuperar el estado actual de un nodo. Un valor devuelto no es necesario de `GetScript`. Si especifica un valor devuelto, debe ser un `hashtable` que contenga una tecla **Result** cuyo valor sea `String`.

### <a name="testscript"></a>TestScript

DSC ejecuta el `TestScript` para determinar si se debe ejecutar el `SetScript`. Si `TestScript` devuelve `$false`, DSC ejecuta el `SetScript` para devolver al nodo al estado deseado. Debe devolver un valor `boolean`. Un resultado de `$true` indica que el nodo es compatible y que `SetScript` no debe ejecutar.

El cmdlet [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) ejecuta el `TestScript` para recuperar el cumplimiento de los nodos con los recursos **Script**. Sin embargo, en este caso, el `SetScript` no se ejecuta, con independencia de lo que devuelva el bloque `TestScript`.

> [!NOTE]
> Toda la salida de su `TestScript` es parte de su valor devuelto. PowerShell interpreta la salida no suprimida como distinta de cero, lo que significa que `TestScript` devolverá `$true`, con independencia del estado del nodo.
> Esto da como resultado resultados impredecibles, falsos positivos y dificulta la resolución de problemas.

### <a name="setscript"></a>SetScript

El `SetScript` modifica el nodo para aplicar el estado deseado. Se invoca mediante el DSC si el bloque de scripts `TestScript` devuelve `$false`. El `SetScript` no debe tener ningún valor devuelto.

## <a name="examples"></a>Ejemplos

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Ejemplo 1: Escribir texto de ejemplo con un recurso de Script

En este ejemplo se comprueba la existencia de `C:\TempFolder\TestFile.txt` en cada nodo. Si no existe, se crea mediante el `SetScript`. El `GetScript` devuelve el contenido del archivo y su valor devuelto no se utiliza.

```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

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

En este ejemplo se recupera la información de la versión *compatible* de un archivo de texto en el equipo de creación y la almacena en la variable `$version`. Al generar el archivo MOF del nodo, DSC reemplaza las variables de `$using:version` en cada bloque de scripts con el valor de la variable `$version`. Durante la ejecución, la versión *compatible* se almacena en un archivo de texto en cada nodo y se compara y actualiza en ejecuciones posteriores.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

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