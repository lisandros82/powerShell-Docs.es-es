---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 0c450d765531c18c0b73c5c64262e9895f92068a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="archive-cmdlets"></a><span data-ttu-id="69195-102">Cmdlets Archive</span><span class="sxs-lookup"><span data-stu-id="69195-102">Archive cmdlets</span></span>

<span data-ttu-id="69195-103">Dos nuevos cmdlets, **Compress-Archive** y **Expand-Archive**, permiten comprimir y expandir archivos ZIP.</span><span class="sxs-lookup"><span data-stu-id="69195-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="69195-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="69195-104">Compress-Archive</span></span>
<span data-ttu-id="69195-105">El cmdlet **Compress-Archive** crea un nuevo archivo de almacenamiento a partir de los archivos especificados.</span><span class="sxs-lookup"><span data-stu-id="69195-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="69195-106">Un archivo de almacenamiento permite empaquetar varios archivos y, opcionalmente, comprimirlos en un único archivo para facilitar la manipulación y el almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="69195-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="69195-107">Un archivo de almacenamiento se puede comprimir mediante un algoritmo de compresión especificado en el parámetro **-CompressionLevel**.</span><span class="sxs-lookup"><span data-stu-id="69195-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="69195-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="69195-108">Expand-Archive</span></span>
<span data-ttu-id="69195-109">El cmdlet **Expand-Archive** extrae los archivos de un archivo de almacenamiento especificado.</span><span class="sxs-lookup"><span data-stu-id="69195-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="69195-110">Un archivo de almacenamiento permite empaquetar varios archivos y, opcionalmente, comprimirlos en un único archivo para facilitar la manipulación y el almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="69195-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```