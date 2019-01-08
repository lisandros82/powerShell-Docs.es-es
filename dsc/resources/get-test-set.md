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
# <a name="get-test-set"></a><span data-ttu-id="b4914-103">Get-conjunto de pruebas</span><span class="sxs-lookup"><span data-stu-id="b4914-103">Get-Test-Set</span></span>

><span data-ttu-id="b4914-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b4914-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Obtención, prueba y establecimiento](/media/get-test-set.png)

<span data-ttu-id="b4914-106">Desired State Configuration de PowerShell se crea en torno a un **obtener**, **prueba**, y **establecer** proceso.</span><span class="sxs-lookup"><span data-stu-id="b4914-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="b4914-107">DSC [recursos](resources.md) cada una contiene métodos para completar cada una de estas operaciones.</span><span class="sxs-lookup"><span data-stu-id="b4914-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="b4914-108">En un [configuración](../configurations/configurations.md), definir bloques de recursos para rellenar las claves que se convierten en parámetros para un recurso **obtener**, **prueba**, y **establecer** métodos.</span><span class="sxs-lookup"><span data-stu-id="b4914-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="b4914-109">Ésta es la sintaxis para una **servicio** bloque de recursos.</span><span class="sxs-lookup"><span data-stu-id="b4914-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="b4914-110">El **servicio** recursos configura servicios de Windows.</span><span class="sxs-lookup"><span data-stu-id="b4914-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="b4914-111">El **obtener**, **prueba**, y **establecer** métodos de la **servicio** recursos tendrá bloques de parámetros que aceptan estos valores.</span><span class="sxs-lookup"><span data-stu-id="b4914-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="b4914-112">Determina el idioma y el método utilizado para definir el recurso la **obtener**, **prueba**, y **establecer** se definirán los métodos.</span><span class="sxs-lookup"><span data-stu-id="b4914-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="b4914-113">Porque el **servicio** recurso solo tiene una clave necesaria (`Name`), un **servicio** recursos bloque podrían ser tan simple como esto:</span><span class="sxs-lookup"><span data-stu-id="b4914-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="b4914-114">Cuando se compila la configuración anterior, los valores que especifique para una clave se almacenan en el archivo "MOF" que se genera.</span><span class="sxs-lookup"><span data-stu-id="b4914-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="b4914-115">Para obtener más información, consulte [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="b4914-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="b4914-116">Cuando se aplica, la [Localconfigurationmanager](../managing-nodes/metaConfig.md) leerá el valor "Spooler" desde el archivo ".mof" y pasarlo a la `-Name` parámetro de la **obtener**, **prueba**, y **establecer** métodos para la instancia "MyService" de la **servicio** recursos.</span><span class="sxs-lookup"><span data-stu-id="b4914-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="b4914-117">Get</span><span class="sxs-lookup"><span data-stu-id="b4914-117">Get</span></span>

<span data-ttu-id="b4914-118">El **obtener** método de un recurso, recupera el estado del recurso que está configurada en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="b4914-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="b4914-119">Este estado se devuelve como un [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="b4914-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="b4914-120">Las claves de la **hashtable** serán los valores configurables, o parámetros, acepta el recurso.</span><span class="sxs-lookup"><span data-stu-id="b4914-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="b4914-121">El **obtener** método asigna directamente a la [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b4914-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="b4914-122">Cuando se llama a `Get-DSCConfiguration`, se ejecuta el LCM la **obtener** método de cada recurso en la configuración aplicada actualmente.</span><span class="sxs-lookup"><span data-stu-id="b4914-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="b4914-123">El LCM usa los valores de clave que se almacena en el archivo "MOF" como parámetros para cada instancia de recurso correspondiente.</span><span class="sxs-lookup"><span data-stu-id="b4914-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="b4914-124">Se trata de salida de ejemplo de un **servicio** recursos que configura el servicio de "Cola".</span><span class="sxs-lookup"><span data-stu-id="b4914-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="b4914-125">La salida muestra las propiedades actuales del valor configurable por el **servicio** recursos.</span><span class="sxs-lookup"><span data-stu-id="b4914-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="b4914-126">Test</span><span class="sxs-lookup"><span data-stu-id="b4914-126">Test</span></span>

<span data-ttu-id="b4914-127">El **prueba** método de un recurso determina si el nodo de destino es compatible actualmente con el recurso *estado deseado*.</span><span class="sxs-lookup"><span data-stu-id="b4914-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="b4914-128">El **prueba** devuelve del método `$True` o `$False` sólo para indicar si el nodo es compatible.</span><span class="sxs-lookup"><span data-stu-id="b4914-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="b4914-129">Cuando se llama a [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), las llamadas de LCM el **prueba** método de cada recurso en la configuración aplicada actualmente.</span><span class="sxs-lookup"><span data-stu-id="b4914-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="b4914-130">El LCM usa los valores de clave que se almacena en el archivo "MOF" como parámetros para cada instancia de recurso correspondiente.</span><span class="sxs-lookup"><span data-stu-id="b4914-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="b4914-131">Si el resultado de cualquier recurso individual **prueba** es `$False`, `Test-DSCConfiguration` devuelve `$False` que indica que el nodo no es compatible.</span><span class="sxs-lookup"><span data-stu-id="b4914-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="b4914-132">Si todos los recursos **prueba** métodos devuelven `$True`, `Test-DSCConfiguration` devuelve `$True` para indicar que el nodo es compatible.</span><span class="sxs-lookup"><span data-stu-id="b4914-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="b4914-133">A partir de PowerShell 5.0, el `-Detailed` se agregó el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b4914-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="b4914-134">Especificar `-Detailed` hace `Test-DSCConfiguration` para devolver un objeto que contiene las colecciones de resultados para los recursos compatibles y no compatibles.</span><span class="sxs-lookup"><span data-stu-id="b4914-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="b4914-135">Para obtener más información, consulte [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="b4914-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="b4914-136">Establecer</span><span class="sxs-lookup"><span data-stu-id="b4914-136">Set</span></span>

<span data-ttu-id="b4914-137">El **establecer** método de un recurso intenta forzar que el nodo para cumplir con el recurso *estado deseado*.</span><span class="sxs-lookup"><span data-stu-id="b4914-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="b4914-138">El **establecer** método está pensado para ser **idempotente**, lo que significa que **establecer** posible ejecutar varias veces y siempre obtendrá el mismo resultado sin errores.</span><span class="sxs-lookup"><span data-stu-id="b4914-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="b4914-139">Al ejecutar [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), los ciclos de LCM a través de cada recurso en la configuración aplicada actualmente.</span><span class="sxs-lookup"><span data-stu-id="b4914-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="b4914-140">El LCM recupera valores de clave para la instancia actual del recurso desde el archivo ".mof" y usarlas como parámetros para el **prueba** método.</span><span class="sxs-lookup"><span data-stu-id="b4914-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="b4914-141">Si el **prueba** devuelve del método `$True`, el nodo es compatible con el recurso actual y el **establecer** se omite el método.</span><span class="sxs-lookup"><span data-stu-id="b4914-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="b4914-142">Si el **prueba** devuelve `$False`, el nodo no es compatible.</span><span class="sxs-lookup"><span data-stu-id="b4914-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="b4914-143">El LCM pasa el recurso de los valores de clave de la instancia como parámetros para el recurso **establecer** método, restaurar el nodo para el cumplimiento de normas.</span><span class="sxs-lookup"><span data-stu-id="b4914-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="b4914-144">Especificando el `-Verbose` y `-Wait` parámetros, puede ver el progreso de la `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b4914-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="b4914-145">En este ejemplo, el nodo ya es compatible.</span><span class="sxs-lookup"><span data-stu-id="b4914-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="b4914-146">El `Verbose` resultado indica que el **establecer** se omitió el método.</span><span class="sxs-lookup"><span data-stu-id="b4914-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b4914-147">Vea también</span><span class="sxs-lookup"><span data-stu-id="b4914-147">See also</span></span>

- [<span data-ttu-id="b4914-148">Información general de DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="b4914-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="b4914-149">Configuración de un servidor de extracción SMB</span><span class="sxs-lookup"><span data-stu-id="b4914-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="b4914-150">Configuración de un cliente de extracción</span><span class="sxs-lookup"><span data-stu-id="b4914-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
