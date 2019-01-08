---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Get-conjunto de pruebas
ms.openlocfilehash: e46710954679bf20f4536c6efbcbd4dafd9e629e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402577"
---
# <a name="get-test-set"></a>Get-conjunto de pruebas

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

![Obtención, prueba y establecimiento](/media/get-test-set.png)

Desired State Configuration de PowerShell se crea en torno a un **obtener**, **prueba**, y **establecer** proceso. DSC [recursos](resources.md) cada una contiene métodos para completar cada una de estas operaciones. En un [configuración](../configurations/configurations.md), definir bloques de recursos para rellenar las claves que se convierten en parámetros para un recurso **obtener**, **prueba**, y **establecer** métodos.

Ésta es la sintaxis para una **servicio** bloque de recursos. El **servicio** recursos configura servicios de Windows.

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

El **obtener**, **prueba**, y **establecer** métodos de la **servicio** recursos tendrá bloques de parámetros que aceptan estos valores.

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
> Determina el idioma y el método utilizado para definir el recurso la **obtener**, **prueba**, y **establecer** se definirán los métodos.

Porque el **servicio** recurso solo tiene una clave necesaria (`Name`), un **servicio** recursos bloque podrían ser tan simple como esto:

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

Cuando se compila la configuración anterior, los valores que especifique para una clave se almacenan en el archivo "MOF" que se genera. Para obtener más información, consulte [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

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

Cuando se aplica, la [Localconfigurationmanager](../managing-nodes/metaConfig.md) leerá el valor "Spooler" desde el archivo ".mof" y pasarlo a la `-Name` parámetro de la **obtener**, **prueba**, y **establecer** métodos para la instancia "MyService" de la **servicio** recursos.

## <a name="get"></a>Get

El **obtener** método de un recurso, recupera el estado del recurso que está configurada en el nodo de destino. Este estado se devuelve como un [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Las claves de la **hashtable** serán los valores configurables, o parámetros, acepta el recurso.

El **obtener** método asigna directamente a la [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet. Cuando se llama a `Get-DSCConfiguration`, se ejecuta el LCM la **obtener** método de cada recurso en la configuración aplicada actualmente. El LCM usa los valores de clave que se almacena en el archivo "MOF" como parámetros para cada instancia de recurso correspondiente.

Se trata de salida de ejemplo de un **servicio** recursos que configura el servicio de "Cola".

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
                       this service, you won’t be able to print or see your printers.
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

La salida muestra las propiedades actuales del valor configurable por el **servicio** recursos.

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

El **prueba** método de un recurso determina si el nodo de destino es compatible actualmente con el recurso *estado deseado*. El **prueba** devuelve del método `$True` o `$False` sólo para indicar si el nodo es compatible.
Cuando se llama a [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), las llamadas de LCM el **prueba** método de cada recurso en la configuración aplicada actualmente. El LCM usa los valores de clave que se almacena en el archivo "MOF" como parámetros para cada instancia de recurso correspondiente.

Si el resultado de cualquier recurso individual **prueba** es `$False`, `Test-DSCConfiguration` devuelve `$False` que indica que el nodo no es compatible. Si todos los recursos **prueba** métodos devuelven `$True`, `Test-DSCConfiguration` devuelve `$True` para indicar que el nodo es compatible.

```powershell
Test-DSCConfiguration
```

```output
True
```

A partir de PowerShell 5.0, el `-Detailed` se agregó el parámetro. Especificar `-Detailed` hace `Test-DSCConfiguration` para devolver un objeto que contiene las colecciones de resultados para los recursos compatibles y no compatibles.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Para obtener más información, consulte [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Establecer

El **establecer** método de un recurso intenta forzar que el nodo para cumplir con el recurso *estado deseado*. El **establecer** método está pensado para ser **idempotente**, lo que significa que **establecer** posible ejecutar varias veces y siempre obtendrá el mismo resultado sin errores.  Al ejecutar [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), los ciclos de LCM a través de cada recurso en la configuración aplicada actualmente. El LCM recupera valores de clave para la instancia actual del recurso desde el archivo ".mof" y usarlas como parámetros para el **prueba** método. Si el **prueba** devuelve del método `$True`, el nodo es compatible con el recurso actual y el **establecer** se omite el método. Si el **prueba** devuelve `$False`, el nodo no es compatible.  El LCM pasa el recurso de los valores de clave de la instancia como parámetros para el recurso **establecer** método, restaurar el nodo para el cumplimiento de normas.

Especificando el `-Verbose` y `-Wait` parámetros, puede ver el progreso de la `Start-DSCConfiguration` cmdlet. En este ejemplo, el nodo ya es compatible. El `Verbose` resultado indica que el **establecer** se omitió el método.

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

- [Información general de DSC de Azure Automation](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Configuración de un servidor de extracción SMB](../pull-server/pullServerSMB.md)
- [Configuración de un cliente de extracción](../pull-server/pullClientConfigID.md)
