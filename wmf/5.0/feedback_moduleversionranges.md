---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225698"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="f8eb0-102">Compatibilidad de los módulos para la declaración de intervalos de versiones (1.\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="f8eb0-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="f8eb0-103">Combinado con **-MinimumVersion**, **-MaximumVersion** permite ahora al usuario obtener o importar el módulo dentro de un intervalo específico.</span><span class="sxs-lookup"><span data-stu-id="f8eb0-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="f8eb0-104">El parámetro también admite **.**\*.</span><span class="sxs-lookup"><span data-stu-id="f8eb0-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="f8eb0-105">El siguiente ejemplo muestra funciona:</span><span class="sxs-lookup"><span data-stu-id="f8eb0-105">The following example shows how it works:</span></span>

<span data-ttu-id="f8eb0-106">Ahora puede combinar **-MinimumVersion** y **-MaximumVersion** para importar un módulo dentro de un intervalo específico:</span><span class="sxs-lookup"><span data-stu-id="f8eb0-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
