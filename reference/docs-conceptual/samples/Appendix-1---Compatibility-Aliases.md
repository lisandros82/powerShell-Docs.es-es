---
ms.date: 09/09/2019
keywords: powershell, cmdlet
title: Apéndice 1 Alias de compatibilidad
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "70848168"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="d0ff3-103">Apéndice 1: Alias de compatibilidad</span><span class="sxs-lookup"><span data-stu-id="d0ff3-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="d0ff3-104">PowerShell tiene varios alias que permiten a los usuarios de **UNIX** y **cmd.exe** utilizar comandos familiares.</span><span class="sxs-lookup"><span data-stu-id="d0ff3-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="d0ff3-105">Los comandos y sus alias y cmdlet de PowerShell relacionados se muestran en la siguiente tabla:</span><span class="sxs-lookup"><span data-stu-id="d0ff3-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="d0ff3-106">Comando cmd.exe</span><span class="sxs-lookup"><span data-stu-id="d0ff3-106">cmd.exe command</span></span>|<span data-ttu-id="d0ff3-107">Comando de UNIX</span><span class="sxs-lookup"><span data-stu-id="d0ff3-107">UNIX command</span></span>|<span data-ttu-id="d0ff3-108">Cmdlet de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0ff3-108">PowerShell cmdlet</span></span>|<span data-ttu-id="d0ff3-109">Alias de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0ff3-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="d0ff3-110">**cls**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-110">**cls**</span></span>|<span data-ttu-id="d0ff3-111">**clear**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-111">**clear**</span></span>|<span data-ttu-id="d0ff3-112">`Clear-Host` (función)</span><span class="sxs-lookup"><span data-stu-id="d0ff3-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="d0ff3-113">**copy**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-113">**copy**</span></span>|<span data-ttu-id="d0ff3-114">**cp**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="d0ff3-115">**dir**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-115">**dir**</span></span>|<span data-ttu-id="d0ff3-116">**ls**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="d0ff3-117">**type**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-117">**type**</span></span>|<span data-ttu-id="d0ff3-118">**cat**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="d0ff3-119">**move**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-119">**move**</span></span>|<span data-ttu-id="d0ff3-120">**mv**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="d0ff3-121">**md**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-121">**md**</span></span>|<span data-ttu-id="d0ff3-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="d0ff3-123">**pushd**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-123">**pushd**</span></span>|<span data-ttu-id="d0ff3-124">**pushd**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="d0ff3-125">**popd**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-125">**popd**</span></span>|<span data-ttu-id="d0ff3-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="d0ff3-127">**del**, **erase**, **rd**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="d0ff3-128">**rm**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="d0ff3-129">**ren**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-129">**ren**</span></span>|<span data-ttu-id="d0ff3-130">**mv**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="d0ff3-131">**cd**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-131">**cd**, **chdir**</span></span>|<span data-ttu-id="d0ff3-132">**cd**</span><span class="sxs-lookup"><span data-stu-id="d0ff3-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="d0ff3-133">Para buscar los alias de PowerShell, use el cmdlet [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias).</span><span class="sxs-lookup"><span data-stu-id="d0ff3-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="d0ff3-134">Para mostrar los alias de un cmdlet, use el parámetro **Definition** y especifique el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d0ff3-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="d0ff3-135">O bien, para buscar el nombre del cmdlet de un alias, use el parámetro **Name** y especifique el alias.</span><span class="sxs-lookup"><span data-stu-id="d0ff3-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
