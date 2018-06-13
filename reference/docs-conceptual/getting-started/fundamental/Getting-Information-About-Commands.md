---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Obtener información sobre los comandos
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: c51579fe2cdf4f2a0d3248d1aaf3f1f9cac83868
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482733"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="041b7-103">Obtener información sobre los comandos</span><span class="sxs-lookup"><span data-stu-id="041b7-103">Getting Information About Commands</span></span>
<span data-ttu-id="041b7-104">El cmdlet `Get-Command` de Windows PowerShell obtiene todos los comandos disponibles en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="041b7-104">The Windows PowerShell `Get-Command` cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="041b7-105">Cuando se escribe `Get-Command` en un símbolo del sistema de Windows PowerShell, se obtiene un resultado como este:</span><span class="sxs-lookup"><span data-stu-id="041b7-105">When you type `Get-Command` at a PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="041b7-106">Este resultado se parece mucho al resultado de la Ayuda de Cmd.exe: es un resumen tabular de comandos internos.</span><span class="sxs-lookup"><span data-stu-id="041b7-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="041b7-107">En el extracto de la salida del comando **Get-Command** mostrado anteriormente, la sección CommandType de cada comando es Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="041b7-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="041b7-108">Un cmdlet es el tipo de comando intrínseco de Windows PowerShell: un tipo que equivale en cierto modo a los comandos **dir** y **cd** de Cmd.exe y a elementos integrados de los shells de UNIX, como BASH.</span><span class="sxs-lookup"><span data-stu-id="041b7-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="041b7-109">En la salida del comando `Get-Command`, todas las definiciones terminan con puntos suspensivos (...) para indicar que PowerShell no puede mostrar todo el contenido en el espacio disponible.</span><span class="sxs-lookup"><span data-stu-id="041b7-109">In the output of the `Get-Command` command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="041b7-110">Cuando Windows PowerShell muestra un resultado, le aplica un formato de texto y, a continuación, lo organiza para ajustar los datos correctamente en la ventana.</span><span class="sxs-lookup"><span data-stu-id="041b7-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="041b7-111">Hablaremos sobre esto más adelante en la sección sobre formateadores.</span><span class="sxs-lookup"><span data-stu-id="041b7-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="041b7-112">El cmdlet `Get-Command` tiene un parámetro **Syntax** con el que se obtiene la sintaxis de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="041b7-112">The `Get-Command` cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="041b7-113">Para obtener la sintaxis del cmdlet Get-Help, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="041b7-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

```
Get-Command Get-Help -Syntax

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a><span data-ttu-id="041b7-114">Mostrar tipos de comandos disponibles</span><span class="sxs-lookup"><span data-stu-id="041b7-114">Displaying Available Command Types</span></span>
<span data-ttu-id="041b7-115">El comando **Get-Command** no enumera todos los comandos que están disponibles en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="041b7-115">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="041b7-116">En su lugar, el comando **Get-Command** enumera únicamente los cmdlets de la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="041b7-116">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="041b7-117">En realidad, Windows PowerShell admite otros muchos tipos de comandos.</span><span class="sxs-lookup"><span data-stu-id="041b7-117">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="041b7-118">Los alias, funciones y scripts también son comandos de Windows PowerShell, aunque no se describen en detalle en la guía de usuario de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="041b7-118">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="041b7-119">Los archivos externos que son ejecutables o que tienen un controlador de tipo de archivo registrado, también son comandos.</span><span class="sxs-lookup"><span data-stu-id="041b7-119">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="041b7-120">Para obtener todos los comandos de la sesión, escriba:</span><span class="sxs-lookup"><span data-stu-id="041b7-120">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="041b7-121">Esta lista incluye los archivos externos de su ruta de búsqueda, con lo cual puede contener miles de elementos.</span><span class="sxs-lookup"><span data-stu-id="041b7-121">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="041b7-122">Es más útil buscar en un conjunto reducido de comandos.</span><span class="sxs-lookup"><span data-stu-id="041b7-122">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="041b7-123">Para obtener los comandos nativos de otros tipos, use el parámetro **CommandType** del cmdlet `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="041b7-123">To get native commands of other types, use the **CommandType** parameter of the `Get-Command` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="041b7-124">El asterisco (\*) sirve de comodín para hallar coincidencias en los argumentos de comando de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="041b7-124">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="041b7-125">El carácter \* quiere decir "coincide con uno o varios caracteres".</span><span class="sxs-lookup"><span data-stu-id="041b7-125">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="041b7-126">Así, puede escribir `Get-Command a*` para encontrar todos los comandos que comienzan por la letra "a".</span><span class="sxs-lookup"><span data-stu-id="041b7-126">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="041b7-127">A diferencia de las búsquedas con comodín en Cmd.exe, los comodines de Windows PowerShell también encontrarán coincidencias de período.</span><span class="sxs-lookup"><span data-stu-id="041b7-127">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="041b7-128">Para obtener los alias de comandos (que son los sobrenombres asignados de los comandos), escriba:</span><span class="sxs-lookup"><span data-stu-id="041b7-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="041b7-129">Para obtener las funciones en la sesión actual, escriba:</span><span class="sxs-lookup"><span data-stu-id="041b7-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="041b7-130">Para mostrar los scripts en la ruta de búsqueda de Windows PowerShell, escriba:</span><span class="sxs-lookup"><span data-stu-id="041b7-130">To display scripts in Windows PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```
