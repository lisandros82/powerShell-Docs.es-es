---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Usar variables para almacenar objetos
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 067948d7c234fb70c7cf9966c9ae3e8df1f99757
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="07ecc-103">Usar variables para almacenar objetos</span><span class="sxs-lookup"><span data-stu-id="07ecc-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="07ecc-104">Windows PowerShell funciona con objetos.</span><span class="sxs-lookup"><span data-stu-id="07ecc-104">Windows PowerShell works with objects.</span></span> <span data-ttu-id="07ecc-105">Windows PowerShell permite crear variables (básicamente objetos con nombre) para conservar la salida para usos posteriores.</span><span class="sxs-lookup"><span data-stu-id="07ecc-105">Windows PowerShell lets you create variables - essentially named objects - to preserve output to use later.</span></span> <span data-ttu-id="07ecc-106">Si está acostumbrado a trabajar con variables en otros shells, recuerde que las variables de Windows PowerShell son objetos, no texto.</span><span class="sxs-lookup"><span data-stu-id="07ecc-106">If you are used to working with variables in other shells, remember that Windows PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="07ecc-107">Las variables siempre se especifican con el carácter inicial $ y pueden incluir cualquier carácter alfanumérico o el carácter de subrayado en sus nombres.</span><span class="sxs-lookup"><span data-stu-id="07ecc-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="07ecc-108">Crear una variable</span><span class="sxs-lookup"><span data-stu-id="07ecc-108">Creating a Variable</span></span>
<span data-ttu-id="07ecc-109">Para crear una variable, puede escribir un nombre de variable válido:</span><span class="sxs-lookup"><span data-stu-id="07ecc-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="07ecc-110">Esto no devuelve ningún resultado porque **$loc** no tiene un valor.</span><span class="sxs-lookup"><span data-stu-id="07ecc-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="07ecc-111">Puede crear una variable y asignarle un valor en el mismo paso.</span><span class="sxs-lookup"><span data-stu-id="07ecc-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="07ecc-112">Windows PowerShell solo crea la variable si no existe; de lo contrario, asigna el valor especificado a la variable existente.</span><span class="sxs-lookup"><span data-stu-id="07ecc-112">Windows PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="07ecc-113">Para almacenar su ubicación actual en la variable **$loc**, escriba:</span><span class="sxs-lookup"><span data-stu-id="07ecc-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="07ecc-114">No se muestra ninguna salida cuando escribe este comando porque la salida se envía a $loc.</span><span class="sxs-lookup"><span data-stu-id="07ecc-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="07ecc-115">En Windows PowerShell, la salida mostrada es un efecto secundario del hecho de que los datos siempre se envíen a la pantalla, si no se indica de otro modo.</span><span class="sxs-lookup"><span data-stu-id="07ecc-115">In Windows PowerShell, displayed output is a side effect of the fact that data which is not otherwise directed always gets sent to the screen.</span></span> <span data-ttu-id="07ecc-116">Al escribir $loc se mostrará su ubicación actual:</span><span class="sxs-lookup"><span data-stu-id="07ecc-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="07ecc-117">Puede usar **Get-Member** para mostrar información sobre el contenido de las variables.</span><span class="sxs-lookup"><span data-stu-id="07ecc-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="07ecc-118">La canalización de $loc a Get-Member le mostrará que se trata de un objeto **PathInfo**, al igual que la salida de Get-Location:</span><span class="sxs-lookup"><span data-stu-id="07ecc-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="07ecc-119">Manipular variables</span><span class="sxs-lookup"><span data-stu-id="07ecc-119">Manipulating Variables</span></span>
<span data-ttu-id="07ecc-120">Windows PowerShell proporciona varios comandos para manipular variables.</span><span class="sxs-lookup"><span data-stu-id="07ecc-120">Windows PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="07ecc-121">Para ver una lista completa en un formato legible, escriba:</span><span class="sxs-lookup"><span data-stu-id="07ecc-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="07ecc-122">Además de las variables que crea en la sesión actual de Windows PowerShell, existen varias variables definidas por el sistema.</span><span class="sxs-lookup"><span data-stu-id="07ecc-122">In addition to the variables you create in your current Windows PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="07ecc-123">Puede usar el cmdlet **Remove-Variable** para borrar todas las variables que no se controlan mediante Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07ecc-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by Windows PowerShell.</span></span> <span data-ttu-id="07ecc-124">Escriba el siguiente comando para borrar todas las variables:</span><span class="sxs-lookup"><span data-stu-id="07ecc-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="07ecc-125">Esto generará el mensaje de confirmación que aparece a continuación.</span><span class="sxs-lookup"><span data-stu-id="07ecc-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="07ecc-126">Si ejecuta el cmdlet **Get-Variable**, verá las demás variables de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07ecc-126">If you then run the **Get-Variable** cmdlet, you will see the remaining Windows PowerShell variables.</span></span> <span data-ttu-id="07ecc-127">Puesto que también existe una unidad de Windows PowerShell variable, también puede mostrar todas las variables de Windows PowerShell. Para ello, escriba:</span><span class="sxs-lookup"><span data-stu-id="07ecc-127">Since there is also a variable Windows PowerShell drive, you can also display all Windows PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="07ecc-128">Usar variables de Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="07ecc-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="07ecc-129">Aunque Windows PowerShell no es Cmd.exe, se ejecuta en un entorno de shell de comandos y puede usar las mismas variables disponibles en cualquier entorno de Windows.</span><span class="sxs-lookup"><span data-stu-id="07ecc-129">Although Windows PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="07ecc-130">Estas variables se exponen a través de una unidad denominada **env**:.</span><span class="sxs-lookup"><span data-stu-id="07ecc-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="07ecc-131">Para ver estas variables, escriba:</span><span class="sxs-lookup"><span data-stu-id="07ecc-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="07ecc-132">Aunque los cmdlets de variables estándar no están diseñados para trabajar con variables **env:**, puede seguir usándolos si especifica el prefijo **env:**.</span><span class="sxs-lookup"><span data-stu-id="07ecc-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="07ecc-133">Por ejemplo, para ver el directorio raíz del sistema operativo, puede usar la variable **%SystemRoot%** del shell de comandos en Windows PowerShell. Para ello, escriba:</span><span class="sxs-lookup"><span data-stu-id="07ecc-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within Windows PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="07ecc-134">También puede crear y modificar variables de entorno desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07ecc-134">You can also create and modify environment variables from within Windows PowerShell.</span></span> <span data-ttu-id="07ecc-135">Las variables de entorno a las que se accede desde Windows PowerShell se ajustan a las reglas habituales para las variables de entorno en cualquier otra ubicación de Windows.</span><span class="sxs-lookup"><span data-stu-id="07ecc-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>

