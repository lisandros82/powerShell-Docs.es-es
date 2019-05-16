---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Get-Test-Set
ms.openlocfilehash: e4aa7770bb5fc8b916b0c0a6488b1ccc0ef0ade9
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229521"
---
# <a name="get-test-set"></a><span data-ttu-id="19d99-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="19d99-103">Get-Test-Set</span></span>

><span data-ttu-id="19d99-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="19d99-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Obtención, prueba y establecimiento](/media/get-test-set.png)

<span data-ttu-id="19d99-106">Desired State Configuration de PowerShell se construye alrededor de un proceso de **Get**, **Test** y **Set**.</span><span class="sxs-lookup"><span data-stu-id="19d99-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="19d99-107">Cada [recurso](resources.md) de DSC contiene métodos para completar cada una de estas operaciones.</span><span class="sxs-lookup"><span data-stu-id="19d99-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="19d99-108">En una [configuración](../configurations/configurations.md), se definen bloques de recursos para rellenar claves que se convierten en parámetros para los métodos **Get**, **Test** y **Set** de un recurso.</span><span class="sxs-lookup"><span data-stu-id="19d99-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="19d99-109">Esta es la sintaxis para un bloque de recursos **Service**.</span><span class="sxs-lookup"><span data-stu-id="19d99-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="19d99-110">El recurso **Service** configura servicios de Windows.</span><span class="sxs-lookup"><span data-stu-id="19d99-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="19d99-111">Los métodos **Get**, **Test** y **Set** del recurso **Service** tendrán bloques de parámetros que aceptan estos valores.</span><span class="sxs-lookup"><span data-stu-id="19d99-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="19d99-112">El lenguaje y el método utilizados para definir el recurso determinan cómo se definirán los métodos **Get**, **Test** y **Set**.</span><span class="sxs-lookup"><span data-stu-id="19d99-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="19d99-113">Como el recurso **Service** solo tiene una clave requerida (`Name`), un recurso de bloque **Service** podría ser tan simple como esto:</span><span class="sxs-lookup"><span data-stu-id="19d99-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="19d99-114">Cuando se compila la configuración anterior, los valores que especifique para una clave se almacenan en el archivo ".mof" que se genera.</span><span class="sxs-lookup"><span data-stu-id="19d99-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="19d99-115">Para obtener más información, vea [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="19d99-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="19d99-116">Cuando se aplica, el [Administrador de configuración local](../managing-nodes/metaConfig.md) (LCM) leerá el valor "Spooler" desde el archivo ".mof" y lo pasará al parámetro `-Name` de los métodos **Get**, **Test** y **Set** para la instancia "MyService" del recurso **Service**.</span><span class="sxs-lookup"><span data-stu-id="19d99-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="19d99-117">Get</span><span class="sxs-lookup"><span data-stu-id="19d99-117">Get</span></span>

<span data-ttu-id="19d99-118">El método **Get** de un recurso recupera el estado del recurso tal y como está configurado en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="19d99-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="19d99-119">Este estado se devuelve como una [tabla hash](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="19d99-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="19d99-120">Las claves de la **tabla hash** serán los valores configurables, o parámetros, que acepta el recurso.</span><span class="sxs-lookup"><span data-stu-id="19d99-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="19d99-121">El método **Get** se asigna directamente al cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="19d99-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="19d99-122">Cuando se llama a `Get-DSCConfiguration`, el LCM ejecuta el método **Get** de cada recurso en la configuración aplicada actualmente.</span><span class="sxs-lookup"><span data-stu-id="19d99-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="19d99-123">El LCM usa los valores de clave almacenados en el archivo ".mof" como parámetros para cada instancia de recurso correspondiente.</span><span class="sxs-lookup"><span data-stu-id="19d99-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="19d99-124">Esta es una salida de ejemplo de un recurso **Service** que configura el servicio "Spooler".</span><span class="sxs-lookup"><span data-stu-id="19d99-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="19d99-125">La salida muestra las propiedades actuales del valor configurables por el recurso **Service**.</span><span class="sxs-lookup"><span data-stu-id="19d99-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="19d99-126">Test</span><span class="sxs-lookup"><span data-stu-id="19d99-126">Test</span></span>

<span data-ttu-id="19d99-127">El método **Test** de un recurso determina si el nodo de destino es compatible actualmente con el *estado deseado* del recurso.</span><span class="sxs-lookup"><span data-stu-id="19d99-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="19d99-128">El método **Test** devuelve `$True` o `$False` solo para indicar si el nodo es compatible.</span><span class="sxs-lookup"><span data-stu-id="19d99-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="19d99-129">Cuando se llama a [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), el LCM llama al método **Test** de cada recurso en la configuración aplicada actualmente.</span><span class="sxs-lookup"><span data-stu-id="19d99-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="19d99-130">El LCM usa los valores de clave almacenados en el archivo ".mof" como parámetros para cada instancia de recurso correspondiente.</span><span class="sxs-lookup"><span data-stu-id="19d99-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="19d99-131">Si el resultado del método **Test** en cualquier recurso individual es `$False`, `Test-DSCConfiguration` devuelve `$False` para indicar que el nodo no es compatible.</span><span class="sxs-lookup"><span data-stu-id="19d99-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="19d99-132">Si los métodos **Test** de todos los recursos devuelven `$True`, `Test-DSCConfiguration` devuelve `$True` para indicar que el nodo es compatible.</span><span class="sxs-lookup"><span data-stu-id="19d99-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="19d99-133">A partir de PowerShell 5.0, se agregó el parámetro `-Detailed`.</span><span class="sxs-lookup"><span data-stu-id="19d99-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="19d99-134">La especificación de `-Detailed` provoca que `Test-DSCConfiguration` devuelva un objeto que contiene las colecciones de resultados para los recursos compatibles y no compatibles.</span><span class="sxs-lookup"><span data-stu-id="19d99-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="19d99-135">Para obtener más información, consulte [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="19d99-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="19d99-136">Establecer</span><span class="sxs-lookup"><span data-stu-id="19d99-136">Set</span></span>

<span data-ttu-id="19d99-137">El método **Set** de un recurso intenta forzar que el nodo sea compatible con el *estado deseado* del recurso.</span><span class="sxs-lookup"><span data-stu-id="19d99-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="19d99-138">El método **Set** está pensado para ser **idempotente**, lo que significa que **Set** podría ejecutarse varias veces y siempre obtendría el mismo resultado sin errores.</span><span class="sxs-lookup"><span data-stu-id="19d99-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="19d99-139">Cuando se ejecuta [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), el LCM pasa en ciclo por cada recurso en la configuración aplicada actualmente.</span><span class="sxs-lookup"><span data-stu-id="19d99-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="19d99-140">El LCM recupera los valores de clave para la instancia actual del recurso del archivo ".mof" y los usa como parámetros para el método **Test**.</span><span class="sxs-lookup"><span data-stu-id="19d99-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="19d99-141">Si el método **Test** devuelve `$True`, el nodo es compatible con el recurso actual y se omite el método **Set**.</span><span class="sxs-lookup"><span data-stu-id="19d99-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="19d99-142">Si **Test** devuelve `$False`, el nodo no es compatible.</span><span class="sxs-lookup"><span data-stu-id="19d99-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="19d99-143">El LCM pasa los valores de la clave de la instancia del recurso como parámetros para el método **Set** del recurso, restaurando la compatibilidad del nodo.</span><span class="sxs-lookup"><span data-stu-id="19d99-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="19d99-144">Al especificar los parámetros `-Verbose` y `-Wait`, puede observar el progreso del cmdlet `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="19d99-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="19d99-145">En este ejemplo, el nodo ya es compatible.</span><span class="sxs-lookup"><span data-stu-id="19d99-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="19d99-146">La salida `Verbose` indica que el método **Set** se omitió.</span><span class="sxs-lookup"><span data-stu-id="19d99-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="19d99-147">Vea también</span><span class="sxs-lookup"><span data-stu-id="19d99-147">See also</span></span>

- [<span data-ttu-id="19d99-148">Información general de DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="19d99-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="19d99-149">Configuración de un servidor de extracción SMB</span><span class="sxs-lookup"><span data-stu-id="19d99-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="19d99-150">Configuración de un cliente de extracción</span><span class="sxs-lookup"><span data-stu-id="19d99-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
