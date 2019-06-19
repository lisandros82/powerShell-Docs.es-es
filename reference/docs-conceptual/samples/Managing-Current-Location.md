---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Administrar la ubicación actual
ms.openlocfilehash: 42ab56759dec882d140f813c8614e578957722b3
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030202"
---
# <a name="managing-current-location"></a><span data-ttu-id="bf8b8-103">Administrar la ubicación actual</span><span class="sxs-lookup"><span data-stu-id="bf8b8-103">Managing Current Location</span></span>

<span data-ttu-id="bf8b8-104">Al navegar por los sistemas de carpeta en el Explorador de archivos, normalmente tiene una ubicación de trabajo específica; es decir, la carpeta abierta actual.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="bf8b8-105">Los elementos de la carpeta actual se pueden manipular fácilmente haciendo clic en ellos.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="bf8b8-106">En las interfaces de línea de comandos como Cmd.exe, si está en la misma carpeta que un archivo determinado, puede tener acceso a él especificando un nombre relativamente corto. No será necesario especificar la ruta de acceso completa al archivo.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="bf8b8-107">El directorio actual se conoce como el directorio de trabajo.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="bf8b8-108">Windows PowerShell usa el término **Location** para referirse al directorio de trabajo e implementa una familia de cmdlets para examinar y manipular la ubicación.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

## <a name="getting-your-current-location-get-location"></a><span data-ttu-id="bf8b8-109">Obtener la ubicación actual (Get-Location)</span><span class="sxs-lookup"><span data-stu-id="bf8b8-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="bf8b8-110">Para averiguar la ruta de acceso de su ubicación de directorio actual, escriba el comando **Get-Location**:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="bf8b8-111">El cmdlet Get-Location es similar al comando **pwd** en el shell de BASH.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="bf8b8-112">El cmdlet Set-Location es similar al comando **cd** en Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

## <a name="setting-your-current-location-set-location"></a><span data-ttu-id="bf8b8-113">Configurar la ubicación actual (Set-Location)</span><span class="sxs-lookup"><span data-stu-id="bf8b8-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="bf8b8-114">El comando **Get-Location** se usa con el comando **Set-Location**.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="bf8b8-115">El comando **Set-Location** permite especificar la ubicación de directorio actual.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="bf8b8-116">Después de escribir el comando, observará que no recibe ningún tipo de información directa sobre el efecto del comando.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="bf8b8-117">Casi todos los comandos de Windows PowerShell que realizan una acción apenas si generan resultados, ya que no siempre son útiles.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="bf8b8-118">Para comprobar que se ha producido un cambio de directorio correcto al escribir el comando **Set-Location**, incluya el parámetro **-PassThru** cuando escriba el comando **Set-Location**:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="bf8b8-119">El parámetro **-PassThru**se puede usar con muchos comandos Set en Windows PowerShell para devolver información sobre el resultado en aquellos casos en que no haya ninguna salida predeterminada.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="bf8b8-120">Puede especificar rutas relativas a la ubicación actual de la misma manera en que lo haría en la mayoría de los shells de comandos de UNIX y Windows.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="bf8b8-121">En la notación estándar de las rutas de acceso relativas, un punto (**.**) representa la carpeta actual y dos puntos (**..**), el directorio principal de su ubicación actual.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="bf8b8-122">Así, si está en la carpeta **C:\\Windows**, un punto (**.**) representa a **C:\\Windows** y dos puntos (**..**), a **C:**.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="bf8b8-123">Puede cambiar su ubicación actual por la raíz de la unidad C:; para ello, escriba:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="bf8b8-124">Esta misma técnica funciona en unidades de Windows PowerShell que no son unidades del sistema de archivos, como **HKLM:**.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="bf8b8-125">Puede establecer su ubicación en la clave HKLM\\Software del Registro escribiendo lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="bf8b8-126">Luego, puede cambiar la ubicación del directorio al directorio principal (que es la raíz de la unidad HKLM: de Windows PowerShell) usando una ruta de acceso relativa:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="bf8b8-127">Puede escribir Set-Location o usar cualquiera de los alias de Windows PowerShell integrados para Set-Location (cd, chdir, sl).</span><span class="sxs-lookup"><span data-stu-id="bf8b8-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="bf8b8-128">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="bf8b8-129">Guardar y recuperar ubicaciones recientes (Push-Location y Pop-Location)</span><span class="sxs-lookup"><span data-stu-id="bf8b8-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="bf8b8-130">Al cambiar de ubicación, es útil realizar un seguimiento de dónde ha estado y poder volver a la ubicación anterior.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="bf8b8-131">El cmdlet **Push-Location** de Windows PowerShell crea un historial ordenado (una "pila") de las rutas de acceso de directorio donde ha estado, mientras que el cmdlet complementario **Pop-Location** sirve para ir hacia atrás en el historial de las rutas de acceso de directorio.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="bf8b8-132">Por ejemplo, Windows PowerShell suele iniciarse en el directorio principal del usuario.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="bf8b8-133">La palabra *pila* tiene un significado especial en muchas configuraciones de programación, incluido .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="bf8b8-134">Al igual que sucede con una pila física de elementos, el último elemento que se coloca en la pila es el primer elemento que se puede extraer de ella.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="bf8b8-135">Agregar un elemento a una pila se conoce coloquialmente como "insertar" el elemento en la pila,</span><span class="sxs-lookup"><span data-stu-id="bf8b8-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="bf8b8-136">mientras que extraer un elemento de la pila se suele conocer como "retirar" el elemento de la pila.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="bf8b8-137">Escriba lo siguiente para insertar la ubicación actual en la pila y, después, ir a la carpeta Configuración local:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="bf8b8-138">Tras ello, puede escribir lo siguiente para insertar la ubicación de Configuración local en la pila y moverse a la carpeta Temp:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-138">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="bf8b8-139">Si quiere confirmar que ha cambiado de directorio, escriba el comando **Get-Location**:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="bf8b8-140">Después, puede regresar al último directorio visitado; para ello, escriba el comando **Pop-Location** y compruebe el cambio con el comando **Get-Location**:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="bf8b8-141">Al igual que con el cmdlet **Set-Location**, puede incluir el parámetro **-PassThru** cuando escriba el cmdlet **Pop-Location** para mostrar el directorio que ha especificado:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="bf8b8-142">Los cmdlets Location también se pueden usar con rutas de acceso de red.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="bf8b8-143">Si tiene un servidor denominado FS01 con un recurso compartido denominado Public, puede cambiar la ubicación escribiendo:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="bf8b8-144">o</span><span class="sxs-lookup"><span data-stu-id="bf8b8-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="bf8b8-145">Puede usar los comandos **Push-Location** y **Set-Location** para cambiar la ubicación a cualquier unidad disponible.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="bf8b8-146">Por ejemplo, si tiene una unidad de CD-ROM local con la letra de unidad D que contiene un CD de datos, puede cambiar la ubicación a dicha unidad de CD escribiendo el comando **Set-Location D:**.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="bf8b8-147">Si la unidad está vacía, obtendrá el siguiente mensaje de error:</span><span class="sxs-lookup"><span data-stu-id="bf8b8-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="bf8b8-148">Cuando se usa una interfaz de línea de comandos, conviene no usar el Explorador de archivos para examinar las unidades de disco físicas disponibles.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="bf8b8-149">Además, el Explorador de archivos no le mostrará todas las unidades de disco de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="bf8b8-150">Windows PowerShell proporciona un conjunto de comandos para manipular unidades de Windows PowerShell, aspecto que trataremos más adelante.</span><span class="sxs-lookup"><span data-stu-id="bf8b8-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>
