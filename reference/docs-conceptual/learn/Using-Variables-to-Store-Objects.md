---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Usar variables para almacenar objetos
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030376"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="5dcb3-103">Usar variables para almacenar objetos</span><span class="sxs-lookup"><span data-stu-id="5dcb3-103">Using variables to store objects</span></span>

<span data-ttu-id="5dcb3-104">PowerShell funciona con objetos.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-104">PowerShell works with objects.</span></span> <span data-ttu-id="5dcb3-105">PowerShell le permite crear objetos con nombre conocidos como variables.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="5dcb3-106">Los nombres de variables pueden incluir el carácter de subrayado y cualquier carácter alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="5dcb3-107">Cuando se utiliza en PowerShell, siempre se especifica una variable utilizando el carácter \$ seguido del nombre de la variable.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="5dcb3-108">Creación de una variable</span><span class="sxs-lookup"><span data-stu-id="5dcb3-108">Creating a variable</span></span>

<span data-ttu-id="5dcb3-109">Para crear una variable, puede escribir un nombre de variable válido:</span><span class="sxs-lookup"><span data-stu-id="5dcb3-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="5dcb3-110">Este ejemplo no devuelve ningún resultado porque `$loc` no tiene un valor.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="5dcb3-111">Puede crear una variable y asignarle un valor en el mismo paso.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="5dcb3-112">PowerShell solo crea la variable si no existe.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="5dcb3-113">De lo contrario, asigna el valor especificado a la variable existente.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="5dcb3-114">En el ejemplo siguiente se almacena la ubicación actual en la variable `$loc`:</span><span class="sxs-lookup"><span data-stu-id="5dcb3-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="5dcb3-115">PowerShell no muestra ninguna salida cuando se escribe este comando.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="5dcb3-116">PowerShell envía la salida de "Get-Location" a `$loc`.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="5dcb3-117">En PowerShell, los datos que no están asignados o redirigidos se envían a la pantalla.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="5dcb3-118">Si se escribe `$loc`, se muestra la ubicación actual:</span><span class="sxs-lookup"><span data-stu-id="5dcb3-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="5dcb3-119">Puede usar `Get-Member` para mostrar información sobre el contenido de las variables.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="5dcb3-120">`Get-Member` muestra que `$loc` es un objeto **PathInfo**, al igual que la salida de `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="5dcb3-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="5dcb3-121">Manipulación de variables</span><span class="sxs-lookup"><span data-stu-id="5dcb3-121">Manipulating variables</span></span>

<span data-ttu-id="5dcb3-122">PowerShell proporciona varios comandos para manipular variables.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="5dcb3-123">Para ver una lista completa en un formato legible, escriba:</span><span class="sxs-lookup"><span data-stu-id="5dcb3-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="5dcb3-124">PowerShell también crea varias variables definidas por el sistema.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="5dcb3-125">Puede usar el cmdlet `Remove-Variable` para quitar variables, que no se controlan mediante PowerShell, de la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="5dcb3-126">Escriba el siguiente comando para borrar todas las variables:</span><span class="sxs-lookup"><span data-stu-id="5dcb3-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="5dcb3-127">Después de ejecutar el comando anterior, el cmdlet `Get-Variable` muestra las variables del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="5dcb3-128">PowerShell también crea una unidad variable.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="5dcb3-129">Use el siguiente ejemplo para mostrar todas las variables de PowerShell mediante la unidad variable:</span><span class="sxs-lookup"><span data-stu-id="5dcb3-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="5dcb3-130">Uso de variables de Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="5dcb3-130">Using cmd.exe variables</span></span>

<span data-ttu-id="5dcb3-131">PowerShell puede usar las mismas variables de entorno disponibles para cualquier proceso de Windows, incluido **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="5dcb3-132">Estas variables se exponen a través de una unidad denominada `env:`.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="5dcb3-133">Para ver estas variables, escriba el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="5dcb3-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="5dcb3-134">Los cmdlet `*-Variable` estándar no están diseñados para trabajar con variables de entorno.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="5dcb3-135">Las variables de entorno son accesibles mediante el prefijo de unidad `env:`.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="5dcb3-136">Por ejemplo, la variable **%SystemRoot%** de **cmd.exe** contiene el nombre del directorio raíz del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="5dcb3-137">En PowerShell, se utiliza `$env:SystemRoot` para acceder al mismo valor.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="5dcb3-138">También puede crear y modificar variables de entorno desde PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="5dcb3-139">Las variables de entorno de PowerShell siguen las mismas reglas para las variables de entorno que se utilizan en cualquier otra parte del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="5dcb3-140">En el ejemplo siguiente se crea una nueva variable de entorno:</span><span class="sxs-lookup"><span data-stu-id="5dcb3-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="5dcb3-141">Aunque no es obligatorio, es común que los nombres de variables de entorno utilicen todas las letras mayúsculas.</span><span class="sxs-lookup"><span data-stu-id="5dcb3-141">Though not required, it's common for environment variable names to use all uppercase letters.</span></span>
