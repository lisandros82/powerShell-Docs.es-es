---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Aplicación, obtención y prueba de las configuraciones en un nodo
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402946"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="2ab47-103">Aplicación, obtención y prueba de las configuraciones en un nodo</span><span class="sxs-lookup"><span data-stu-id="2ab47-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="2ab47-104">Esta guía le mostrará cómo trabajar con las configuraciones en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="2ab47-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="2ab47-105">Esta guía se divide en los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="2ab47-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="2ab47-106">Aplicar una configuración</span><span class="sxs-lookup"><span data-stu-id="2ab47-106">Apply a Configuration</span></span>

<span data-ttu-id="2ab47-107">Para aplicar y administrar una configuración, es necesario generar un archivo "MOF".</span><span class="sxs-lookup"><span data-stu-id="2ab47-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="2ab47-108">El siguiente código representa una configuración simple que se usará en esta guía.</span><span class="sxs-lookup"><span data-stu-id="2ab47-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

<span data-ttu-id="2ab47-109">Compilación de esta configuración dará como resultado dos archivos "MOF".</span><span class="sxs-lookup"><span data-stu-id="2ab47-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="2ab47-110">Para aplicar una configuración, use el [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ab47-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="2ab47-111">El `-Path` parámetro especifica un directorio donde residen los archivos "MOF".</span><span class="sxs-lookup"><span data-stu-id="2ab47-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="2ab47-112">Si no hay ningún `-Computername` se especifica, `Start-DSCConfiguration` intentará aplicar cada configuración en el nombre del equipo especificado por el nombre del archivo '.mof' (\<computername\>.mof).</span><span class="sxs-lookup"><span data-stu-id="2ab47-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="2ab47-113">Especificar `-Verbose` a `Start-DSCConfiguration` para ver los resultados más detallados.</span><span class="sxs-lookup"><span data-stu-id="2ab47-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="2ab47-114">Si `-Wait` no se especifica, verá un trabajo que creó.</span><span class="sxs-lookup"><span data-stu-id="2ab47-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="2ab47-115">El trabajo creado tendrá una **ChildJob** para cada archivo de "MOF" procesados por `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="2ab47-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="2ab47-116">Si una configuración está tardando mucho tiempo y desea detenerlo, puede usar [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) para detener la aplicación en el nodo local.</span><span class="sxs-lookup"><span data-stu-id="2ab47-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="2ab47-117">Una vez que haya finalizado, puede ver el estado de los trabajos a través del objeto de trabajo devueltos por [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="2ab47-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="2ab47-118">Para ver el **detallado** de salida, utilice los siguientes comandos para ver el **detallado** secuencia para cada **ChildJob**.</span><span class="sxs-lookup"><span data-stu-id="2ab47-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="2ab47-119">Para obtener más información acerca de los trabajos de PowerShell, consulte [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="2ab47-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="2ab47-120">A partir de PowerShell 5.0, el `-UseExisting` parámetro se agregó a `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="2ab47-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="2ab47-121">Mediante la especificación de `-UseExisting`, indicar al cmdlet que use la configuración aplicada existente en lugar de uno especificado por el `-Path` parámetro.</span><span class="sxs-lookup"><span data-stu-id="2ab47-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="2ab47-122">Probar una configuración</span><span class="sxs-lookup"><span data-stu-id="2ab47-122">Test a Configuration</span></span>

<span data-ttu-id="2ab47-123">Puede probar una configuración aplicada actualmente mediante [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="2ab47-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="2ab47-124">`Test-DSCConfiguration` devolverá `True` si el nodo es compatible, y `False` si no lo está.</span><span class="sxs-lookup"><span data-stu-id="2ab47-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="2ab47-125">A partir de PowerShell 5.0, el `-Detailed` parámetro se ha agregado que devuelve un objeto con las colecciones de **ResourcesInDesiredState** y **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="2ab47-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="2ab47-126">A partir de PowerShell 5.0, puede probar una configuración sin aplicarlo.</span><span class="sxs-lookup"><span data-stu-id="2ab47-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="2ab47-127">El `-ReferenceConfiguration` parámetro acepta la ruta de acceso de un archivo de "MOF" para probar el nodo contra.</span><span class="sxs-lookup"><span data-stu-id="2ab47-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="2ab47-128">No **establecer** se realizan acciones en el nodo.</span><span class="sxs-lookup"><span data-stu-id="2ab47-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="2ab47-129">En PowerShell 4.0, hay soluciones alternativas para probar una configuración sin aplicarlo, pero no se tratan aquí.</span><span class="sxs-lookup"><span data-stu-id="2ab47-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="2ab47-130">Obtener los valores de configuración</span><span class="sxs-lookup"><span data-stu-id="2ab47-130">Get Configuration Values</span></span>

<span data-ttu-id="2ab47-131">El [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet devuelve los valores actuales de los recursos configurados en la configuración aplicada actualmente.</span><span class="sxs-lookup"><span data-stu-id="2ab47-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="2ab47-132">Resultados del ejemplo de nuestra configuración tendría un aspecto similar al siguiente si se aplicaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="2ab47-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a><span data-ttu-id="2ab47-133">Obtener estado de configuración</span><span class="sxs-lookup"><span data-stu-id="2ab47-133">Get Configuration Status</span></span>

<span data-ttu-id="2ab47-134">A partir de PowerShell 5.0 el [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet le permite ver el historial de las configuraciones aplicadas al nodo.</span><span class="sxs-lookup"><span data-stu-id="2ab47-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="2ab47-135">DSC de PowerShell realiza un seguimiento de los últimos valores de configuración de {{N}} aplicados en **Push** o **extraer** modo.</span><span class="sxs-lookup"><span data-stu-id="2ab47-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="2ab47-136">Esto incluye cualquier *coherencia* comprueba que el LCM la ejecuta.</span><span class="sxs-lookup"><span data-stu-id="2ab47-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="2ab47-137">De forma predeterminada, `Get-DSCConfigurationStatus` muestra solo la última entrada del historial.</span><span class="sxs-lookup"><span data-stu-id="2ab47-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="2ab47-138">Use el `-All` parámetro para ver todo el historial de estado de configuración.</span><span class="sxs-lookup"><span data-stu-id="2ab47-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="2ab47-139">Salida queda truncada por razones de brevedad.</span><span class="sxs-lookup"><span data-stu-id="2ab47-139">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a><span data-ttu-id="2ab47-140">Administrar documentos de configuración</span><span class="sxs-lookup"><span data-stu-id="2ab47-140">Manage Configuration Documents</span></span>

<span data-ttu-id="2ab47-141">El LCM administra la configuración del nodo al trabajar con **documentos de configuración**.</span><span class="sxs-lookup"><span data-stu-id="2ab47-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="2ab47-142">Estos archivos "MOF" residen en el directorio "C:\Windows\System32\Configuration".</span><span class="sxs-lookup"><span data-stu-id="2ab47-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="2ab47-143">A partir de PowerShell 5.0 el [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) le permite quitar los archivos "MOF" para detener las comprobaciones de coherencia futura o quitar una configuración que tiene errores cuando se aplica.</span><span class="sxs-lookup"><span data-stu-id="2ab47-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="2ab47-144">El `-Stage` parámetro le permite especificar qué archivo de "MOF" que desea quitar.</span><span class="sxs-lookup"><span data-stu-id="2ab47-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="2ab47-145">En PowerShell 4.0, todavía puede quitar estos archivos "MOF" directamente mediante [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="2ab47-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="2ab47-146">Las configuraciones de publicación</span><span class="sxs-lookup"><span data-stu-id="2ab47-146">Publish Configurations</span></span>

<span data-ttu-id="2ab47-147">A partir de PowerShell 5.0, el [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) se agregó el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ab47-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="2ab47-148">Este cmdlet permite publicar un archivo de "MOF" en equipos remotos, sin aplicarlo.</span><span class="sxs-lookup"><span data-stu-id="2ab47-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="2ab47-149">Vea también</span><span class="sxs-lookup"><span data-stu-id="2ab47-149">See also</span></span>

- [<span data-ttu-id="2ab47-150">Obtención, prueba y establecimiento</span><span class="sxs-lookup"><span data-stu-id="2ab47-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
