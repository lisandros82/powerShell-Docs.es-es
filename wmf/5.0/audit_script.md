---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: b440ea4a8208d5c576fa566a19e2de377bf5f475
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="a37db-102">Seguimiento y registro de scripts</span><span class="sxs-lookup"><span data-stu-id="a37db-102">Script Tracing and Logging</span></span>

<span data-ttu-id="a37db-103">Mientras que Windows PowerShell ya tiene la opción de Directiva de grupo **LogPipelineExecutionDetails** para registrar la invocación de cmdlets, el lenguaje de scripting de PowerShell tiene muchas características que quizás quiera registrar y/o auditar.</span><span class="sxs-lookup"><span data-stu-id="a37db-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="a37db-104">La nueva característica de seguimiento detallado de scripts permite habilitar el seguimiento detallado y el análisis del uso de scripting de Windows PowerShell en un sistema.</span><span class="sxs-lookup"><span data-stu-id="a37db-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="a37db-105">Después de habilitar el seguimiento detallado de scripts, Windows PowerShell registra todos los bloques de script en el registro de eventos ETW, **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="a37db-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="a37db-106">Si un bloque de script crea otro bloque de script (por ejemplo, un script que llame al cmdlet Invoke-Expression en una cadena), también se registra este bloque de script resultante.</span><span class="sxs-lookup"><span data-stu-id="a37db-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="a37db-107">El registro de estos eventos se puede habilitar a través de la opción de Directiva de grupo **Activar el registro de bloque de script de PowerShell** (en Plantillas administrativas -> Componentes de Windows -> Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="a37db-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="a37db-108">Los eventos son:</span><span class="sxs-lookup"><span data-stu-id="a37db-108">The events are:</span></span>

| <span data-ttu-id="a37db-109">Canal</span><span class="sxs-lookup"><span data-stu-id="a37db-109">Channel</span></span> | <span data-ttu-id="a37db-110">Operativo</span><span class="sxs-lookup"><span data-stu-id="a37db-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="a37db-111">Nivel</span><span class="sxs-lookup"><span data-stu-id="a37db-111">Level</span></span>   | <span data-ttu-id="a37db-112">Verbose</span><span class="sxs-lookup"><span data-stu-id="a37db-112">Verbose</span></span>                                     |
| <span data-ttu-id="a37db-113">Código de operación</span><span class="sxs-lookup"><span data-stu-id="a37db-113">Opcode</span></span>  | <span data-ttu-id="a37db-114">Crear</span><span class="sxs-lookup"><span data-stu-id="a37db-114">Create</span></span>                                      |
| <span data-ttu-id="a37db-115">Tarea</span><span class="sxs-lookup"><span data-stu-id="a37db-115">Task</span></span>    | <span data-ttu-id="a37db-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="a37db-116">CommandStart</span></span>                                |
| <span data-ttu-id="a37db-117">Palabra clave</span><span class="sxs-lookup"><span data-stu-id="a37db-117">Keyword</span></span> | <span data-ttu-id="a37db-118">Espacio de ejecución</span><span class="sxs-lookup"><span data-stu-id="a37db-118">Runspace</span></span>                                    |
| <span data-ttu-id="a37db-119">Id. de evento</span><span class="sxs-lookup"><span data-stu-id="a37db-119">EventId</span></span> | <span data-ttu-id="a37db-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="a37db-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="a37db-121">Mensaje</span><span class="sxs-lookup"><span data-stu-id="a37db-121">Message</span></span> | <span data-ttu-id="a37db-122">Creando texto de bloque de script (%1 de %2):</span><span class="sxs-lookup"><span data-stu-id="a37db-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="a37db-123">%3</span><span class="sxs-lookup"><span data-stu-id="a37db-123">%3</span></span> </br> <span data-ttu-id="a37db-124">Id. de bloque de script: %4</span><span class="sxs-lookup"><span data-stu-id="a37db-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="a37db-125">El texto insertado en el mensaje es la extensión del bloque de script compilado.</span><span class="sxs-lookup"><span data-stu-id="a37db-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="a37db-126">El identificador es un GUID que se conserva durante la vida del bloque de script.</span><span class="sxs-lookup"><span data-stu-id="a37db-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="a37db-127">Cuando se habilita el registro detallado, la característica escribe los marcadores de inicio y fin:</span><span class="sxs-lookup"><span data-stu-id="a37db-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="a37db-128">Canal</span><span class="sxs-lookup"><span data-stu-id="a37db-128">Channel</span></span> | <span data-ttu-id="a37db-129">Operativo</span><span class="sxs-lookup"><span data-stu-id="a37db-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="a37db-130">Nivel</span><span class="sxs-lookup"><span data-stu-id="a37db-130">Level</span></span>   | <span data-ttu-id="a37db-131">Verbose</span><span class="sxs-lookup"><span data-stu-id="a37db-131">Verbose</span></span>                                                |
| <span data-ttu-id="a37db-132">Código de operación</span><span class="sxs-lookup"><span data-stu-id="a37db-132">Opcode</span></span>  | <span data-ttu-id="a37db-133">Abrir (/Cerrar)</span><span class="sxs-lookup"><span data-stu-id="a37db-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="a37db-134">Tarea</span><span class="sxs-lookup"><span data-stu-id="a37db-134">Task</span></span>    | <span data-ttu-id="a37db-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="a37db-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="a37db-136">Palabra clave</span><span class="sxs-lookup"><span data-stu-id="a37db-136">Keyword</span></span> | <span data-ttu-id="a37db-137">Espacio de ejecución</span><span class="sxs-lookup"><span data-stu-id="a37db-137">Runspace</span></span>                                               |
| <span data-ttu-id="a37db-138">Id. de evento</span><span class="sxs-lookup"><span data-stu-id="a37db-138">EventId</span></span> | <span data-ttu-id="a37db-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="a37db-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="a37db-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="a37db-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="a37db-141">Mensaje</span><span class="sxs-lookup"><span data-stu-id="a37db-141">Message</span></span> | <span data-ttu-id="a37db-142">Invocación iniciada (/completada) del id. de bloque de script: %1</span><span class="sxs-lookup"><span data-stu-id="a37db-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="a37db-143">Id. de espacio de ejecución: %2</span><span class="sxs-lookup"><span data-stu-id="a37db-143">Runspace ID: %2</span></span> |

<span data-ttu-id="a37db-144">El identificador es el GUID que representa el bloque de script (que puede estar correlacionado con Id. de evento 0x1008) y el identificador de espacio de ejecución representa el espacio de ejecución en el que se ejecutó este bloque de script.</span><span class="sxs-lookup"><span data-stu-id="a37db-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="a37db-145">Los signos de porcentaje del mensaje de invocación representan las propiedades de ETW estructuradas.</span><span class="sxs-lookup"><span data-stu-id="a37db-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="a37db-146">Mientras se reemplazan por los valores reales en el texto del mensaje, una manera más segura de acceder a ellos es recuperar el mensaje con el cmdlet Get-WinEvent y, luego, usara la matriz **Properties** del mensaje.</span><span class="sxs-lookup"><span data-stu-id="a37db-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="a37db-147">Este es un ejemplo de cómo esta funcionalidad puede ayudarle a descubrir un intento malicioso para cifrar y ofuscar un script:</span><span class="sxs-lookup"><span data-stu-id="a37db-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
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

<span data-ttu-id="a37db-148">Si se ejecuta, generará las entradas de registro siguientes:</span><span class="sxs-lookup"><span data-stu-id="a37db-148">Running this generates the following log entries:</span></span>

```
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

Si la longitud del bloque de script supera la que ETW es capaz de contener en un único evento, Windows PowerShell divide el script en varias partes. <span data-ttu-id="a37db-150">A continuación, se muestra código de ejemplo para volver a combinar un script a partir de sus mensajes de registro:</span><span class="sxs-lookup"><span data-stu-id="a37db-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="a37db-151">Al igual que con todos los sistemas de registro que tienen un búfer de retención limitado (es decir, registros de ETW), un ataque contra esta infraestructura es inundar el registro de eventos falsos para ocultar las pruebas anteriores.</span><span class="sxs-lookup"><span data-stu-id="a37db-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="a37db-152">Para protegerse de este ataque, asegúrese de que tiene algún tipo de colección de registro de eventos configurado (es decir, Colección de reenvío de eventos de Windows, [Spotting the Adversary with Windows Event Log Monitoring](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) para desplazar los registros de eventos del equipo tan pronto como sea posible.</span><span class="sxs-lookup"><span data-stu-id="a37db-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) to move event logs off of the computer as soon as possible.</span></span>