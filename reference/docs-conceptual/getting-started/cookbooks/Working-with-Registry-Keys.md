---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Trabajar con claves del Registro
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951705"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="38953-103">Trabajar con claves del Registro</span><span class="sxs-lookup"><span data-stu-id="38953-103">Working with Registry Keys</span></span>

<span data-ttu-id="38953-104">Dado que las claves del Registro son elementos en unidades de Windows PowerShell, trabajar con ellas es muy similar a trabajar con archivos y carpetas.</span><span class="sxs-lookup"><span data-stu-id="38953-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="38953-105">Una diferencia fundamental es que todos los elementos en una unidad de Windows PowerShell basada en el Registro es un contenedor, como una carpeta en una unidad del sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="38953-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="38953-106">Sin embargo, las entradas del Registro y sus valores asociados son propiedades de los elementos, no elementos distintos.</span><span class="sxs-lookup"><span data-stu-id="38953-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

### <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="38953-107">Enumerar a todas las subclaves de una clave del Registro</span><span class="sxs-lookup"><span data-stu-id="38953-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="38953-108">Puede mostrar todos los elementos directamente dentro de una clave del Registro mediante **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="38953-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="38953-109">Agregue el parámetro **Force** opcional para mostrar elementos ocultos o del sistema.</span><span class="sxs-lookup"><span data-stu-id="38953-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="38953-110">Por ejemplo, este comando muestra los elementos directamente en la unidad HKCU: de Windows PowerShell, que se corresponde con el subárbol del Registro HKEY_CURRENT_USER:</span><span class="sxs-lookup"><span data-stu-id="38953-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="38953-111">Estas son las claves de nivel superior visibles en HKEY_CURRENT_USER en el Editor del Registro (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="38953-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="38953-112">Para especificar esta ruta de acceso del Registro también puede especificar el nombre del proveedor del Registro, seguido de "**::**".</span><span class="sxs-lookup"><span data-stu-id="38953-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="38953-113">El nombre completo del proveedor del Registro es **Microsoft.PowerShell.Core\\Registry**, pero se puede abreviar a **Registry**.</span><span class="sxs-lookup"><span data-stu-id="38953-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="38953-114">Cualquiera de los siguientes comandos enumerará el contenido directamente en HKCU:</span><span class="sxs-lookup"><span data-stu-id="38953-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="38953-115">Estos comandos muestran solo los elementos contenidos directamente, lo que se parece a usar el comando **DIR** de Cmd.exe o **ls** en un shell de UNIX.</span><span class="sxs-lookup"><span data-stu-id="38953-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="38953-116">Para mostrar los elementos contenidos, debe especificar el parámetro **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="38953-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="38953-117">Para enumerar todas las claves del Registro en HKCU, use el comando siguiente (esta operación puede tardar una gran cantidad de tiempo):</span><span class="sxs-lookup"><span data-stu-id="38953-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="38953-118">**Get-ChildItem** puede realizar funciones complejas de filtrado a través de sus parámetros **Path**, **Filter**, **Include** y **Exclude**, pero estos parámetros suelen basarse solo en el nombre.</span><span class="sxs-lookup"><span data-stu-id="38953-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="38953-119">Puede realizar un filtrado complejo basado en otras propiedades de elementos mediante el cmdlet **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="38953-119">You can perform complex filtering based on other properties of items by using the **Where-Object** cmdlet.</span></span> <span data-ttu-id="38953-120">El siguiente comando busca en HKCU:\\Software todas las claves que no tengan más de una subclave y que tengan exactamente cuatro valores:</span><span class="sxs-lookup"><span data-stu-id="38953-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a><span data-ttu-id="38953-121">Copiar claves</span><span class="sxs-lookup"><span data-stu-id="38953-121">Copying Keys</span></span>

<span data-ttu-id="38953-122">La copia se realiza con **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="38953-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="38953-123">El siguiente comando copia HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion y todas sus propiedades en HKCU:\\, y crea una nueva clave denominada "CurrentVersion":</span><span class="sxs-lookup"><span data-stu-id="38953-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="38953-124">Si examina esta nueva clave en el Editor del Registro o mediante **Get-ChildItem**, observará que no tiene copias de las subclaves contenidas en la nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="38953-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="38953-125">Para copiar todo el contenido de un contenedor, debe especificar el parámetro **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="38953-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="38953-126">Para hacer que el comando de copia anterior sea recursivo, debe usar este comando:</span><span class="sxs-lookup"><span data-stu-id="38953-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="38953-127">Puede seguir usando otras herramientas que tiene a su disposición para realizar copias del sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="38953-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="38953-128">Todas las herramientas de edición del Registro, incluidas reg.exe, regini.exe y regedit.exe, y los objetos COM que admiten la edición del Registro (como WScript.Shell y la clase WMI StdRegProv) pueden usarse desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38953-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

### <a name="creating-keys"></a><span data-ttu-id="38953-129">Crear claves</span><span class="sxs-lookup"><span data-stu-id="38953-129">Creating Keys</span></span>

<span data-ttu-id="38953-130">Crear nuevas claves en el Registro es más sencillo que crear un nuevo elemento en un sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="38953-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="38953-131">Dado que todas las claves del Registro son contenedores, no es necesario especificar el tipo de elemento; solo tiene que proporcionar una ruta de acceso explícita, como:</span><span class="sxs-lookup"><span data-stu-id="38953-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="38953-132">También puede usar una ruta de acceso basada en el proveedor para especificar una clave:</span><span class="sxs-lookup"><span data-stu-id="38953-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a><span data-ttu-id="38953-133">Eliminar claves</span><span class="sxs-lookup"><span data-stu-id="38953-133">Deleting Keys</span></span>

<span data-ttu-id="38953-134">El proceso de eliminación de elementos es básicamente igual para todos los proveedores.</span><span class="sxs-lookup"><span data-stu-id="38953-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="38953-135">Los siguientes comandos quitarán elementos de forma automática:</span><span class="sxs-lookup"><span data-stu-id="38953-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="38953-136">Quitar todas las claves bajo una clave específica</span><span class="sxs-lookup"><span data-stu-id="38953-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="38953-137">Puede quitar los elementos contenidos mediante **Remove-Item**, pero se le pedirá que confirme la eliminación si el elemento contiene algo más.</span><span class="sxs-lookup"><span data-stu-id="38953-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="38953-138">Por ejemplo, si se intenta eliminar la subclave HKCU:\\CurrentVersion creada, se muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="38953-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="38953-139">Para eliminar los elementos contenidos sin preguntar, especifique el parámetro **-Recurse**:</span><span class="sxs-lookup"><span data-stu-id="38953-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="38953-140">Si deseara quitar todos los elementos de HKCU:\\CurrentVersion, pero no el propio HKCU:\\CurrentVersion, podría usar:</span><span class="sxs-lookup"><span data-stu-id="38953-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```