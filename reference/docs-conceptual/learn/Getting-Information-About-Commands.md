---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Obtener información sobre los comandos
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057713"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="5d767-103">Obtener información sobre los comandos</span><span class="sxs-lookup"><span data-stu-id="5d767-103">Getting information about commands</span></span>

<span data-ttu-id="5d767-104">El `Get-Command` de PowerShell muestra los comandos que están disponibles en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="5d767-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="5d767-105">Cuando ejecute el cmdlet `Get-Command`, verá algo similar a la siguiente salida:</span><span class="sxs-lookup"><span data-stu-id="5d767-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

<span data-ttu-id="5d767-106">Esta salida se parece mucho a la salida de la Ayuda de **cmd.exe**: es un resumen tabular de comandos internos.</span><span class="sxs-lookup"><span data-stu-id="5d767-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="5d767-107">En el extracto de la salida del comando `Get-Command` mostrado anteriormente, cada comando muestra una sección CommandType de Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5d767-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="5d767-108">Un cmdlet es el tipo de comando intrínseco de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d767-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="5d767-109">Este tipo corresponde aproximadamente a comandos como `dir` y `cd` en **cmd.exe** o a los comandos integrados de shells Unix como bash.</span><span class="sxs-lookup"><span data-stu-id="5d767-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="5d767-110">El cmdlet `Get-Command` tiene un parámetro **Syntax** que devuelve la sintaxis de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5d767-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="5d767-111">El siguiente ejemplo muestra cómo obtener la sintaxis del cmdlet `Get-Help`:</span><span class="sxs-lookup"><span data-stu-id="5d767-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="5d767-112">Visualización de los comandos disponibles por tipo</span><span class="sxs-lookup"><span data-stu-id="5d767-112">Displaying available command by type</span></span>

<span data-ttu-id="5d767-113">El comando `Get-Command` enumera únicamente los cmdlets de la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="5d767-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="5d767-114">En realidad, PowerShell admite otros muchos tipos de comandos:</span><span class="sxs-lookup"><span data-stu-id="5d767-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="5d767-115">Alias</span><span class="sxs-lookup"><span data-stu-id="5d767-115">Aliases</span></span>
- <span data-ttu-id="5d767-116">Funciones</span><span class="sxs-lookup"><span data-stu-id="5d767-116">Functions</span></span>
- <span data-ttu-id="5d767-117">Scripts</span><span class="sxs-lookup"><span data-stu-id="5d767-117">Scripts</span></span>

<span data-ttu-id="5d767-118">Los archivos externos ejecutables o los que tienen un controlador de tipo de archivo registrado también se clasifican como comandos.</span><span class="sxs-lookup"><span data-stu-id="5d767-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="5d767-119">Para obtener todos los comandos de la sesión, escriba:</span><span class="sxs-lookup"><span data-stu-id="5d767-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="5d767-120">Esta lista incluye los comandos externos de su ruta de búsqueda, para que pueda contener miles de elementos.</span><span class="sxs-lookup"><span data-stu-id="5d767-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="5d767-121">Es más útil buscar en un conjunto reducido de comandos.</span><span class="sxs-lookup"><span data-stu-id="5d767-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="5d767-122">El asterisco (\*) sirve de comodín para hallar coincidencias en los argumentos de comando de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d767-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="5d767-123">El carácter \* quiere decir "coincide con uno o varios caracteres".</span><span class="sxs-lookup"><span data-stu-id="5d767-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="5d767-124">Así, puede escribir `Get-Command a*` para encontrar todos los comandos que comienzan por la letra "a".</span><span class="sxs-lookup"><span data-stu-id="5d767-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="5d767-125">A diferencia de las búsquedas con comodín en **cmd.exe**, los comodines de PowerShell también encontrarán coincidencias de período.</span><span class="sxs-lookup"><span data-stu-id="5d767-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="5d767-126">Use el parámetro **CommandType** de `Get-Command` para obtener los comandos nativos de otros tipos.</span><span class="sxs-lookup"><span data-stu-id="5d767-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="5d767-127">cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5d767-127">cmdlet.</span></span>

<span data-ttu-id="5d767-128">Para obtener los alias de comandos (que son los sobrenombres asignados de los comandos), escriba:</span><span class="sxs-lookup"><span data-stu-id="5d767-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="5d767-129">Para obtener las funciones en la sesión actual, escriba:</span><span class="sxs-lookup"><span data-stu-id="5d767-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="5d767-130">Para mostrar los scripts en la ruta de búsqueda de PowerShell, escriba:</span><span class="sxs-lookup"><span data-stu-id="5d767-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```