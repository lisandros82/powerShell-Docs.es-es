---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057518"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="0f038-102">Compatibilidad de los módulos para la declaración de intervalos de versiones (1.\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="0f038-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="0f038-103">Combinado con **-MinimumVersion**, **-MaximumVersion** permite ahora al usuario obtener o importar el módulo dentro de un intervalo específico.</span><span class="sxs-lookup"><span data-stu-id="0f038-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="0f038-104">El parámetro también admite **.**\*.</span><span class="sxs-lookup"><span data-stu-id="0f038-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="0f038-105">El siguiente ejemplo muestra funciona:</span><span class="sxs-lookup"><span data-stu-id="0f038-105">The following example shows how it works:</span></span>

<span data-ttu-id="0f038-106">Ahora puede combinar **-MinimumVersion** y **-MaximumVersion** para importar un módulo dentro de un intervalo específico:</span><span class="sxs-lookup"><span data-stu-id="0f038-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
