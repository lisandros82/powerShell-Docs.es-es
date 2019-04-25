---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Cmdlets del catálogo
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057661"
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="a96f9-103">Cmdlets del catálogo</span><span class="sxs-lookup"><span data-stu-id="a96f9-103">Catalog Cmdlets</span></span>

<span data-ttu-id="a96f9-104">Hemos agregado dos nuevos cmdlets en el módulo [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) para generar y validar los archivos de catálogo de Windows.</span><span class="sxs-lookup"><span data-stu-id="a96f9-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="a96f9-105">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a96f9-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="a96f9-106">`New-FileCatalog` crea un archivo de catálogo de Windows para un conjunto de carpetas y archivos.</span><span class="sxs-lookup"><span data-stu-id="a96f9-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="a96f9-107">El archivo de catálogo contiene hashes para todos los archivos de las rutas de acceso especificadas.</span><span class="sxs-lookup"><span data-stu-id="a96f9-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="a96f9-108">Los usuarios pueden distribuir el conjunto de carpetas junto con el correspondiente archivo de catálogo que representa a esas carpetas.</span><span class="sxs-lookup"><span data-stu-id="a96f9-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="a96f9-109">El destinatario del contenido puede usar el archivo de catálogo para validar si se realizaron cambios en las carpetas después de la creación del catálogo.</span><span class="sxs-lookup"><span data-stu-id="a96f9-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="a96f9-110">Se admite la creación de catálogos de las versiones 1 y 2.</span><span class="sxs-lookup"><span data-stu-id="a96f9-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="a96f9-111">La versión 1, utiliza el algoritmo hash SHA1 para crear los hashes de archivo y la versión 2 utiliza SHA256.</span><span class="sxs-lookup"><span data-stu-id="a96f9-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="a96f9-112">La versión 2 del catálogo no es compatible con *Windows Server 2008 R2* y *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="a96f9-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="a96f9-113">Se recomienda utilizar la versión 2 del catálogo si utiliza las plataformas *Windows 8*, *Windows Server 2012* y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="a96f9-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="a96f9-114">Para utilizar este comando en un módulo existente, especifique las variables CatalogFilePath y Path de modo que coincidan con la ubicación del manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="a96f9-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="a96f9-115">En el ejemplo siguiente, el manifiesto del módulo se encuentra en la ruta C:\Program Files\Windows PowerShell\Modules\Pester.</span><span class="sxs-lookup"><span data-stu-id="a96f9-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="a96f9-116">Esto crea el archivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="a96f9-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="a96f9-117">Para comprobar la integridad del archivo de catálogo (Pester.cat en el ejemplo anterior) debe firmarse mediante el cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).</span><span class="sxs-lookup"><span data-stu-id="a96f9-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="a96f9-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a96f9-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="a96f9-119">`Test-FileCatalog` valida el catálogo que representa un conjunto de carpetas.</span><span class="sxs-lookup"><span data-stu-id="a96f9-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="a96f9-120">Este cmdlet compara los valores hash de todos los archivos y de sus rutas de acceso relativas que se encuentran en el archivo de catálogo con los guardados en el disco.</span><span class="sxs-lookup"><span data-stu-id="a96f9-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="a96f9-121">Si se detecta cualquier error de coincidencia entre los hashes y las rutas de acceso de los archivos devuelve el estado `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="a96f9-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="a96f9-122">Los usuarios pueden recuperar toda esta información mediante el modificador `Detailed`.</span><span class="sxs-lookup"><span data-stu-id="a96f9-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="a96f9-123">Se muestra el estado de firma del catálogo en el campo `Signature`, lo que es igual que llamar al cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) en el archivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="a96f9-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="a96f9-124">El usuario también puede omitir cualquier archivo durante la validación mediante el parámetro `FilesToSkip`.</span><span class="sxs-lookup"><span data-stu-id="a96f9-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
