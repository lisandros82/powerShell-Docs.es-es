---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Obtener información sobre los comandos"
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="65312-103">Obtener información sobre los comandos</span><span class="sxs-lookup"><span data-stu-id="65312-103">Getting Information About Commands</span></span>
<span data-ttu-id="65312-104">El cmdlet **Get-Command** de Windows PowerShell obtiene todos los comandos disponibles en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="65312-104">The Windows PowerShell **Get-Command** cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="65312-105">Cuando **Get-Command** se escribe en un símbolo del sistema de Windows PowerShell, se obtiene un resultado similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="65312-105">When you type **Get-Command** at a Windows PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="65312-106">Este resultado se parece mucho al resultado de la Ayuda de Cmd.exe: es un resumen tabular de comandos internos.</span><span class="sxs-lookup"><span data-stu-id="65312-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="65312-107">En el extracto de la salida del comando **Get-Command** mostrado anteriormente, la sección CommandType de cada comando es Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="65312-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="65312-108">Un cmdlet es el tipo de comando intrínseco de Windows PowerShell: un tipo que equivale en cierto modo a los comandos **dir** y **cd** de Cmd.exe y a elementos integrados de los shells de UNIX, como BASH.</span><span class="sxs-lookup"><span data-stu-id="65312-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="65312-109">En la salida del comando **Get-Command**, todas las definiciones terminan con puntos suspensivos (...) para indicar que PowerShell no puede mostrar todo el contenido en el espacio disponible.</span><span class="sxs-lookup"><span data-stu-id="65312-109">In the output of the **Get-Command** command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="65312-110">Cuando Windows PowerShell muestra un resultado, le aplica un formato de texto y, a continuación, lo organiza para ajustar los datos correctamente en la ventana.</span><span class="sxs-lookup"><span data-stu-id="65312-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="65312-111">Hablaremos sobre esto más adelante en la sección sobre formateadores.</span><span class="sxs-lookup"><span data-stu-id="65312-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="65312-112">El cmdlet **Get-Command** tiene un parámetro **Syntax** con el que se obtiene la sintaxis de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="65312-112">The **Get-Command** cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="65312-113">Para obtener la sintaxis del cmdlet Get-Help, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="65312-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

<span data-ttu-id="65312-114">**Get-Command Get-Help -Syntax**</span><span class="sxs-lookup"><span data-stu-id="65312-114">**Get-Command Get-Help -Syntax**</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a><span data-ttu-id="65312-115">Mostrar tipos de comandos disponibles</span><span class="sxs-lookup"><span data-stu-id="65312-115">Displaying Available Command Types</span></span>
<span data-ttu-id="65312-116">El comando **Get-Command** no enumera todos los comandos que están disponibles en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65312-116">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="65312-117">En su lugar, el comando **Get-Command** enumera únicamente los cmdlets de la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="65312-117">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="65312-118">En realidad, Windows PowerShell admite otros muchos tipos de comandos.</span><span class="sxs-lookup"><span data-stu-id="65312-118">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="65312-119">Los alias, funciones y scripts también son comandos de Windows PowerShell, aunque no se describen en detalle en la guía de usuario de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65312-119">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="65312-120">Los archivos externos que son ejecutables o que tienen un controlador de tipo de archivo registrado, también son comandos.</span><span class="sxs-lookup"><span data-stu-id="65312-120">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="65312-121">Para obtener todos los comandos de la sesión, escriba:</span><span class="sxs-lookup"><span data-stu-id="65312-121">To get all commands in the session, type:</span></span>

```
Get-Command *
```

<span data-ttu-id="65312-122">Esta lista incluye los archivos externos de su ruta de búsqueda, con lo cual puede contener miles de elementos.</span><span class="sxs-lookup"><span data-stu-id="65312-122">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="65312-123">Es más útil buscar en un conjunto reducido de comandos.</span><span class="sxs-lookup"><span data-stu-id="65312-123">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="65312-124">Para obtener los comandos nativos de otros tipos, use el parámetro **CommandType** del cmdet **Get-Command**.</span><span class="sxs-lookup"><span data-stu-id="65312-124">To get native commands of other types, use the **CommandType** parameter of the **Get-Command** cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="65312-125">El asterisco (\*) sirve de comodín para hallar coincidencias en los argumentos de comando de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65312-125">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="65312-126">El carácter \* quiere decir "coincide con uno o varios caracteres".</span><span class="sxs-lookup"><span data-stu-id="65312-126">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="65312-127">Así, puede escribir **Get-Command a\&#42;** para encontrar todos los comandos que comienzan por la letra "a".</span><span class="sxs-lookup"><span data-stu-id="65312-127">You can type **Get-Command a\&#42;** to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="65312-128">A diferencia de las búsquedas con comodín en Cmd.exe, los comodines de Windows PowerShell también encontrarán coincidencias de período.</span><span class="sxs-lookup"><span data-stu-id="65312-128">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="65312-129">Para obtener los alias de comandos (que son los sobrenombres asignados de los comandos), escriba:</span><span class="sxs-lookup"><span data-stu-id="65312-129">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```
Get-Command -CommandType Alias
```

<span data-ttu-id="65312-130">Para obtener las funciones en la sesión actual, escriba:</span><span class="sxs-lookup"><span data-stu-id="65312-130">To get the functions in the current session, type:</span></span>

```
Get-Command -CommandType Function
```

<span data-ttu-id="65312-131">Para mostrar los scripts en la ruta de búsqueda de Windows PowerShell, escriba:</span><span class="sxs-lookup"><span data-stu-id="65312-131">To display scripts in Windows PowerShell's search path, type:</span></span>

```
Get-Command -CommandType Script
```

