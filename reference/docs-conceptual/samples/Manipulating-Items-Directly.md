---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Manipular elementos directamente
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 4caa7d2e0eecff9783556062d8503fe10e616fe5
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293272"
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="af42f-103">Manipular elementos directamente</span><span class="sxs-lookup"><span data-stu-id="af42f-103">Manipulating Items Directly</span></span>

<span data-ttu-id="af42f-104">Los elementos que se ven en las unidades de Windows PowerShell (como los archivos y carpetas en las unidades del sistema de archivos y las claves del Registro en las unidades de Registro de Windows PowerShell) se denominan *elementos* en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af42f-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="af42f-105">Los cmdlets que funcionan con los elementos contienen el término **Item** en sus nombres.</span><span class="sxs-lookup"><span data-stu-id="af42f-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="af42f-106">La salida del comando **Get-Command -Noun Item** indica que hay nueve cmdlets de elemento en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af42f-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

## <a name="creating-new-items-new-item"></a><span data-ttu-id="af42f-107">Crear elementos (New-Item)</span><span class="sxs-lookup"><span data-stu-id="af42f-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="af42f-108">Para crear un elemento en el sistema de archivos, use el cmdlet **New-Item**.</span><span class="sxs-lookup"><span data-stu-id="af42f-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="af42f-109">Incluya el parámetro **Path** con la ruta de acceso al elemento y el parámetro **ItemType** con un valor "file" o "directory".</span><span class="sxs-lookup"><span data-stu-id="af42f-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="af42f-110">Por ejemplo, para crear un directorio denominado "New.Directory" en el directorio C:\\Temp, escriba:</span><span class="sxs-lookup"><span data-stu-id="af42f-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="af42f-111">Para crear un archivo, cambie el valor de **ItemType** a "file".</span><span class="sxs-lookup"><span data-stu-id="af42f-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="af42f-112">Por ejemplo, para crear un archivo denominado "file1.txt" en el directorio New.Directory, escriba:</span><span class="sxs-lookup"><span data-stu-id="af42f-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="af42f-113">Esta misma técnica se puede usar para crear una clave del Registro.</span><span class="sxs-lookup"><span data-stu-id="af42f-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="af42f-114">De hecho, una clave del Registro es más fácil de crear porque se trata del único tipo de elemento que hay en el Registro de Windows.</span><span class="sxs-lookup"><span data-stu-id="af42f-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="af42f-115">(Las entradas del Registro son *propiedades* de los elementos). Por ejemplo, para crear una clave denominada "_Test" en la subclave CurrentVersion, escriba:</span><span class="sxs-lookup"><span data-stu-id="af42f-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="af42f-116">Cuando escriba una ruta de acceso del Registro, no olvide incluir dos puntos (**:**) en los nombres de unidad de Windows PowerShell, HKLM: y HKCU:.</span><span class="sxs-lookup"><span data-stu-id="af42f-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="af42f-117">Sin esos dos puntos, Windows PowerShell no reconoce el nombre de la unidad en la ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="af42f-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

## <a name="why-registry-values-are-not-items"></a><span data-ttu-id="af42f-118">¿Por qué valores del Registro no son elementos?</span><span class="sxs-lookup"><span data-stu-id="af42f-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="af42f-119">Si usa el cmdlet **Get-ChildItem** para encontrar los elementos en una clave del Registro, nunca verá las entradas del Registro reales ni sus valores.</span><span class="sxs-lookup"><span data-stu-id="af42f-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="af42f-120">Por ejemplo, la clave del Registro **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** suele contener varias entradas del Registro que representan las aplicaciones que se ejecutan cuando el sistema se inicia.</span><span class="sxs-lookup"><span data-stu-id="af42f-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="af42f-121">Sin embargo, si usa **Get-ChildItem** para buscar elementos secundarios en la clave, solamente verá la subclave **OptionalComponents** de la clave:</span><span class="sxs-lookup"><span data-stu-id="af42f-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="af42f-122">Aunque posiblemente sea conveniente tratar las entradas del Registro como elementos, no se puede especificar una ruta de acceso a una entrada del Registro de una manera que garantice que sea única.</span><span class="sxs-lookup"><span data-stu-id="af42f-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="af42f-123">La notación de ruta de acceso no distingue entre la subclave del Registro **Run** y la entrada del Registro **(Default)** en la subclave **Run**.</span><span class="sxs-lookup"><span data-stu-id="af42f-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="af42f-124">Es más, dado que los nombres de las entradas del Registro pueden contener el carácter de barra diagonal inversa (**\\**), si las entradas de Registro fueran elementos, no podría usar la notación de ruta de acceso para distinguir una entrada del Registro llamada **Windows\\CurrentVersion\\Run** de la subclave que se encuentra en esa ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="af42f-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if registry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

## <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="af42f-125">Cambiar el nombre de los elementos existentes (Rename-Item)</span><span class="sxs-lookup"><span data-stu-id="af42f-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="af42f-126">Para cambiar el nombre de un archivo o una carpeta, use el cmdlet **Rename-Item**.</span><span class="sxs-lookup"><span data-stu-id="af42f-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="af42f-127">El siguiente comando cambia el nombre del archivo **file1.txt** a **fileOne.txt**.</span><span class="sxs-lookup"><span data-stu-id="af42f-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="af42f-128">El cmdlet **Rename-Item** puede cambiar el nombre de un archivo o una carpeta, pero no puede mover un elemento.</span><span class="sxs-lookup"><span data-stu-id="af42f-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="af42f-129">El siguiente comando genera un error porque intenta mover el archivo del directorio New.Directory al directorio Temp.</span><span class="sxs-lookup"><span data-stu-id="af42f-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a><span data-ttu-id="af42f-130">Mover elementos (Move-Item)</span><span class="sxs-lookup"><span data-stu-id="af42f-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="af42f-131">Para mover un archivo o una carpeta, use el cmdlet **Move-Item**.</span><span class="sxs-lookup"><span data-stu-id="af42f-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="af42f-132">Por ejemplo, el siguiente comando mueve el directorio New.Directory del directorio C:\\temp a la raíz de la unidad C:.</span><span class="sxs-lookup"><span data-stu-id="af42f-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="af42f-133">Para confirmar que el elemento se ha movido, incluya el parámetro **PassThru** del cmdlet **Move-Item**.</span><span class="sxs-lookup"><span data-stu-id="af42f-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="af42f-134">Sin **Passthru**, el cmdlet **Move-Item** no muestra ningún resultado.</span><span class="sxs-lookup"><span data-stu-id="af42f-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a><span data-ttu-id="af42f-135">Copiar elementos (Copy-Item)</span><span class="sxs-lookup"><span data-stu-id="af42f-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="af42f-136">Si está familiarizado con las operaciones de copia de otros shells, el comportamiento del cmdlet **Copy-Item** de Windows PowerShell le puede parecer inusual.</span><span class="sxs-lookup"><span data-stu-id="af42f-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="af42f-137">Al copiar un elemento de una ubicación en otra, Copy-Item no copia el contenido de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="af42f-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="af42f-138">Por ejemplo, si copia el directorio **New.Directory** de la unidad C: en el directorio C:\\temp, el comando se ejecuta correctamente, pero los archivos del directorio New.Directory no se copian.</span><span class="sxs-lookup"><span data-stu-id="af42f-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="af42f-139">Si muestra el contenido de **C:\\temp\\New.Directory**, verá que no hay archivos:</span><span class="sxs-lookup"><span data-stu-id="af42f-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="af42f-140">¿Por qué el cmdlet **Copy-Item** no copia el contenido en la nueva ubicación?</span><span class="sxs-lookup"><span data-stu-id="af42f-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="af42f-141">El cmdlet **Copy-Item** está diseñado para ser genérico; no sirve única y exclusivamente para copiar archivos y carpetas.</span><span class="sxs-lookup"><span data-stu-id="af42f-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="af42f-142">Además, incluso cuando se copian archivos y carpetas, conviene copiar solo el contenedor y no los elementos que hay en él.</span><span class="sxs-lookup"><span data-stu-id="af42f-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="af42f-143">Para copiar todo el contenido de una carpeta, incluya el parámetro **Recurse** del cmdlet **Copy-Item** en el comando.</span><span class="sxs-lookup"><span data-stu-id="af42f-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="af42f-144">Si ya ha copiado el directorio sin su contenido, agregue el parámetro **Force**, que permite sobrescribir la carpeta vacía.</span><span class="sxs-lookup"><span data-stu-id="af42f-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

## <a name="deleting-items-remove-item"></a><span data-ttu-id="af42f-145">Eliminar elementos (Remove-Item)</span><span class="sxs-lookup"><span data-stu-id="af42f-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="af42f-146">Use el cmdlet **Remove-Item** para eliminar archivos y carpetas.</span><span class="sxs-lookup"><span data-stu-id="af42f-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="af42f-147">Los cmdlets de Windows PowerShell como **Remove-Item**, que pueden realizar cambios importantes e irreversibles, a menudo pedirán confirmación al escribir sus comandos.</span><span class="sxs-lookup"><span data-stu-id="af42f-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="af42f-148">Así, si intenta quitar la carpeta **New.Directory**, se le pedirá que confirme el comando, ya que la carpeta contiene archivos:</span><span class="sxs-lookup"><span data-stu-id="af42f-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="af42f-149">Dado que **Sí** es la respuesta predeterminada, presione la tecla **Entrar** para eliminar la carpeta y sus archivos.</span><span class="sxs-lookup"><span data-stu-id="af42f-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="af42f-150">Para quitar la carpeta sin confirmar, use el parámetro **-Recurse**.</span><span class="sxs-lookup"><span data-stu-id="af42f-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a><span data-ttu-id="af42f-151">Ejecutar elementos (Invoke-Item)</span><span class="sxs-lookup"><span data-stu-id="af42f-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="af42f-152">Windows PowerShell usa el cmdlet **Invoke-Item** para realizar una acción predeterminada relativa a un archivo o una carpeta.</span><span class="sxs-lookup"><span data-stu-id="af42f-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="af42f-153">Esta acción predeterminada viene determinada por el controlador de aplicación predeterminado en el Registro; el efecto es el mismo que si hiciera doble clic en el elemento en el Explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="af42f-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="af42f-154">Por ejemplo, suponga que ejecuta el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="af42f-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="af42f-155">Se abre una ventana del explorador en la ubicación C:\\Windows, básicamente como si hubiera hecho doble clic en la carpeta C:\\Windows.</span><span class="sxs-lookup"><span data-stu-id="af42f-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="af42f-156">Si invoca el archivo **Boot.ini** en un sistema previo a Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="af42f-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="af42f-157">Si el tipo de archivo .ini está asociado con el Bloc de notas, se abrirá en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="af42f-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>
