---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Nuevos escenarios y características de WMF 5.1
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085455"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="a1b43-103">Nuevos escenarios y características de WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a1b43-103">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="a1b43-104">Nota: Esta información es preliminar y está sujeta a cambios.</span><span class="sxs-lookup"><span data-stu-id="a1b43-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="a1b43-105">Ediciones de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1b43-105">PowerShell Editions</span></span>

<span data-ttu-id="a1b43-106">A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.</span><span class="sxs-lookup"><span data-stu-id="a1b43-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="a1b43-107">**Desktop Edition:** basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="a1b43-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="a1b43-108">**Core Edition:** basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Nano Server y Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="a1b43-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="a1b43-109">**Más información sobre el uso de las ediciones de PowerShell**</span><span class="sxs-lookup"><span data-stu-id="a1b43-109">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="a1b43-110">Determinación de la edición de ejecución de PowerShell con $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="a1b43-110">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="a1b43-111">Filtrado de los resultados de Get-Module mediante CompatiblePSEditions con el parámetro PSEdition</span><span class="sxs-lookup"><span data-stu-id="a1b43-111">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="a1b43-112">Impedir la ejecución de scripts, a menos que se ejecuten en una edición compatible de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1b43-112">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="a1b43-113">Declarar la compatibilidad de un módulo con versiones específicas de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1b43-113">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a><span data-ttu-id="a1b43-114">Cmdlets del catálogo</span><span class="sxs-lookup"><span data-stu-id="a1b43-114">Catalog Cmdlets</span></span>

<span data-ttu-id="a1b43-115">Hemos agregado dos nuevos cmdlets en el módulo [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) para generar y validar los archivos de catálogo de Windows.</span><span class="sxs-lookup"><span data-stu-id="a1b43-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) module; these generate and validate Windows catalog files.</span></span>

### <a name="new-filecatalog"></a><span data-ttu-id="a1b43-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a1b43-116">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="a1b43-117">New-FileCatalog crea un archivo de catálogo de Windows para un conjunto de carpetas y archivos.</span><span class="sxs-lookup"><span data-stu-id="a1b43-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="a1b43-118">Este archivo de catálogo contiene hashes para todos los archivos de las rutas de acceso especificadas.</span><span class="sxs-lookup"><span data-stu-id="a1b43-118">This catalog file contains hashes for all files in specified paths.</span></span>
<span data-ttu-id="a1b43-119">Los usuarios pueden distribuir el conjunto de carpetas junto con el correspondiente archivo de catálogo que representa a esas carpetas.</span><span class="sxs-lookup"><span data-stu-id="a1b43-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span>
<span data-ttu-id="a1b43-120">Esta información es útil para validar si se han realizado cambios en las carpetas desde que se creó el catálogo.</span><span class="sxs-lookup"><span data-stu-id="a1b43-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="a1b43-121">Se admiten las versiones 1 y 2 del catálogo.</span><span class="sxs-lookup"><span data-stu-id="a1b43-121">Catalog versions 1 and 2 are supported.</span></span>
<span data-ttu-id="a1b43-122">La versión 1, utiliza el algoritmo hash SHA1 para crear los hashes de archivo y la versión 2 utiliza SHA256.</span><span class="sxs-lookup"><span data-stu-id="a1b43-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span>
<span data-ttu-id="a1b43-123">La versión 2 del catálogo no es compatible con *Windows Server 2008 R2* o *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="a1b43-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span>
<span data-ttu-id="a1b43-124">Deberá utilizar la versión 2 del catálogo en *Windows 8*, *Windows Server 2012* y sistemas operativos posteriores.</span><span class="sxs-lookup"><span data-stu-id="a1b43-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="a1b43-125">Esto crea el archivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="a1b43-125">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="a1b43-126">Para comprobar la integridad del archivo de catálogo (Pester.cat en el ejemplo anterior), fírmelo mediante el cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature).</span><span class="sxs-lookup"><span data-stu-id="a1b43-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.</span></span>

### <a name="test-filecatalog"></a><span data-ttu-id="a1b43-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a1b43-127">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="a1b43-128">Test-FileCatalog valida el catálogo que representa un conjunto de carpetas.</span><span class="sxs-lookup"><span data-stu-id="a1b43-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="a1b43-129">Este cmdlet compara los hashes y rutas de acceso relativas de los archivos que se encuentran en el *catálogo* con los de los que están en el *disco*.</span><span class="sxs-lookup"><span data-stu-id="a1b43-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span>
<span data-ttu-id="a1b43-130">Si se detecta cualquier error de coincidencia entre los hashes y las rutas de acceso de los archivos devuelve el estado *ValidationFailed*.</span><span class="sxs-lookup"><span data-stu-id="a1b43-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span>
<span data-ttu-id="a1b43-131">Los usuarios pueden recuperar toda esta información mediante el parámetro *-Detailed*.</span><span class="sxs-lookup"><span data-stu-id="a1b43-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span>
<span data-ttu-id="a1b43-132">También muestra el estado de firma del catálogo en la propiedad *Signature*, lo que equivale a llamar al cmdlet [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) en el archivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="a1b43-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet on the catalog file.</span></span>
<span data-ttu-id="a1b43-133">El usuario también puede omitir cualquier archivo durante la validación mediante el parámetro *FilesToSkip -*.</span><span class="sxs-lookup"><span data-stu-id="a1b43-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

## <a name="module-analysis-cache"></a><span data-ttu-id="a1b43-134">Caché de análisis de módulo</span><span class="sxs-lookup"><span data-stu-id="a1b43-134">Module Analysis Cache</span></span>

<span data-ttu-id="a1b43-135">A partir de WMF 5.1, PowerShell proporciona control sobre el archivo que se utiliza para almacenar en la caché los datos acerca de un módulo, como los comandos que exporta.</span><span class="sxs-lookup"><span data-stu-id="a1b43-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="a1b43-136">De manera predeterminada, esta caché se almacena en el archivo `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="a1b43-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="a1b43-137">La caché normalmente se lee en el inicio al buscar un comando y se escribe en un subproceso en segundo plano después de que se importa un módulo.</span><span class="sxs-lookup"><span data-stu-id="a1b43-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="a1b43-138">Para cambiar la ubicación predeterminada de la memoria caché, establezca la variable de entorno `$env:PSModuleAnalysisCachePath` antes de iniciar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a1b43-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span>
<span data-ttu-id="a1b43-139">Los cambios en esta variable de entorno solo afectarán a los procesos secundarios.</span><span class="sxs-lookup"><span data-stu-id="a1b43-139">Changes to this environment variable will only affect children processes.</span></span>
<span data-ttu-id="a1b43-140">El valor debe asignar un nombre a una ruta de acceso completa (nombre de archivo incluido) en la que PowerShell tiene permiso para crear y escribir archivos.</span><span class="sxs-lookup"><span data-stu-id="a1b43-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>
<span data-ttu-id="a1b43-141">Para deshabilitar la caché del archivo, establezca este valor en una ubicación no válida, como por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a1b43-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="a1b43-142">Esto establece la ruta de acceso en un dispositivo no válido.</span><span class="sxs-lookup"><span data-stu-id="a1b43-142">This sets the path to an invalid device.</span></span>
<span data-ttu-id="a1b43-143">Si PowerShell no puede escribir en la ruta de acceso, no se devuelve ningún error, pero se pueden ver informes del error a través de un seguimiento:</span><span class="sxs-lookup"><span data-stu-id="a1b43-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="a1b43-144">Al escribir en la caché, PowerShell buscará si hay módulos que no existen, con el fin de evitar que la caché sea demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="a1b43-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="a1b43-145">A veces no interesa que se realicen estas comprobaciones, en cuyo caso se pueden desactivar estableciendo:</span><span class="sxs-lookup"><span data-stu-id="a1b43-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="a1b43-146">El establecimiento de esta variable de entorno surtirá efecto de inmediato en el proceso actual.</span><span class="sxs-lookup"><span data-stu-id="a1b43-146">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="a1b43-147">Especificación de la versión del módulo</span><span class="sxs-lookup"><span data-stu-id="a1b43-147">Specifying module version</span></span>

<span data-ttu-id="a1b43-148">En WMF 5.1, `using module` se comporta de la misma forma que las restantes construcciones relacionadas con módulos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a1b43-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="a1b43-149">Antes no había forma de especificar una versión concreta del módulo; si había varias versiones, aparecía un error.</span><span class="sxs-lookup"><span data-stu-id="a1b43-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="a1b43-150">En WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="a1b43-150">In WMF 5.1:</span></span>

- <span data-ttu-id="a1b43-151">Puede usar el [constructor ModuleSpecification (tabla hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="a1b43-151">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="a1b43-152">Esta tabla hash tiene el mismo formato que `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="a1b43-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="a1b43-153">**Ejemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="a1b43-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="a1b43-154">Si hay varias versiones del módulo de multiplicar, PowerShell usa la **misma lógica de resolución** que `Import-Module` y no devuelve ningún error (el mismo comportamiento que `Import-Module` y `Import-DscResource`).</span><span class="sxs-lookup"><span data-stu-id="a1b43-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="a1b43-155">Mejoras en Pester</span><span class="sxs-lookup"><span data-stu-id="a1b43-155">Improvements to Pester</span></span>

<span data-ttu-id="a1b43-156">En WMF 5.1, se ha actualizado la versión de Pester que se incluye con PowerShell de la versión 3.3.5 a la 3.4.0, con la adición de confirmación https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, lo que permite un mejor comportamiento de Pester en Nano Server.</span><span class="sxs-lookup"><span data-stu-id="a1b43-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="a1b43-157">Para consultar los cambios de la versión 3.3.5 a la 3.4.0, vea el archivo ChangeLog.md en: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="a1b43-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>
