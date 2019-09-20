---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Seguimiento y registro de scripts
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147805"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="061cd-103">Seguimiento y registro de scripts</span><span class="sxs-lookup"><span data-stu-id="061cd-103">Script Tracing and Logging</span></span>

<span data-ttu-id="061cd-104">Mientras que PowerShell ya tiene la opción de Directiva de grupo **LogPipelineExecutionDetails** para registrar la invocación de cmdlets, el lenguaje de scripting de PowerShell tiene muchas características que quizás quiera registrar y auditar.</span><span class="sxs-lookup"><span data-stu-id="061cd-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="061cd-105">La nueva característica de seguimiento detallado de scripts ofrece el seguimiento detallado y el análisis de la actividad de los scripts de PowerShell en un sistema.</span><span class="sxs-lookup"><span data-stu-id="061cd-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="061cd-106">Después de habilitar el seguimiento detallado de scripts, PowerShell registra todos los bloques de script en el registro de eventos ETW, **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="061cd-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="061cd-107">Si un bloque de script crea otro bloque de script, por ejemplo, al llamar a `Invoke-Expression`, también se registrará el bloque de script al que se invocó.</span><span class="sxs-lookup"><span data-stu-id="061cd-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="061cd-108">El registro se habilita a través de la opción de Directiva de grupo **Activar el registro de bloque de script de PowerShell** en **Plantillas administrativas** -> **Componentes de Windows** -> **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="061cd-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="061cd-109">Los eventos son:</span><span class="sxs-lookup"><span data-stu-id="061cd-109">The events are:</span></span>

| <span data-ttu-id="061cd-110">Canal</span><span class="sxs-lookup"><span data-stu-id="061cd-110">Channel</span></span> |                               <span data-ttu-id="061cd-111">Operativo</span><span class="sxs-lookup"><span data-stu-id="061cd-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="061cd-112">Nivel</span><span class="sxs-lookup"><span data-stu-id="061cd-112">Level</span></span>   | <span data-ttu-id="061cd-113">Verbose</span><span class="sxs-lookup"><span data-stu-id="061cd-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="061cd-114">Código de operación</span><span class="sxs-lookup"><span data-stu-id="061cd-114">Opcode</span></span>  | <span data-ttu-id="061cd-115">Crear</span><span class="sxs-lookup"><span data-stu-id="061cd-115">Create</span></span>                                                                  |
| <span data-ttu-id="061cd-116">Tarea</span><span class="sxs-lookup"><span data-stu-id="061cd-116">Task</span></span>    | <span data-ttu-id="061cd-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="061cd-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="061cd-118">Palabra clave</span><span class="sxs-lookup"><span data-stu-id="061cd-118">Keyword</span></span> | <span data-ttu-id="061cd-119">Espacio de ejecución</span><span class="sxs-lookup"><span data-stu-id="061cd-119">Runspace</span></span>                                                                |
| <span data-ttu-id="061cd-120">Id. de evento</span><span class="sxs-lookup"><span data-stu-id="061cd-120">EventId</span></span> | <span data-ttu-id="061cd-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="061cd-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="061cd-122">Mensaje</span><span class="sxs-lookup"><span data-stu-id="061cd-122">Message</span></span> | <span data-ttu-id="061cd-123">Creando texto de bloque de script (%1 de %2):</span><span class="sxs-lookup"><span data-stu-id="061cd-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="061cd-124">%3</span><span class="sxs-lookup"><span data-stu-id="061cd-124">%3</span></span> </br> <span data-ttu-id="061cd-125">Id. de bloque de script: %4</span><span class="sxs-lookup"><span data-stu-id="061cd-125">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="061cd-126">El texto insertado en el mensaje es la extensión del bloque de script compilado.</span><span class="sxs-lookup"><span data-stu-id="061cd-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="061cd-127">El identificador es un GUID que se conserva durante la vida del bloque de script.</span><span class="sxs-lookup"><span data-stu-id="061cd-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="061cd-128">Cuando se habilita el registro detallado, la característica escribe los marcadores de inicio y fin:</span><span class="sxs-lookup"><span data-stu-id="061cd-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="061cd-129">Canal</span><span class="sxs-lookup"><span data-stu-id="061cd-129">Channel</span></span> |                                 <span data-ttu-id="061cd-130">Operativo</span><span class="sxs-lookup"><span data-stu-id="061cd-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="061cd-131">Nivel</span><span class="sxs-lookup"><span data-stu-id="061cd-131">Level</span></span>   | <span data-ttu-id="061cd-132">Verbose</span><span class="sxs-lookup"><span data-stu-id="061cd-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="061cd-133">Código de operación</span><span class="sxs-lookup"><span data-stu-id="061cd-133">Opcode</span></span>  | <span data-ttu-id="061cd-134">Abrir / Cerrar</span><span class="sxs-lookup"><span data-stu-id="061cd-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="061cd-135">Tarea</span><span class="sxs-lookup"><span data-stu-id="061cd-135">Task</span></span>    | <span data-ttu-id="061cd-136">CommandStart / CommandStop</span><span class="sxs-lookup"><span data-stu-id="061cd-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="061cd-137">Palabra clave</span><span class="sxs-lookup"><span data-stu-id="061cd-137">Keyword</span></span> | <span data-ttu-id="061cd-138">Espacio de ejecución</span><span class="sxs-lookup"><span data-stu-id="061cd-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="061cd-139">Id. de evento</span><span class="sxs-lookup"><span data-stu-id="061cd-139">EventId</span></span> | <span data-ttu-id="061cd-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="061cd-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="061cd-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="061cd-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="061cd-142">Mensaje</span><span class="sxs-lookup"><span data-stu-id="061cd-142">Message</span></span> | <span data-ttu-id="061cd-143">Invocación iniciada / completada del id. de bloque de script: %1</span><span class="sxs-lookup"><span data-stu-id="061cd-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="061cd-144">Id. de espacio de ejecución: %2</span><span class="sxs-lookup"><span data-stu-id="061cd-144">Runspace ID: %2</span></span> |

<span data-ttu-id="061cd-145">El identificador es el GUID que representa el bloque de script (que puede estar correlacionado con Id. de evento 0x1008) y el identificador de espacio de ejecución representa el espacio de ejecución en el que se ejecutó este bloque de script.</span><span class="sxs-lookup"><span data-stu-id="061cd-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="061cd-146">Los signos de porcentaje del mensaje de invocación representan las propiedades de ETW estructuradas.</span><span class="sxs-lookup"><span data-stu-id="061cd-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="061cd-147">Mientras se reemplazan por los valores reales en el texto del mensaje, una manera más segura de acceder a ellos es recuperar el mensaje con el cmdlet Get-WinEvent y, luego, usara la matriz **Properties** del mensaje.</span><span class="sxs-lookup"><span data-stu-id="061cd-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="061cd-148">Este es un ejemplo de cómo esta funcionalidad puede ayudarle a descubrir un intento malicioso para cifrar y ofuscar un script:</span><span class="sxs-lookup"><span data-stu-id="061cd-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="061cd-149">Si se ejecuta, generará las entradas de registro siguientes:</span><span class="sxs-lookup"><span data-stu-id="061cd-149">Running this generates the following log entries:</span></span>

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Si la longitud del bloque de script supera la capacidad de un solo evento, PowerShell divide el script en varias partes. <span data-ttu-id="061cd-151">A continuación, se muestra código de ejemplo para volver a combinar un script a partir de sus mensajes de registro:</span><span class="sxs-lookup"><span data-stu-id="061cd-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="061cd-152">Al igual que con todos los sistemas de registro que tienen un búfer de retención limitado, una forma de atacar esta infraestructura es inundar el registro de eventos falsos para ocultar las pruebas anteriores.</span><span class="sxs-lookup"><span data-stu-id="061cd-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="061cd-153">Para protegerse de este ataque, asegúrese de tener configurado algún tipo de colección de registros de eventos, como Reenvío de eventos de Windows.</span><span class="sxs-lookup"><span data-stu-id="061cd-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="061cd-154">Para más información, consulte [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span><span class="sxs-lookup"><span data-stu-id="061cd-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>