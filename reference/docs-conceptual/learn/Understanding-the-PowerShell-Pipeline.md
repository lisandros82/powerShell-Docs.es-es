---
ms.date: 08/23/2018
keywords: powershell, cmdlet
title: Descripción de los módulos de PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: fc7c7f57bdce458185a0f5bdb8bc1fbbd81d0d61
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402273"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="d0440-103">Descripción de las canalizaciones</span><span class="sxs-lookup"><span data-stu-id="d0440-103">Understanding pipelines</span></span>

<span data-ttu-id="d0440-104">Las canalizaciones actúan como una serie de segmentos de canalización conectados.</span><span class="sxs-lookup"><span data-stu-id="d0440-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="d0440-105">Los elementos que se mueven por la canalización pasan a través de cada segmento.</span><span class="sxs-lookup"><span data-stu-id="d0440-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="d0440-106">Para crear una canalización en PowerShell, se conectan comandos con el operador de canalización "|".</span><span class="sxs-lookup"><span data-stu-id="d0440-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="d0440-107">La salida de cada comando se usa como entrada para el siguiente.</span><span class="sxs-lookup"><span data-stu-id="d0440-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="d0440-108">La notación utilizada para las canalizaciones es similar a la notación utilizada en otros shells.</span><span class="sxs-lookup"><span data-stu-id="d0440-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="d0440-109">A primera vista, puede que no sea evidente en qué se diferencian las canalizaciones en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0440-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="d0440-110">Aunque se ve texto en la pantalla, PowerShell canaliza objetos, no texto, entre los comandos.</span><span class="sxs-lookup"><span data-stu-id="d0440-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="d0440-111">Canalización de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0440-111">The PowerShell pipeline</span></span>

<span data-ttu-id="d0440-112">Las canalizaciones son sin duda el concepto más valioso usado en las interfaces de línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="d0440-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="d0440-113">Cuando se usan correctamente, las canalizaciones reducen el esfuerzo de usar comandos complejos y facilitan la visualización del flujo de trabajo de los comandos.</span><span class="sxs-lookup"><span data-stu-id="d0440-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="d0440-114">Cada comando de una canalización (denominado un elemento de canalización) pasa la salida al siguiente comando de la canalización elemento por elemento.</span><span class="sxs-lookup"><span data-stu-id="d0440-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="d0440-115">Los comandos no tienen que controlar más de un elemento a la vez.</span><span class="sxs-lookup"><span data-stu-id="d0440-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="d0440-116">El resultado es un menor consumo de recursos y la capacidad de empezar a obtener la salida inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="d0440-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="d0440-117">Por ejemplo, si usa el cmdlet `Out-Host` para forzar una presentación página por página de la salida de otro comando, la salida tiene el aspecto del texto normal que se muestra en la pantalla, dividida en páginas:</span><span class="sxs-lookup"><span data-stu-id="d0440-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="d0440-118">La paginación también reduce la utilización de la CPU porque el procesamiento se transfiere al cmdlet `Out-Host` cuando tiene una página completa lista para mostrar.</span><span class="sxs-lookup"><span data-stu-id="d0440-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="d0440-119">Los cmdlets que lo preceden en la canalización pausan la ejecución hasta que la siguiente página de salida está disponible.</span><span class="sxs-lookup"><span data-stu-id="d0440-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="d0440-120">Puede ver la diferencia si usa el Administrador de tareas de Windows para supervisar el uso de la CPU y la memoria de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0440-120">You can see the difference Windows Task Manager to monitor CPU and memory used by PowerShell.</span></span> <span data-ttu-id="d0440-121">Ejecute el siguiente comando: `Get-ChildItem C:\Windows -Recurse`.</span><span class="sxs-lookup"><span data-stu-id="d0440-121">Run the following command: `Get-ChildItem C:\Windows -Recurse`.</span></span> <span data-ttu-id="d0440-122">Compare el uso de la CPU y la memoria con este comando: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.</span><span class="sxs-lookup"><span data-stu-id="d0440-122">Compare the CPU and memory usage to this command: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.</span></span>

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="d0440-123">Objetos de la canalización</span><span class="sxs-lookup"><span data-stu-id="d0440-123">Objects in the pipeline</span></span>

<span data-ttu-id="d0440-124">Cuando se ejecuta un cmdlet en PowerShell, se verá la salida del texto debido a la necesidad de representar objetos como texto en una ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="d0440-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="d0440-125">Es posible que la salida de texto no muestre todas las propiedades del objeto que se está emitiendo.</span><span class="sxs-lookup"><span data-stu-id="d0440-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="d0440-126">Por ejemplo, tenga en cuenta el cmdlet `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="d0440-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="d0440-127">Si ejecuta `Get-Location` mientras la ubicación actual es el directorio raíz de la unidad C, verá la siguiente salida:</span><span class="sxs-lookup"><span data-stu-id="d0440-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="d0440-128">La salida de texto es un resumen de la información y no una representación completa del objeto devuelto por `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="d0440-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="d0440-129">El encabezado de la salida se agrega mediante el proceso que formatea los datos para su visualización en pantalla.</span><span class="sxs-lookup"><span data-stu-id="d0440-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="d0440-130">Al canalizar la salida al cmdlet `Get-Member`, se obtiene información sobre el objeto devuelto por `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="d0440-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
PS> Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="d0440-131">`Get-Location` devuelve un objeto **PathInfo** que contiene la ruta de acceso actual y otra información.</span><span class="sxs-lookup"><span data-stu-id="d0440-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>
