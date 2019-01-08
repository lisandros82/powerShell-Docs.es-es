---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Script con las ediciones compatibles de PowerShell
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655283"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="fd21f-103">Script con las ediciones compatibles de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd21f-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="fd21f-104">A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.</span><span class="sxs-lookup"><span data-stu-id="fd21f-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="fd21f-105">Desktop Edition Basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y el escritorio de Windows.</span><span class="sxs-lookup"><span data-stu-id="fd21f-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="fd21f-106">**Core Edition:** Basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a versiones de PowerShell que se ejecutan en las ediciones de superficie reducida de Windows como Nano Server y Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="fd21f-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="fd21f-107">La edición de PowerShell que se está ejecutando se muestra en la propiedad PSEdition de $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="fd21f-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="fd21f-108">Los autores de scripts pueden impedir que se ejecute un script a menos que se ejecute en una edición compatible de PowerShell mediante el parámetro PSEdition en una instrucción `#requires`.</span><span class="sxs-lookup"><span data-stu-id="fd21f-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="fd21f-109">Los usuarios de la Galería de PowerShell pueden encontrar la lista de scripts compatibles en una edición específica de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd21f-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="fd21f-110">Se considera que los scripts que no tienen las etiquetas PSEdition_Desktop o PSEdition_Core funcionan correctamente en la edición de PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="fd21f-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="fd21f-111">Más detalles</span><span class="sxs-lookup"><span data-stu-id="fd21f-111">More details</span></span>

- [<span data-ttu-id="fd21f-112">Módulos con PSEditions</span><span class="sxs-lookup"><span data-stu-id="fd21f-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="fd21f-113">Compatibilidad con PSEditions en la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd21f-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)
