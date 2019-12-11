---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Depuración de recursos de DSC
ms.openlocfilehash: c088e13a25ba31ceebaf52b2d24b5d32b96ae2fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954262"
---
# <a name="debugging-dsc-resources"></a>Depuración de recursos de DSC

> Se aplica a: Windows PowerShell 5.0

En PowerShell 5.0, se introdujo una nueva característica en Desired State Configuration (DSC) que permite depurar un recurso de DSC mientras se aplica una configuración.

## <a name="enabling-dsc-debugging"></a>Habilitar la depuración de DSC
Antes de poder depurar un recurso, tendrá que habilitar la depuración mediante una llamada al cmdlet [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug).
Este cmdlet toma un parámetro obligatorio, **BreakAll**.

Puede comprobar que se ha habilitado la depuración si examina el resultado de una llamada a [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

En la siguiente salida de PowerShell se muestra el resultado de la habilitación de la depuración:


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a>Iniciar una configuración con la depuración habilitada
Para depurar un recurso de DSC, debe iniciar una configuración que llame a ese recurso.
En este ejemplo, se examinará una configuración simple que llama al recurso **WindowsFeature** para garantizar que se instale la característica "WindowsPowerShellWebAccess":

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
Después de compilar la configuración, iníciela mediante una llamada a [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).
La configuración se detendrá cuando el administrador de configuración local (LCM) llame al primer recurso de la configuración.
Si usa los parámetros `-Verbose` y `-Wait`, la salida mostrará las líneas que se deben especificar para iniciar la depuración.

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
En este punto, el LCM ha llamado al recurso y alcanza el primer punto de interrupción.
En las tres últimas líneas de la salida se muestra cómo adjuntarse al proceso y empezar a depurar el script del recurso.

## <a name="debugging-the-resource-script"></a>Depuración del script del recurso

Inicie una nueva instancia de PowerShell ISE.
En el panel de la consola, escriba las tres últimas líneas de la salida `Start-DscConfiguration` como comandos, reemplazando `<credentials>` por credenciales de usuario válidas.
Ahora debería ver un aviso parecido a:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

El script de recursos se abrirá en el panel de scripts y el depurador se detendrá en la primera línea de la función **Test-TargetResource** (el método **Test()** de un recurso basado en clases).
Ahora, puede utilizar los comandos de depuración en el ISE para seguir los pasos del script de recursos, consultar valores variables, ver la pila de llamadas, etc. Recuerde que cada línea del script de recursos (o clase) se define como un punto de interrupción.

## <a name="disabling-dsc-debugging"></a>Deshabilitar la depuración de DSC

Después de llamar a [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), todas las llamadas a [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) darán como resultado que la configuración interrumpa al depurador. Para permitir que las configuraciones sigan ejecutándose con normalidad, debe deshabilitar la depuración mediante una llamada al cmdlet [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug).

>**Nota:** Reiniciar no cambia el estado de depuración del LCM. Si está habilitada la depuración, iniciar una configuración seguirá interrumpiendo el depurador tras reiniciar.

## <a name="see-also"></a>Véase también

- [Escribir un recurso de DSC personalizado con MOF](../resources/authoringResourceMOF.md)
- [Escribir un recurso de DSC personalizado con clases de PowerShell](../resources/authoringResourceClass.md)
