---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Get-Test-Set
ms.openlocfilehash: 42c1df6df2fbf65cbbb8407db613cac2e5b81cfb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954292"
---
# <a name="get-test-set"></a>Get-Test-Set

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

![Obtención, prueba y establecimiento](../media/get-test-set.png)

Desired State Configuration de PowerShell se construye alrededor de un proceso de **Get**, **Test** y **Set**. Cada [recurso](resources.md) de DSC contiene métodos para completar cada una de estas operaciones. En una [configuración](../configurations/configurations.md), se definen bloques de recursos para rellenar claves que se convierten en parámetros para los métodos **Get**, **Test** y **Set** de un recurso.

Esta es la sintaxis para un bloque de recursos **Service**. El recurso **Service** configura servicios de Windows.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

Los métodos **Get**, **Test** y **Set** del recurso **Service** tendrán bloques de parámetros que aceptan estos valores.

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> El lenguaje y el método utilizados para definir el recurso determinan cómo se definirán los métodos **Get**, **Test** y **Set**.

Como el recurso **Service** solo tiene una clave requerida (`Name`), un recurso de bloque **Service** podría ser tan simple como esto:

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

Cuando se compila la configuración anterior, los valores que especifique para una clave se almacenan en el archivo ".mof" que se genera. Para obtener más información, vea [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

Cuando se aplica, el [Administrador de configuración local](../managing-nodes/metaConfig.md) (LCM) leerá el valor "Spooler" desde el archivo ".mof" y lo pasará al parámetro `-Name` de los métodos **Get**, **Test** y **Set** para la instancia "MyService" del recurso **Service**.

## <a name="get"></a>Get

El método **Get** de un recurso recupera el estado del recurso tal y como está configurado en el nodo de destino. Este estado se devuelve como una [tabla hash](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Las claves de la **tabla hash** serán los valores configurables, o parámetros, que acepta el recurso.

El método **Get** se asigna directamente al cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration). Cuando se llama a `Get-DSCConfiguration`, el LCM ejecuta el método **Get** de cada recurso en la configuración aplicada actualmente. El LCM usa los valores de clave almacenados en el archivo ".mof" como parámetros para cada instancia de recurso correspondiente.

Esta es una salida de ejemplo de un recurso **Service** que configura el servicio "Spooler".

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won't be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

La salida muestra las propiedades actuales del valor configurables por el recurso **Service**.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a>Test

El método **Test** de un recurso determina si el nodo de destino es compatible actualmente con el *estado deseado* del recurso. El método **Test** devuelve `$True` o `$False` solo para indicar si el nodo es compatible.
Cuando se llama a [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), el LCM llama al método **Test** de cada recurso en la configuración aplicada actualmente. El LCM usa los valores de clave almacenados en el archivo ".mof" como parámetros para cada instancia de recurso correspondiente.

Si el resultado del método **Test** en cualquier recurso individual es `$False`, `Test-DSCConfiguration` devuelve `$False` para indicar que el nodo no es compatible. Si los métodos **Test** de todos los recursos devuelven `$True`, `Test-DSCConfiguration` devuelve `$True` para indicar que el nodo es compatible.

```powershell
Test-DSCConfiguration
```

```output
True
```

A partir de PowerShell 5.0, se agregó el parámetro `-Detailed`. La especificación de `-Detailed` provoca que `Test-DSCConfiguration` devuelva un objeto que contiene las colecciones de resultados para los recursos compatibles y no compatibles.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Para obtener más información, consulte [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

## <a name="set"></a>Establecer

El método **Set** de un recurso intenta forzar que el nodo sea compatible con el *estado deseado* del recurso. El método **Set** está pensado para ser **idempotente**, lo que significa que **Set** podría ejecutarse varias veces y siempre obtendría el mismo resultado sin errores.  Cuando se ejecuta [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), el LCM pasa en ciclo por cada recurso en la configuración aplicada actualmente. El LCM recupera los valores de clave para la instancia actual del recurso del archivo ".mof" y los usa como parámetros para el método **Test**. Si el método **Test** devuelve `$True`, el nodo es compatible con el recurso actual y se omite el método **Set**. Si **Test** devuelve `$False`, el nodo no es compatible.  El LCM pasa los valores de la clave de la instancia del recurso como parámetros para el método **Set** del recurso, restaurando la compatibilidad del nodo.

Al especificar los parámetros `-Verbose` y `-Wait`, puede observar el progreso del cmdlet `Start-DSCConfiguration`. En este ejemplo, el nodo ya es compatible. La salida `Verbose` indica que el método **Set** se omitió.

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a>Vea también

- [Información general de DSC de Azure Automation](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Configuración de un servidor de extracción SMB](../pull-server/pullServerSMB.md)
- [Configuración de un cliente de extracción](../pull-server/pullClientConfigID.md)
