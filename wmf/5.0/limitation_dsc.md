---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 883f80a5c8c99f2ab9886558a7aebfe1204f3be6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085174"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Problemas y limitaciones conocidos de la configuración de estado deseado (DSC)

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Cambio de última hora: los certificados usados para cifrar o descifrar contraseñas en configuraciones de DSC no funcionan después de instalar WMF 5.0 RTM

En las versiones WMF 4.0 y WMF 5.0 Preview, DSC no permitía que las contraseñas de la configuración tuvieran más de 121 caracteres de longitud. DSC obligaba a usar contraseñas cortas, aunque se deseasen contraseñas largas y seguras. Este cambio de última hora permite que las contraseñas tengan una longitud arbitraria en la configuración de DSC.

**Resolución:** vuelva a crear el certificado mediante el cifrado de datos o el cifrado de clave, así como con el uso mejorado de claves de cifrado de documentos (1.3.6.1.4.1.311.80.1). En el artículo de TechNet <https://technet.microsoft.com/library/dn807171.aspx> encontrará más información.

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>Los cmdlets de DSC puede producir un error después de instalar WMF 5.0 RTM

Start-DscConfiguration y otros cmdlets de DSC pueden generar el siguiente error después de instalar WMF 5.0 RTM:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Resolución:** elimine DSCEngineCache.mof. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>Es posible que los Cmdlets de DSC no funcionen si WMF 5.0 RTM se instala encima de WMF 5.0 Production Preview

**Resolución:** ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>LCM puede entrar en un estado inestable al usar Get-DscConfiguration en DebugMode

Si LCM está en DebugMode, al presionar CTRL+C para detener el procesamiento de Get-DscConfiguration puede causar que LCM entre en un estado inestable que impida funcionar a la mayoría de los cmdlets de DSC.

**Resolución:** no presione CTRL+C mientras se depura el cmdlet Get-DscConfiguration.

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-DscConfiguration puede no responder en DebugMode

Si LCM está en DebugMode, Stop-DscConfiguration puede no responder cuando intenta detener una operación iniciada por Get-DscConfiguration

**Resolución:** finalice la depuración de la operación iniciada por Get-DscConfiguration, como se describe en la sección "[Depuración de recursos de DSC](https://msdn.microsoft.com/powershell/dsc/debugresource)".

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>No se muestran mensajes de error detallados en DebugMode

Si LCM está en DebugMode, no se muestra ningún mensaje de error detallado de recursos de DSC.

**Resolución:** deshabilite *DebugMode* para ver mensajes detallados del recurso

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Las operaciones Invoke-DscResource no se pueden recuperar mediante el cmdlet Get-DscConfigurationStatus

Después de usar el cmdlet Invoke-DscResource para invocar directamente los métodos de cualquier recurso, los registros de esta operación no se pueden recuperar a través de Get-DscConfigurationStatus posteriormente.

**Resolución:** Ninguna.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus devuelve operaciones de ciclo de extracción como de tipo *Consistency*

Cuando un nodo se establece en modo de actualización de extracción, para cada operación de extracción realizada, el cmdlet Get-DscConfigurationStatus indica el tipo de operación como *Consistency* en lugar de *Initial*

**Resolución:** Ninguna.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>El cmdlet Invoke-DscResource no devuelve los mensajes en el orden en que se producen

El cmdlet Invoke-DscResource no devuelve los mensajes detallados, de advertencia ni de error en el orden en que los producen LCM o el recurso de DSC.

**Resolución:** Ninguna.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>Los recursos de DSC no se pueden depurar fácilmente cuando se usan con Invoke-DscResource

Cuando se ejecuta LCM en modo de depuración (consulte [Depuración de recursos de DSC](https://msdn.microsoft.com/powershell/dsc/debugresource) para obtener más detalles), el cmdlet Invoke-DscResource no ofrece información sobre el espacio de ejecución al que debe conectarse para la depuración.
**Resolución:** detecte el espacio de ejecución y conéctese a este mediante los cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess**, **Get-Runspace** y **Debug-Runspace** para depurar el recurso de DSC.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Varios documentos de configuración parcial para el mismo nodo no pueden tener nombres de recurso idénticos

Para varias configuraciones parciales implementadas en un mismo nodo, los nombres idénticos de recursos causan un error en tiempo de ejecución.

**Resolución:** use nombres diferentes para la mismos recursos en distintas configuraciones parciales.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-DscConfiguration –UseExisting no funciona con -Credential

Si se usa Start-DscConfiguration con el parámetro –UseExisting, el parámetro –Credential se ignora. DSC usa la identidad de proceso predeterminada para continuar la operación. Esto provoca un error cuando se necesita una credencial distinta para continuar en el nodo remoto.

**Resolución:** use una sesión CIM para las operaciones remotas de DSC:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>Direcciones IPv6 como nombres de nodo en configuraciones de DSC

No se admiten direcciones IPv6 como nombres de nodo en los scripts de configuración de DSC en esta versión.

**Resolución:** Ninguna.

## <a name="debugging-of-class-based-dsc-resources"></a>Depuración de los recursos de DSC basados en clases

En esta versión no se admite la depuración de los recursos de DSC basado en clases.

**Resolución:** Ninguna.

## <a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Las variables y las funciones que se definen en el ámbito de $script en el recurso basado en clases de DSC no se conservan en varias llamadas a un recurso de DSC

Varias llamadas consecutivas a Start-DSCConfiguration producirán un error si la configuración usa cualquier recurso basado en clases que tenga variables o funciones definidas en el ámbito de $script.

**Resolución:** defina todas las variables y funciones de la propia clase de recurso de DSC. No usar funciones o variables de ámbito $script.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>Depuración de recursos de DSC cuando un recurso usa PSDscRunAsCredential

La depuración de recursos de DSC cuando un recurso usa la propiedad *PSDscRunAsCredential* en la configuración no se admite en esta versión.

**Resolución:** Ninguna.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential no se admite para los recursos compuestos de DSC

**Resolución:** use la propiedad Credential si está disponible. ServiceSet y WindowsFeatureSet de ejemplo

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>*Get-DscResource -Syntax* no refleja PsDscRunAsCredential correctamente

Get-DscResource -Syntax no refleja correctamente la propiedad PsDscRunAsCredential cuando el recurso la marca como obligatoria o no la admite.

**Resolución:** Ninguna. Sin embargo, la configuración de creación en ISE refleja los metadatos correctos acerca de la propiedad PsDscRunAsCredential al usar IntelliSense.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature no está disponible en Windows 7

El recurso de DSC WindowsOptionalFeature no está disponible en Windows 7. Este recurso requiere el módulo DISM, así como los cmdlets DISM que están disponibles a partir de Windows 8 y versiones más recientes del sistema operativo Windows.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>En el caso de los recursos de DSC basados en clases, puede que Import-DscResource -ModuleVersion no funcione según lo previsto

Si el nodo de compilación tiene varias versiones de un módulo de recursos de DSC basados en clases, `Import-DscResource -ModuleVersion` no podrá seleccionar la versión especificada y genera el siguiente error de compilación.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Resolución:** importe la versión necesaria mediante la definición del objeto *ModuleSpecification* en `-ModuleName` con la clave `RequiredVersion` especificada como sigue:

``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Algunos recursos de DSC, como el recurso de registro, pueden comenzar a tardar mucho tiempo en procesar la solicitud.

**Resolución1:** cree una tarea de programación que limpie periódicamente la siguiente carpeta.

``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Resolución2:** cambie la configuración de DSC para limpiar la carpeta *CommandAnalysis* al final de la configuración.

``` PowerShell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
