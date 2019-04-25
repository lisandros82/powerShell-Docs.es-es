---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Mejoras del motor de PowerShell en WMF 5.1
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055571"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="7a0ed-103">Mejoras del motor de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a0ed-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="7a0ed-104">En WMF 5.1, se han implementado las siguientes mejoras al motor central de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7a0ed-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="7a0ed-105">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="7a0ed-105">Performance</span></span>

<span data-ttu-id="7a0ed-106">El rendimiento ha mejorado en algunas áreas importantes:</span><span class="sxs-lookup"><span data-stu-id="7a0ed-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="7a0ed-107">Inicio</span><span class="sxs-lookup"><span data-stu-id="7a0ed-107">Startup</span></span>
- <span data-ttu-id="7a0ed-108">La canalización a cmdlets como `ForEach-Object` y `Where-Object` es aproximadamente un 50 % más rápida</span><span class="sxs-lookup"><span data-stu-id="7a0ed-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="7a0ed-109">Algunas mejoras del ejemplo (los resultados pueden variar en función del hardware):</span><span class="sxs-lookup"><span data-stu-id="7a0ed-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="7a0ed-110">Escenario</span><span class="sxs-lookup"><span data-stu-id="7a0ed-110">Scenario</span></span> | <span data-ttu-id="7a0ed-111">Tiempo de 5.0 (ms)</span><span class="sxs-lookup"><span data-stu-id="7a0ed-111">5.0 Time (ms)</span></span> | <span data-ttu-id="7a0ed-112">Tiempo de 5.1 (ms)</span><span class="sxs-lookup"><span data-stu-id="7a0ed-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="7a0ed-113">900</span><span class="sxs-lookup"><span data-stu-id="7a0ed-113">900</span></span> | <span data-ttu-id="7a0ed-114">250</span><span class="sxs-lookup"><span data-stu-id="7a0ed-114">250</span></span> |
| <span data-ttu-id="7a0ed-115">Primera ejecución de PowerShell: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="7a0ed-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="7a0ed-116">30000</span><span class="sxs-lookup"><span data-stu-id="7a0ed-116">30000</span></span> | <span data-ttu-id="7a0ed-117">13000</span><span class="sxs-lookup"><span data-stu-id="7a0ed-117">13000</span></span> |
| <span data-ttu-id="7a0ed-118">Caché de análisis de comandos integrada: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="7a0ed-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="7a0ed-119">7000</span><span class="sxs-lookup"><span data-stu-id="7a0ed-119">7000</span></span> | <span data-ttu-id="7a0ed-120">520</span><span class="sxs-lookup"><span data-stu-id="7a0ed-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="7a0ed-121">1400</span><span class="sxs-lookup"><span data-stu-id="7a0ed-121">1400</span></span> | <span data-ttu-id="7a0ed-122">750</span><span class="sxs-lookup"><span data-stu-id="7a0ed-122">750</span></span> |

> [!Note]
> <span data-ttu-id="7a0ed-123">Un cambio relacionado con el inicio puede afectar a algunos escenarios no compatibles.</span><span class="sxs-lookup"><span data-stu-id="7a0ed-123">One change related to startup might impact some unsupported scenarios.</span></span>
> <span data-ttu-id="7a0ed-124">PowerShell ya no lee los archivos `$pshome\*.ps1xml`: estos archivos se han convertido en C# para evitar la sobrecarga de archivos y de la CPU que supone procesar los archivos XML.</span><span class="sxs-lookup"><span data-stu-id="7a0ed-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span>
> <span data-ttu-id="7a0ed-125">Los archivos aún existen para proporcionar compatibilidad con V2 en paralelo, por lo que si se cambia el contenido de los archivos, esto no tendrá ningún efecto en V5, solo en V2.</span><span class="sxs-lookup"><span data-stu-id="7a0ed-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span>
> <span data-ttu-id="7a0ed-126">Tenga en cuenta que el cambio del contenido de estos archivos nunca ha sido un escenario compatible.</span><span class="sxs-lookup"><span data-stu-id="7a0ed-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="7a0ed-127">Otro cambio visible es la forma en que PowerShell almacena en caché tanto comandos exportados como otra información de los módulos instalados en un sistema.</span><span class="sxs-lookup"><span data-stu-id="7a0ed-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span>
<span data-ttu-id="7a0ed-128">Antes, la memoria caché se almacenaba en el directorio `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="7a0ed-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span>
<span data-ttu-id="7a0ed-129">En WMF 5.1, la memoria caché es un único archivo `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="7a0ed-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="7a0ed-130">Para obtener más información, vea [Caché de análisis de módulo](scenarios-features.md#module-analysis-cache).</span><span class="sxs-lookup"><span data-stu-id="7a0ed-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>