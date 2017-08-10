---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Trabajar con archivos y carpetas
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 73773df9f018c396c9c4237a40f2e9d2c841464e
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="ddbaa-103">Trabajar con archivos y carpetas</span><span class="sxs-lookup"><span data-stu-id="ddbaa-103">Working with Files and Folders</span></span>
<span data-ttu-id="ddbaa-104">Navegar a través de unidades de Windows PowerShell y manipular los elementos son procesos similares al de manipulación de archivos y carpetas en unidades de disco físico de Windows.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="ddbaa-105">Explicaremos cómo tratar con tareas específicas de manipulación de archivos y carpetas en esta sección.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-105">We will discuss how to deal with specific file and folder manipulation tasks in this section.</span></span>

### <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="ddbaa-106">Enumerar todos los archivos y carpetas de una carpeta</span><span class="sxs-lookup"><span data-stu-id="ddbaa-106">Listing All the Files and Folders Within a Folder</span></span>
<span data-ttu-id="ddbaa-107">Puede obtener todos los elementos directamente dentro de una carpeta mediante **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="ddbaa-108">Agregue el parámetro **Force** opcional para mostrar elementos ocultos o del sistema.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="ddbaa-109">Por ejemplo, este comando muestra el contenido directo de la unidad C de Windows PowerShell (que es la misma que la unidad física de Windows C):</span><span class="sxs-lookup"><span data-stu-id="ddbaa-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```
Get-ChildItem -Force C:\
```

<span data-ttu-id="ddbaa-110">El comando muestra solo los elementos contenidos directamente, lo que se parece a usar el comando **DIR** de Cmd.exe o **ls** en un shell de UNIX.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="ddbaa-111">Para mostrar los elementos contenidos, también es preciso especificar el parámetro **-Recurse**.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="ddbaa-112">(Este proceso puede tardar mucho tiempo en completarse). Para mostrar todo el contenido de la unidad C:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```
Get-ChildItem -Force C:\ -Recurse
```

<span data-ttu-id="ddbaa-113">**Get-ChildItem** puede filtrar elementos con sus parámetros **Path**, **Filter**, **Include** y **Exclude**, pero estos suelen basarse solo en el nombre.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="ddbaa-114">Puede realizar un filtrado complejo basado en otras propiedades de elementos mediante **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="ddbaa-115">El siguiente comando busca todos los ejecutables en la carpeta Archivos de programa que se modificaron por última vez después del 1 de octubre de 2005, cuyo tamaño no es inferior a 1 megabyte ni superior a 10 megabytes:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt "2005-10-01") -and ($_.Length -ge 1m) -and ($_.Length -le 10m)}
```

### <a name="copying-files-and-folders"></a><span data-ttu-id="ddbaa-116">Compartir archivos y carpetas</span><span class="sxs-lookup"><span data-stu-id="ddbaa-116">Copying Files and Folders</span></span>
<span data-ttu-id="ddbaa-117">La copia se realiza con **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="ddbaa-118">El comando siguiente realiza una copia de seguridad de C:\\boot.ini en C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak
```

<span data-ttu-id="ddbaa-119">Si el archivo de destino ya existe, se produce un error en el intento de copia.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="ddbaa-120">Para sobrescribir un destino preexistente, use el parámetro Force:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-120">To overwrite a pre-existing destination, use the Force parameter:</span></span>

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak -Force
```

<span data-ttu-id="ddbaa-121">Este comando funciona aunque el destino sea de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="ddbaa-122">La copia de carpetas funciona del mismo modo.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-122">Folder copying works the same way.</span></span> <span data-ttu-id="ddbaa-123">Este comando copia la carpeta C:\\temp\\test1 en la nueva carpeta c:\\temp\\DeleteMe de forma recursiva:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-123">This command copies the folder C:\\temp\\test1 to the new folder c:\\temp\\DeleteMe recursively:</span></span>

```
Copy-Item C:\temp\test1 -Recurse c:\temp\DeleteMe
```

<span data-ttu-id="ddbaa-124">También puede copiar una selección de elementos.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-124">You can also copy a selection of items.</span></span> <span data-ttu-id="ddbaa-125">El siguiente comando copia todos los archivos .txt de cualquier ubicación en c:\\data en c:\\temp\\text:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination c:\temp\text
```

<span data-ttu-id="ddbaa-126">Todavía puede usar otras herramientas para realizar copias del sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="ddbaa-127">Todos los objetos XCOPY, ROBOCOPY y COM, como **Scripting.FileSystemObject**, funcionan en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="ddbaa-128">Por ejemplo, puede usar la clase **Scripting.FileSystem COM** de Windows Script Host para realizar una copia de seguridad de C:\\boot.ini en C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```
(New-Object -ComObject Scripting.FileSystemObject).CopyFile("c:\boot.ini", "c:\boot.bak")
```

### <a name="creating-files-and-folders"></a><span data-ttu-id="ddbaa-129">Crear archivos y carpetas</span><span class="sxs-lookup"><span data-stu-id="ddbaa-129">Creating Files and Folders</span></span>
<span data-ttu-id="ddbaa-130">La creación de nuevos elementos funciona igual en todos los proveedores de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="ddbaa-131">Si un proveedor de Windows PowerShell tiene más de un tipo de elemento (por ejemplo, el proveedor FileSystem de Windows PowerShell distingue entre directorios y archivos), debe especificar el tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="ddbaa-132">Este comando crea una nueva carpeta C:\\temp\\Nueva carpeta:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```
New-Item -Path 'C:\temp\New Folder' -ItemType "directory"
```

<span data-ttu-id="ddbaa-133">Este comando crea un nuevo archivo vacío C:\\temp\\Nueva carpeta\\file.txt</span><span class="sxs-lookup"><span data-stu-id="ddbaa-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType "file"
```

### <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="ddbaa-134">Quitar todos los archivos y carpetas de una carpeta</span><span class="sxs-lookup"><span data-stu-id="ddbaa-134">Removing All Files and Folders Within a Folder</span></span>
<span data-ttu-id="ddbaa-135">Puede quitar los elementos contenidos mediante **Remove-Item**, pero se le pedirá que confirme la eliminación si el elemento contiene algo más.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="ddbaa-136">Por ejemplo, si intenta eliminar la carpeta C:\\temp\\DeleteMe que contiene otros elementos, Windows PowerShell le pedirá confirmación antes de eliminar la carpeta:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="ddbaa-137">Si no quiere que se le solicite confirmación por cada elemento contenido, especifique el parámetro **Recurse**:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```
Remove-Item C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="ddbaa-138">Asignar una carpeta local como una unidad accesible de Windows</span><span class="sxs-lookup"><span data-stu-id="ddbaa-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>
<span data-ttu-id="ddbaa-139">También puede asignar una carpeta local mediante el comando **subst**.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="ddbaa-140">El siguiente comando crea una unidad local P: con raíz en el directorio local Archivos de programa:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```
subst p: $env:programfiles
```

<span data-ttu-id="ddbaa-141">Al igual que con las unidades de red, las unidades asignadas dentro de Windows PowerShell con **subst** son visibles inmediatamente en el shell de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

### <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="ddbaa-142">Leer un archivo de texto en una matriz</span><span class="sxs-lookup"><span data-stu-id="ddbaa-142">Reading a Text File into an Array</span></span>
<span data-ttu-id="ddbaa-143">Uno de los formatos de almacenamiento más comunes para los datos de texto es en un archivo con líneas separadas que se tratan como elementos de datos distintos.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="ddbaa-144">El cmdlet **Get-Content** puede usarse para leer un archivo completo en un solo paso, como se muestra aquí:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional 
with Data Execution Prevention" /noexecute=optin /fastdetect
```

<span data-ttu-id="ddbaa-145">**Get-Content** ya trata los datos leídos del archivo como una matriz con un elemento por línea de contenido del archivo.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="ddbaa-146">Para confirmarlo, compruebe la **longitud** del contenido devuelto:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="ddbaa-147">Este comando es más útil para obtener listas de información en Windows PowerShell directamente.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="ddbaa-148">Por ejemplo, podría almacenar una lista de nombres de equipo o direcciones IP en un archivo C:\\temp\\domainMembers.txt, con un nombre en cada línea del archivo.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="ddbaa-149">Puede usar **Get-Content** para recuperar el contenido del archivo y colocarlo en la variable **$Computers**:</span><span class="sxs-lookup"><span data-stu-id="ddbaa-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="ddbaa-150">**$Computers** es ahora una matriz que contiene un nombre de equipo en cada elemento.</span><span class="sxs-lookup"><span data-stu-id="ddbaa-150">**$Computers** is now an array containing a computer name in each element.</span></span>

