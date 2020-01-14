---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Trabajar con claves del Registro
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736852"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="55e06-103">Trabajar con claves del Registro</span><span class="sxs-lookup"><span data-stu-id="55e06-103">Working with Registry Keys</span></span>

<span data-ttu-id="55e06-104">Dado que las claves del Registro son elementos en unidades de PowerShell, trabajar con ellas es muy similar a trabajar con archivos y carpetas.</span><span class="sxs-lookup"><span data-stu-id="55e06-104">Because registry keys are items on PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="55e06-105">Una diferencia fundamental es que todos los elementos en una unidad de PowerShell basada en el Registro es un contenedor, como una carpeta en una unidad del sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="55e06-105">One critical difference is that every item on a registry-based PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="55e06-106">Sin embargo, las entradas del Registro y sus valores asociados son propiedades de los elementos, no elementos distintos.</span><span class="sxs-lookup"><span data-stu-id="55e06-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="55e06-107">Enumerar a todas las subclaves de una clave del Registro</span><span class="sxs-lookup"><span data-stu-id="55e06-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="55e06-108">Puede mostrar todos los elementos directamente dentro de una clave del Registro, para lo que debe usar `Get-ChildItem`.</span><span class="sxs-lookup"><span data-stu-id="55e06-108">You can show all items directly within a registry key by using `Get-ChildItem`.</span></span> <span data-ttu-id="55e06-109">Agregue el parámetro **Force** opcional para mostrar elementos ocultos o del sistema.</span><span class="sxs-lookup"><span data-stu-id="55e06-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="55e06-110">Por ejemplo, este comando muestra los elementos directamente en la unidad `HKCU:` de PowerShell que se corresponde con el subárbol `HKEY_CURRENT_USER` del Registro:</span><span class="sxs-lookup"><span data-stu-id="55e06-110">For example, this command displays the items directly within PowerShell drive `HKCU:`, which corresponds to the `HKEY_CURRENT_USER` registry hive:</span></span>

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

<span data-ttu-id="55e06-111">Estas son las claves de nivel superior visibles en `HKEY_CURRENT_USER` en el Editor del Registro (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="55e06-111">These are the top-level keys visible under `HKEY_CURRENT_USER` in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="55e06-112">Para especificar esta ruta de acceso del Registro también puede especificar el nombre del proveedor del Registro, seguido de `::`.</span><span class="sxs-lookup"><span data-stu-id="55e06-112">You can also specify this registry path by specifying the registry provider's name, followed by `::`.</span></span> <span data-ttu-id="55e06-113">El nombre completo del proveedor del registro es `Microsoft.PowerShell.Core\Registry`, pero se puede acortar a simplemente `Registry`.</span><span class="sxs-lookup"><span data-stu-id="55e06-113">The registry provider's full name is `Microsoft.PowerShell.Core\Registry`, but this can be shortened to just `Registry`.</span></span> <span data-ttu-id="55e06-114">Cualquiera de los siguientes comandos enumerará el contenido directamente en `HKCU:`.</span><span class="sxs-lookup"><span data-stu-id="55e06-114">Any of the following commands will list the contents directly under `HKCU:`.</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="55e06-115">Estos comandos muestran solo los elementos contenidos directamente, lo que se parece a usar `DIR` en **Cmd.exe** o `ls` en un shell de UNIX.</span><span class="sxs-lookup"><span data-stu-id="55e06-115">These commands list only the directly contained items, much like using `DIR` in **Cmd.exe** or `ls` in a UNIX shell.</span></span> <span data-ttu-id="55e06-116">Para mostrar los elementos contenidos, debe especificar el parámetro **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="55e06-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="55e06-117">Para enumerar todas las claves del Registro en `HKCU:`, use el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="55e06-117">To list all registry keys in `HKCU:`, use the following command.</span></span>

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

<span data-ttu-id="55e06-118">`Get-ChildItem` puede realizar funcionalidades de filtrado complejas a través de sus parámetros **Path**, **Filter**, **Include** y **Exclude**, pero dichos parámetros suelen basarse solo en el nombre.</span><span class="sxs-lookup"><span data-stu-id="55e06-118">`Get-ChildItem` can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="55e06-119">Con el cmdlet `Where-Object` puede realizar un filtrado complejo basado en otras propiedades de los elementos.</span><span class="sxs-lookup"><span data-stu-id="55e06-119">You can perform complex filtering based on other properties of items by using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="55e06-120">El siguiente comando busca en `HKCU:\Software` todas las claves que no tengan más de una subclave y que tengan exactamente cuatro valores:</span><span class="sxs-lookup"><span data-stu-id="55e06-120">The following command finds all keys within `HKCU:\Software` that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="55e06-121">Copiar claves</span><span class="sxs-lookup"><span data-stu-id="55e06-121">Copying Keys</span></span>

<span data-ttu-id="55e06-122">La copia se realiza con `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="55e06-122">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="55e06-123">En el ejemplo siguiente se copia la subclave `CurrentVersion` de `HKLM:\SOFTWARE\Microsoft\Windows\` y todas sus propiedades en `HKCU:\`.</span><span class="sxs-lookup"><span data-stu-id="55e06-123">The following example copies the `CurrentVersion` subkey of `HKLM:\SOFTWARE\Microsoft\Windows\` and all of its properties to `HKCU:\`.</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

<span data-ttu-id="55e06-124">Si examina esta nueva clave en el Editor del Registro o mediante `Get-ChildItem`, observará que no tiene copias de las subclaves contenidas en la nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="55e06-124">If you examine this new key in the registry editor or by using `Get-ChildItem`, you notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="55e06-125">Para copiar todo el contenido de un contenedor, debe especificar el parámetro **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="55e06-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="55e06-126">Para hacer que el comando de copia anterior sea recursivo, debe usar este comando:</span><span class="sxs-lookup"><span data-stu-id="55e06-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

<span data-ttu-id="55e06-127">Puede seguir usando otras herramientas que tiene a su disposición para realizar copias del sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="55e06-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="55e06-128">Todas las herramientas de edición del Registro, incluidas **reg.exe**, **regini.exe**, **regedit.exe** y los objetos COM que admiten la edición del Registro, como **WScript.Shell** y la clase **StdRegProv** de WMI, puede usarse desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="55e06-128">Any registry editing tools—including **reg.exe**, **regini.exe**, **regedit.exe**, and COM objects that support registry editing, such as **WScript.Shell** and WMI's **StdRegProv** class can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="55e06-129">Crear claves</span><span class="sxs-lookup"><span data-stu-id="55e06-129">Creating Keys</span></span>

<span data-ttu-id="55e06-130">Crear nuevas claves en el Registro es más sencillo que crear un nuevo elemento en un sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="55e06-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="55e06-131">Dado que todas las claves del Registro son contenedores, no es necesario especificar el tipo de elemento; solo tiene que proporcionar una ruta de acceso explícita, como:</span><span class="sxs-lookup"><span data-stu-id="55e06-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

<span data-ttu-id="55e06-132">También puede usar una ruta de acceso basada en el proveedor para especificar una clave:</span><span class="sxs-lookup"><span data-stu-id="55e06-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="55e06-133">Eliminar claves</span><span class="sxs-lookup"><span data-stu-id="55e06-133">Deleting Keys</span></span>

<span data-ttu-id="55e06-134">El proceso de eliminación de elementos es básicamente igual para todos los proveedores.</span><span class="sxs-lookup"><span data-stu-id="55e06-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="55e06-135">Los siguientes comandos quitarán elementos de forma automática:</span><span class="sxs-lookup"><span data-stu-id="55e06-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="55e06-136">Quitar todas las claves bajo una clave específica</span><span class="sxs-lookup"><span data-stu-id="55e06-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="55e06-137">Los elementos contenidos se pueden quitar mediante `Remove-Item`, pero se pedirá que se confirme la eliminación si el elemento contiene algo más.</span><span class="sxs-lookup"><span data-stu-id="55e06-137">You can remove contained items by using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="55e06-138">Por ejemplo, si se intenta eliminar la subclave `HKCU:\CurrentVersion` creada, se muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="55e06-138">For example, if we attempt to delete the `HKCU:\CurrentVersion` subkey we created, we see this:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="55e06-139">Para eliminar los elementos contenidos sin preguntar, especifique el parámetro **Recurse**:</span><span class="sxs-lookup"><span data-stu-id="55e06-139">To delete contained items without prompting, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="55e06-140">Si quiere quitar todos los elementos de `HKCU:\CurrentVersion`, pero no del `HKCU:\CurrentVersion` mismo, podría usar en su lugar:</span><span class="sxs-lookup"><span data-stu-id="55e06-140">If you wanted to remove all items within `HKCU:\CurrentVersion` but not `HKCU:\CurrentVersion` itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
