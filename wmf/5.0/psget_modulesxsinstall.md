---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 69188738333a853a16e6ea68689ecba5dc632225
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="f5f0e-102">Compatibilidad de versiones en paralelo en PowerShell 5.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="f5f0e-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="f5f0e-103">Ahora se incluye compatibilidad de versiones de módulos en paralelo (SxS) en los cmdlets Install-Module, Update-Module y Publish-Module que se ejecutan en Windows PowerShell 5.0 o versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="f5f0e-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="f5f0e-104">Además, agregamos un parámetro -RequiredVersion al cmdlet Publish-Module para especificar la versión que se va a publicar.</span><span class="sxs-lookup"><span data-stu-id="f5f0e-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="f5f0e-105">El parámetro Path admite ahora la ruta de acceso base del módulo con la carpeta de la versión.</span><span class="sxs-lookup"><span data-stu-id="f5f0e-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="f5f0e-106">**Ejemplos de Install-Module:**</span><span class="sxs-lookup"><span data-stu-id="f5f0e-106">**Install-Module examples:**</span></span>
```powershell
PS C:\\windows\\system32&gt; Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
PS C:\\windows\\system32&gt; Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase
Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

PS C:\\windows\\system32&gt; Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
PS C:\\windows\\system32&gt; Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase
Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

PS C:\\windows\\system32&gt; Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Type       Repository           Description            
-------    ----                                ----       ----------           -----------            
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```

