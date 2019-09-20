---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Flujo de información
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147615"
---
# <a name="information-stream"></a><span data-ttu-id="d9036-103">Flujo de información</span><span class="sxs-lookup"><span data-stu-id="d9036-103">Information Stream</span></span>

<span data-ttu-id="d9036-104">PowerShell 5.0 agrega un nuevo flujo de **información** estructurado para transmitir datos estructurados entre un script y su host.</span><span class="sxs-lookup"><span data-stu-id="d9036-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="d9036-105">`Write-Host` también se actualizó para emitir su salida en el flujo de **información**, donde ahora se puede capturar o silenciar.</span><span class="sxs-lookup"><span data-stu-id="d9036-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="d9036-106">El nuevo cmdlet `Write-Information` usado con los parámetros comunes **InformationVariable** y **InformationAction** permiten más flexibilidad y funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="d9036-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="d9036-107">La función siguiente usa cmdlets que aprovechan el nuevo flujo de **información**.</span><span class="sxs-lookup"><span data-stu-id="d9036-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

<span data-ttu-id="d9036-108">En los ejemplos se muestran los resultados de la ejecución de esta función.</span><span class="sxs-lookup"><span data-stu-id="d9036-108">The following examples show the results of running this function.</span></span>

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

<span data-ttu-id="d9036-109">La variable `$r` ha capturado la información del proceso en la variable de script `$p`.</span><span class="sxs-lookup"><span data-stu-id="d9036-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="d9036-110">A diferencia del cmdlet `Write-Host`, usar el parámetro **InformationVariable** de `Write-Information` le permite capturar la salida en una variable.</span><span class="sxs-lookup"><span data-stu-id="d9036-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="d9036-111">Con la **etiqueta**, puede crear canales independientes para el mensaje enviado al flujo de **información**.</span><span class="sxs-lookup"><span data-stu-id="d9036-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

<span data-ttu-id="d9036-112">Cuando envía un mensaje al flujo de **información** con una etiqueta, ese mensaje no se muestra en la aplicación host, pero se puede recuperar con el nombre de la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="d9036-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="d9036-113">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d9036-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```