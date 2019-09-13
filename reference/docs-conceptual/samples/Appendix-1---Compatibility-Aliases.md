---
ms.date: 09/09/2019
keywords: powershell, cmdlet
title: Apéndice 1 Alias de compatibilidad
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848168"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="9bd17-103">Apéndice 1: Alias de compatibilidad</span><span class="sxs-lookup"><span data-stu-id="9bd17-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="9bd17-104">PowerShell tiene varios alias que permiten a los usuarios de **UNIX** y **cmd.exe** utilizar comandos familiares.</span><span class="sxs-lookup"><span data-stu-id="9bd17-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="9bd17-105">Los comandos y sus alias y cmdlet de PowerShell relacionados se muestran en la siguiente tabla:</span><span class="sxs-lookup"><span data-stu-id="9bd17-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="9bd17-106">Comando cmd.exe</span><span class="sxs-lookup"><span data-stu-id="9bd17-106">cmd.exe command</span></span>|<span data-ttu-id="9bd17-107">Comando de UNIX</span><span class="sxs-lookup"><span data-stu-id="9bd17-107">UNIX command</span></span>|<span data-ttu-id="9bd17-108">Cmdlet de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bd17-108">PowerShell cmdlet</span></span>|<span data-ttu-id="9bd17-109">Alias de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bd17-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="9bd17-110">**cls**</span><span class="sxs-lookup"><span data-stu-id="9bd17-110">**cls**</span></span>|<span data-ttu-id="9bd17-111">**clear**</span><span class="sxs-lookup"><span data-stu-id="9bd17-111">**clear**</span></span>|<span data-ttu-id="9bd17-112">`Clear-Host` (función)</span><span class="sxs-lookup"><span data-stu-id="9bd17-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="9bd17-113">**copy**</span><span class="sxs-lookup"><span data-stu-id="9bd17-113">**copy**</span></span>|<span data-ttu-id="9bd17-114">**cp**</span><span class="sxs-lookup"><span data-stu-id="9bd17-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="9bd17-115">**dir**</span><span class="sxs-lookup"><span data-stu-id="9bd17-115">**dir**</span></span>|<span data-ttu-id="9bd17-116">**ls**</span><span class="sxs-lookup"><span data-stu-id="9bd17-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="9bd17-117">**type**</span><span class="sxs-lookup"><span data-stu-id="9bd17-117">**type**</span></span>|<span data-ttu-id="9bd17-118">**cat**</span><span class="sxs-lookup"><span data-stu-id="9bd17-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="9bd17-119">**move**</span><span class="sxs-lookup"><span data-stu-id="9bd17-119">**move**</span></span>|<span data-ttu-id="9bd17-120">**mv**</span><span class="sxs-lookup"><span data-stu-id="9bd17-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="9bd17-121">**md**</span><span class="sxs-lookup"><span data-stu-id="9bd17-121">**md**</span></span>|<span data-ttu-id="9bd17-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="9bd17-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="9bd17-123">**pushd**</span><span class="sxs-lookup"><span data-stu-id="9bd17-123">**pushd**</span></span>|<span data-ttu-id="9bd17-124">**pushd**</span><span class="sxs-lookup"><span data-stu-id="9bd17-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="9bd17-125">**popd**</span><span class="sxs-lookup"><span data-stu-id="9bd17-125">**popd**</span></span>|<span data-ttu-id="9bd17-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="9bd17-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="9bd17-127">**del**, **erase**, **rd**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="9bd17-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="9bd17-128">**rm**</span><span class="sxs-lookup"><span data-stu-id="9bd17-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="9bd17-129">**ren**</span><span class="sxs-lookup"><span data-stu-id="9bd17-129">**ren**</span></span>|<span data-ttu-id="9bd17-130">**mv**</span><span class="sxs-lookup"><span data-stu-id="9bd17-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="9bd17-131">**cd**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="9bd17-131">**cd**, **chdir**</span></span>|<span data-ttu-id="9bd17-132">**cd**</span><span class="sxs-lookup"><span data-stu-id="9bd17-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="9bd17-133">Para buscar los alias de PowerShell, use el cmdlet [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias).</span><span class="sxs-lookup"><span data-stu-id="9bd17-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="9bd17-134">Para mostrar los alias de un cmdlet, use el parámetro **Definition** y especifique el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9bd17-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="9bd17-135">O bien, para buscar el nombre del cmdlet de un alias, use el parámetro **Name** y especifique el alias.</span><span class="sxs-lookup"><span data-stu-id="9bd17-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
