---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Aplicación, obtención y prueba de las configuraciones en un nodo
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953842"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="38eb1-103">Aplicación, obtención y prueba de las configuraciones en un nodo</span><span class="sxs-lookup"><span data-stu-id="38eb1-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="38eb1-104">Esta guía le mostrará cómo trabajar con las configuraciones en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="38eb1-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="38eb1-105">Se divide en los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="38eb1-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="38eb1-106">Aplicación de una configuración</span><span class="sxs-lookup"><span data-stu-id="38eb1-106">Apply a Configuration</span></span>

<span data-ttu-id="38eb1-107">Para aplicar y administrar una configuración, es necesario generar un archivo ".mof".</span><span class="sxs-lookup"><span data-stu-id="38eb1-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="38eb1-108">El siguiente código representará una configuración simple que se usará en esta guía.</span><span class="sxs-lookup"><span data-stu-id="38eb1-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

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

<span data-ttu-id="38eb1-109">La compilación de esta configuración dará como resultado dos archivos ".mof".</span><span class="sxs-lookup"><span data-stu-id="38eb1-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="38eb1-110">Para aplicar una configuración, use el cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="38eb1-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="38eb1-111">El parámetro `-Path` especifica un directorio donde residen los archivos ".mof".</span><span class="sxs-lookup"><span data-stu-id="38eb1-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="38eb1-112">Si no se especifica `-Computername`, `Start-DSCConfiguration` intentará aplicar cada configuración al nombre de equipo especificado por el nombre del archivo ".mof" (\<nombredeequipo\>.mof).</span><span class="sxs-lookup"><span data-stu-id="38eb1-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="38eb1-113">Especifique `-Verbose` e `Start-DSCConfiguration` para ver una salida más detallada.</span><span class="sxs-lookup"><span data-stu-id="38eb1-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="38eb1-114">Si `-Wait` no se especifica, verá un trabajo creado.</span><span class="sxs-lookup"><span data-stu-id="38eb1-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="38eb1-115">El trabajo creado tendrá un **ChildJob** para cada archivo ".mof" procesado por `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="38eb1-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="38eb1-116">Si una configuración está tardando mucho tiempo y desea detenerla, puede usar [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) para detener la aplicación en el nodo local.</span><span class="sxs-lookup"><span data-stu-id="38eb1-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="38eb1-117">Una vez que haya finalizado, puede ver el estado de los trabajos a través del objeto de trabajo devuelto por [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="38eb1-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

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

<span data-ttu-id="38eb1-118">Para ver la salida de **Verbose**, use los siguientes comandos para ver la secuencia **Verbose** para cada **ChildJob**.</span><span class="sxs-lookup"><span data-stu-id="38eb1-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="38eb1-119">Para más información sobre los trabajos de PowerShell, vea [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs) (Acerca de los trabajos).</span><span class="sxs-lookup"><span data-stu-id="38eb1-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

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

<span data-ttu-id="38eb1-120">A partir de PowerShell 5.0, se agregó el parámetro `-UseExisting` a `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="38eb1-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="38eb1-121">Mediante la especificación de `-UseExisting`, indica al cmdlet que use la configuración aplicada existente en lugar de una especificada por el parámetro `-Path`.</span><span class="sxs-lookup"><span data-stu-id="38eb1-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="38eb1-122">Prueba de una configuración</span><span class="sxs-lookup"><span data-stu-id="38eb1-122">Test a Configuration</span></span>

<span data-ttu-id="38eb1-123">Puede probar una configuración aplicada actualmente mediante [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="38eb1-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="38eb1-124">`Test-DSCConfiguration` devolverá `True` si el nodo es compatible, y `False` si no lo es.</span><span class="sxs-lookup"><span data-stu-id="38eb1-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="38eb1-125">A partir de PowerShell 5.0, se ha agregado el parámetro `-Detailed`, que devuelve un objeto con las colecciones de **ResourcesInDesiredState** y **ResourcesNotInDesiredState**.</span><span class="sxs-lookup"><span data-stu-id="38eb1-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="38eb1-126">A partir de PowerShell 5.0, puede probar una configuración sin aplicarla.</span><span class="sxs-lookup"><span data-stu-id="38eb1-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="38eb1-127">El parámetro `-ReferenceConfiguration` acepta la ruta de acceso de un archivo ".mof" en la que probar el nodo.</span><span class="sxs-lookup"><span data-stu-id="38eb1-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="38eb1-128">No se realizan acciones **Set** en el nodo.</span><span class="sxs-lookup"><span data-stu-id="38eb1-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="38eb1-129">En PowerShell 4.0, hay soluciones alternativas para probar una configuración sin aplicarla, pero no se tratan aquí.</span><span class="sxs-lookup"><span data-stu-id="38eb1-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="38eb1-130">Obtención de valores de configuración</span><span class="sxs-lookup"><span data-stu-id="38eb1-130">Get Configuration Values</span></span>

<span data-ttu-id="38eb1-131">El cmdlet [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) devuelve los valores actuales de los recursos configurados en la configuración aplicada actualmente.</span><span class="sxs-lookup"><span data-stu-id="38eb1-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="38eb1-132">Los resultados de ejemplo de nuestra configuración tendrían un aspecto similar al siguiente si se aplicaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="38eb1-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

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

## <a name="get-configuration-status"></a><span data-ttu-id="38eb1-133">Obtención de estado de configuración</span><span class="sxs-lookup"><span data-stu-id="38eb1-133">Get Configuration Status</span></span>

<span data-ttu-id="38eb1-134">A partir de PowerShell 5.0, el cmdlet [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) le permite ver el historial de las configuraciones aplicadas al nodo.</span><span class="sxs-lookup"><span data-stu-id="38eb1-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="38eb1-135">DSC de PowerShell realiza un seguimiento de los últimos {{N}} valores de configuración aplicados en modo de **inserción** o **extracción**.</span><span class="sxs-lookup"><span data-stu-id="38eb1-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="38eb1-136">Esto incluye las comprobaciones de *coherencia* ejecutadas por el LCM.</span><span class="sxs-lookup"><span data-stu-id="38eb1-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="38eb1-137">De forma predeterminada, `Get-DSCConfigurationStatus` muestra solo la última entrada del historial.</span><span class="sxs-lookup"><span data-stu-id="38eb1-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="38eb1-138">Use el parámetro `-All` para ver todo el historial del estado de configuración.</span><span class="sxs-lookup"><span data-stu-id="38eb1-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="38eb1-139">La salida se trunca por razones de brevedad.</span><span class="sxs-lookup"><span data-stu-id="38eb1-139">Output is truncated for brevity.</span></span>

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

## <a name="manage-configuration-documents"></a><span data-ttu-id="38eb1-140">Administración de documentos de configuración</span><span class="sxs-lookup"><span data-stu-id="38eb1-140">Manage Configuration Documents</span></span>

<span data-ttu-id="38eb1-141">El LCM administra la configuración del nodo al trabajar con **documentos de configuración**.</span><span class="sxs-lookup"><span data-stu-id="38eb1-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="38eb1-142">Estos archivos ".mof" residen en el directorio "C:\Windows\System32\Configuration".</span><span class="sxs-lookup"><span data-stu-id="38eb1-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="38eb1-143">A partir de PowerShell 5.0, [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) le permite quitar los archivos ".mof" para detener las futuras comprobaciones de coherencia o quitar una configuración que tiene errores cuando se aplica.</span><span class="sxs-lookup"><span data-stu-id="38eb1-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="38eb1-144">El parámetro `-Stage` le permite especificar qué archivo ".mof" desea quitar.</span><span class="sxs-lookup"><span data-stu-id="38eb1-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="38eb1-145">En PowerShell 4.0, todavía puede quitar estos archivos ".mof" directamente mediante [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="38eb1-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="38eb1-146">Publicación de configuraciones</span><span class="sxs-lookup"><span data-stu-id="38eb1-146">Publish Configurations</span></span>

<span data-ttu-id="38eb1-147">A partir de PowerShell 5.0, se agregó el cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="38eb1-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="38eb1-148">Este cmdlet permite publicar un archivo ".mof" en equipos remotos, sin aplicarlo.</span><span class="sxs-lookup"><span data-stu-id="38eb1-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="38eb1-149">Vea también</span><span class="sxs-lookup"><span data-stu-id="38eb1-149">See also</span></span>

- [<span data-ttu-id="38eb1-150">Obtención, prueba y establecimiento</span><span class="sxs-lookup"><span data-stu-id="38eb1-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
