---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Script con las ediciones compatibles de PowerShell
ms.openlocfilehash: 2313131fe17dcd9508db514883ae3dcb837fb07e
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587217"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="8e5eb-103">Script con las ediciones compatibles de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e5eb-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="8e5eb-104">A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.</span><span class="sxs-lookup"><span data-stu-id="8e5eb-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="8e5eb-105">**Desktop Edition:** basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="8e5eb-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="8e5eb-106">**Core Edition:** basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Nano Server y Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="8e5eb-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="8e5eb-107">La edición de PowerShell que se está ejecutando se muestra en la propiedad PSEdition de $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="8e5eb-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

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

<span data-ttu-id="8e5eb-108">Los autores de scripts pueden impedir que se ejecute un script a menos que se ejecute en una edición compatible de PowerShell mediante el parámetro PSEdition en una instrucción `#requires`.</span><span class="sxs-lookup"><span data-stu-id="8e5eb-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

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

<span data-ttu-id="8e5eb-109">Los usuarios de la Galería de PowerShell pueden encontrar la lista de scripts compatibles en una edición específica de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e5eb-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="8e5eb-110">Se considera que los scripts que no tienen las etiquetas PSEdition_Desktop o PSEdition_Core funcionan correctamente en la edición de PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="8e5eb-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="8e5eb-111">Más detalles</span><span class="sxs-lookup"><span data-stu-id="8e5eb-111">More details</span></span>

- [<span data-ttu-id="8e5eb-112">Módulos con PSEditions</span><span class="sxs-lookup"><span data-stu-id="8e5eb-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="8e5eb-113">Compatibilidad con PSEditions en la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e5eb-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)
