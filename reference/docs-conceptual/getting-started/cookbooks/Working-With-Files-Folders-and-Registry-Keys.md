---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Trabajar con archivos, carpetas y claves del Registro
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: 22a2390686659033bfd8b02a151b3397cfd46a22
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="48699-103">Trabajar con archivos, carpetas y claves del Registro</span><span class="sxs-lookup"><span data-stu-id="48699-103">Working With Files, Folders and Registry Keys</span></span>
<span data-ttu-id="48699-104">En Windows PowerShell se usa el término **Item** para hacer referencia a los elementos contenidos en una unidad de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48699-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="48699-105">Cuando se trabaja con el proveedor FileSystem de Windows PowerShell, un **Item** puede ser un archivo, una carpeta o la unidad de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48699-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="48699-106">Enumerar estos elementos y trabajar con ellos son tareas críticas básicas en la mayoría de las configuraciones administrativas, de modo que conviene abordar estas tareas en profundidad.</span><span class="sxs-lookup"><span data-stu-id="48699-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="48699-107">Enumerar archivos, carpetas y claves del Registro (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="48699-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>
<span data-ttu-id="48699-108">Hacerse con una colección de elementos de una ubicación determinada es una tarea extremadamente común, por lo que el cmdlet **Get-ChildItem** está diseñado específicamente para devolver todos los elementos dentro de un contenedor, como, por ejemplo, una carpeta.</span><span class="sxs-lookup"><span data-stu-id="48699-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="48699-109">Si desea que se devuelvan todos los archivos y carpetas contenidos directamente dentro de la carpeta C:\\Windows, escriba:</span><span class="sxs-lookup"><span data-stu-id="48699-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

<span data-ttu-id="48699-110">La lista es similar a lo que se obtendría si se especificara el comando **dir** en **Cmd.exe** o el comando **ls** en un shell de comandos de UNIX.</span><span class="sxs-lookup"><span data-stu-id="48699-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="48699-111">Si se usan los parámetros del cmdlet **Get-ChildItem**, se pueden confeccionar listas de enorme complejidad.</span><span class="sxs-lookup"><span data-stu-id="48699-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="48699-112">Pasemos a ver algunos escenarios sobre esto.</span><span class="sxs-lookup"><span data-stu-id="48699-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="48699-113">La sintaxis del cmdlet **Get-ChildItem** se puede ver escribiendo lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="48699-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```
PS> Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="48699-114">Estos parámetros se pueden mezclar y relacionar para obtener resultados muy personalizados.</span><span class="sxs-lookup"><span data-stu-id="48699-114">These parameters can be mixed and matched to get highly customized output.</span></span>

#### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="48699-115">Enumerar todos los elementos contenidos (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="48699-115">Listing all Contained Items (-Recurse)</span></span>
<span data-ttu-id="48699-116">Para ver tanto los elementos que hay dentro de una carpeta de Windows como cualquier elemento dentro de sus subcarpetas, use el parámetro **Recurse** de **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="48699-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="48699-117">La lista muestra todos los elementos dentro de la carpeta de Windows y los elementos de sus subcarpetas.</span><span class="sxs-lookup"><span data-stu-id="48699-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="48699-118">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="48699-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a><span data-ttu-id="48699-119">Filtrar elementos por su nombre (-Name)</span><span class="sxs-lookup"><span data-stu-id="48699-119">Filtering Items by Name (-Name)</span></span>
<span data-ttu-id="48699-120">Para mostrar solo los nombres de los elementos, use el parámetro **Name** de **Get-Childitem**:</span><span class="sxs-lookup"><span data-stu-id="48699-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="48699-121">Enumerar forzosamente los elementos ocultos (-Force)</span><span class="sxs-lookup"><span data-stu-id="48699-121">Forcibly Listing Hidden Items (-Force)</span></span>
<span data-ttu-id="48699-122">Los elementos que normalmente son invisibles en el Explorador de archivos o en Cmd.exe no aparecen en la salida de un comando **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="48699-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="48699-123">Para ver los elementos ocultos, use el parámetro **Force** de **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="48699-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="48699-124">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="48699-124">For example:</span></span>

```
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="48699-125">Este parámetro se llama Force porque permite anular a la fuerza el comportamiento normal del comando **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="48699-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="48699-126">Force es un parámetro muy usado que fuerza una acción que un cmdlet normalmente no realizaría, si bien no llevará a cabo ninguna acción que ponga en peligro la seguridad del sistema.</span><span class="sxs-lookup"><span data-stu-id="48699-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

#### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="48699-127">Buscar nombres de elemento coincidentes con caracteres comodín</span><span class="sxs-lookup"><span data-stu-id="48699-127">Matching Item Names with Wildcards</span></span>
<span data-ttu-id="48699-128">**El comando Get-ChildItem** acepta caracteres comodín en la ruta de acceso de los elementos que se van a enumerar.</span><span class="sxs-lookup"><span data-stu-id="48699-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="48699-129">Dado que las coincidencias con caracteres comodín se controla mediante el motor de Windows PowerShell, todos los cmdlets que acepten caracteres comodín usan la misma notación y tienen el mismo comportamiento de búsqueda de coincidencias.</span><span class="sxs-lookup"><span data-stu-id="48699-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="48699-130">La notación de caracteres comodín de Windows PowerShell conlleva las siguientes reglas:</span><span class="sxs-lookup"><span data-stu-id="48699-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="48699-131">El asterisco (\*) coincide con cero o más repeticiones de cualquier carácter.</span><span class="sxs-lookup"><span data-stu-id="48699-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="48699-132">El signo de interrogación de cierre (?) coincide exactamente con un carácter.</span><span class="sxs-lookup"><span data-stu-id="48699-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="48699-133">Los caracteres de corchete de apertura (\[) y corchete de cierre (]) rodean un juego de caracteres que debe coincidir.</span><span class="sxs-lookup"><span data-stu-id="48699-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="48699-134">A continuación presentamos algunos ejemplos de cómo funciona la especificación de caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="48699-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="48699-135">Escriba el siguiente comando para encontrar todos los archivos en el directorio de Windows con el sufijo **.log** y exactamente cinco caracteres en el nombre base:</span><span class="sxs-lookup"><span data-stu-id="48699-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\?????.log
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

<span data-ttu-id="48699-136">Escriba lo siguiente para encontrar todos los archivos que comienzan por la letra **x** en el directorio de Windows:</span><span class="sxs-lookup"><span data-stu-id="48699-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="48699-137">Escriba lo siguiente para encontrar todos los archivos cuyos nombres comiencen por **x** o **z**:</span><span class="sxs-lookup"><span data-stu-id="48699-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a><span data-ttu-id="48699-138">Excluir elementos (-Exclude)</span><span class="sxs-lookup"><span data-stu-id="48699-138">Excluding Items (-Exclude)</span></span>
<span data-ttu-id="48699-139">Puede excluir elementos concretos con el parámetro **Exclude** de Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="48699-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="48699-140">Esto le permite realizar filtrados complejos en una sola instrucción.</span><span class="sxs-lookup"><span data-stu-id="48699-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="48699-141">Por ejemplo, imaginemos que estamos buscando el archivo DLL del Servicio de hora de Windows en la carpeta System32, y todo lo que recuerda del nombre del archivo DLL es que comienza por "W" y contiene "32".</span><span class="sxs-lookup"><span data-stu-id="48699-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="48699-142">Con una expresión como **w\&#42;32\&#42;.dll**, se detectarán todos los archivos DLL que cumplan las condiciones, pero también se pueden devolver los archivos DLL de compatibilidad de Windows 95 y Windows de 16 bits que incluyan "95" o "16" en sus nombres.</span><span class="sxs-lookup"><span data-stu-id="48699-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="48699-143">Puede omitir todos los archivos que contengan cualquiera de estos números en sus nombres, para lo que debe usar el parámetro **Exclude** con el patrón **\&#42;\[9516]\&#42;**:</span><span class="sxs-lookup"><span data-stu-id="48699-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

<pre>PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*
Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll</pre>

#### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="48699-144">Mezclar parámetros de Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="48699-144">Mixing Get-ChildItem Parameters</span></span>
<span data-ttu-id="48699-145">Se pueden usar varios de los parámetros del cmdlet **Get-ChildItem** en el mismo comando.</span><span class="sxs-lookup"><span data-stu-id="48699-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="48699-146">Antes de mezclar parámetros, asegúrese de que comprende el concepto de búsqueda de coincidencias con caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="48699-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="48699-147">Por ejemplo, el siguiente comando no devuelve ningún resultado:</span><span class="sxs-lookup"><span data-stu-id="48699-147">For example, the following command returns no results:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="48699-148">No hay ningún resultado, a pesar de que hay dos archivos DLL que comienzan por la letra "z" en la carpeta de Windows.</span><span class="sxs-lookup"><span data-stu-id="48699-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="48699-149">No se devolvieron resultados porque hemos especificado el carácter comodín como parte de la ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="48699-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="48699-150">Aunque el comando era recursivo, el cmdlet **Get-ChildItem** limitó los elementos a aquellos que están en la carpeta de Windows y cuyos nombres terminan en ".dll".</span><span class="sxs-lookup"><span data-stu-id="48699-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="48699-151">Para especificar una búsqueda recursiva de archivos cuyos nombres coincidan con un patrón especial, use el parámetro **-Include**.</span><span class="sxs-lookup"><span data-stu-id="48699-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```

