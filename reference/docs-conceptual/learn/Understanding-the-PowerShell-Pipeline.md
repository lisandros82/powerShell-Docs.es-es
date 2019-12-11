---
ms.date: 08/23/2018
keywords: powershell, cmdlet
title: Descripción de los módulos de PowerShell
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030381"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="ad93c-103">Descripción de las canalizaciones</span><span class="sxs-lookup"><span data-stu-id="ad93c-103">Understanding pipelines</span></span>

<span data-ttu-id="ad93c-104">Las canalizaciones actúan como una serie de segmentos de canalización conectados.</span><span class="sxs-lookup"><span data-stu-id="ad93c-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="ad93c-105">Los elementos que se mueven por la canalización pasan a través de cada segmento.</span><span class="sxs-lookup"><span data-stu-id="ad93c-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="ad93c-106">Para crear una canalización en PowerShell, se conectan comandos con el operador de canalización "|".</span><span class="sxs-lookup"><span data-stu-id="ad93c-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="ad93c-107">La salida de cada comando se usa como entrada para el siguiente.</span><span class="sxs-lookup"><span data-stu-id="ad93c-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="ad93c-108">La notación utilizada para las canalizaciones es similar a la notación utilizada en otros shells.</span><span class="sxs-lookup"><span data-stu-id="ad93c-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="ad93c-109">A primera vista, puede que no sea evidente en qué se diferencian las canalizaciones en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad93c-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="ad93c-110">Aunque se ve texto en la pantalla, PowerShell canaliza objetos, no texto, entre los comandos.</span><span class="sxs-lookup"><span data-stu-id="ad93c-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="ad93c-111">Canalización de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad93c-111">The PowerShell pipeline</span></span>

<span data-ttu-id="ad93c-112">Las canalizaciones son sin duda el concepto más valioso usado en las interfaces de línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="ad93c-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="ad93c-113">Cuando se usan correctamente, las canalizaciones reducen el esfuerzo de usar comandos complejos y facilitan la visualización del flujo de trabajo de los comandos.</span><span class="sxs-lookup"><span data-stu-id="ad93c-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="ad93c-114">Cada comando de una canalización (denominado un elemento de canalización) pasa la salida al siguiente comando de la canalización elemento por elemento.</span><span class="sxs-lookup"><span data-stu-id="ad93c-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="ad93c-115">Los comandos no tienen que controlar más de un elemento a la vez.</span><span class="sxs-lookup"><span data-stu-id="ad93c-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="ad93c-116">El resultado es un menor consumo de recursos y la capacidad de empezar a obtener la salida inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="ad93c-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="ad93c-117">Por ejemplo, si usa el cmdlet `Out-Host` para forzar una presentación página por página de la salida de otro comando, la salida tiene el aspecto del texto normal que se muestra en la pantalla, dividida en páginas:</span><span class="sxs-lookup"><span data-stu-id="ad93c-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

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

<span data-ttu-id="ad93c-118">La paginación también reduce la utilización de la CPU porque el procesamiento se transfiere al cmdlet `Out-Host` cuando tiene una página completa lista para mostrar.</span><span class="sxs-lookup"><span data-stu-id="ad93c-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="ad93c-119">Los cmdlets que lo preceden en la canalización pausan la ejecución hasta que la siguiente página de salida está disponible.</span><span class="sxs-lookup"><span data-stu-id="ad93c-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="ad93c-120">Puede ver cómo la canalización impacta el uso de la memoria y la CPU en el Administrador de tareas de Windows si compara estos comandos:</span><span class="sxs-lookup"><span data-stu-id="ad93c-120">You can see how piping impacts CPU and memory usage in the Windows Task Manager by comparing the following commands:</span></span>

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> <span data-ttu-id="ad93c-121">No todos los hosts de PowerShell admiten el parámetro **Paging**.</span><span class="sxs-lookup"><span data-stu-id="ad93c-121">The **Paging** parameter is not supported by all PowerShell hosts.</span></span> <span data-ttu-id="ad93c-122">Por ejemplo, cuando intenta usar el parámetro **Paging** en PowerShell ISE, verá el error siguiente:</span><span class="sxs-lookup"><span data-stu-id="ad93c-122">For example, when you try to use the **Paging** parameter in the PowerShell ISE, you see the following error:</span></span>
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="ad93c-123">Objetos de la canalización</span><span class="sxs-lookup"><span data-stu-id="ad93c-123">Objects in the pipeline</span></span>

<span data-ttu-id="ad93c-124">Cuando se ejecuta un cmdlet en PowerShell, se verá la salida del texto debido a la necesidad de representar objetos como texto en una ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="ad93c-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="ad93c-125">Es posible que la salida de texto no muestre todas las propiedades del objeto que se está emitiendo.</span><span class="sxs-lookup"><span data-stu-id="ad93c-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="ad93c-126">Por ejemplo, tenga en cuenta el cmdlet `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="ad93c-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="ad93c-127">Si ejecuta `Get-Location` mientras la ubicación actual es el directorio raíz de la unidad C, verá la siguiente salida:</span><span class="sxs-lookup"><span data-stu-id="ad93c-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="ad93c-128">La salida de texto es un resumen de la información y no una representación completa del objeto devuelto por `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="ad93c-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="ad93c-129">El encabezado de la salida se agrega mediante el proceso que formatea los datos para su visualización en pantalla.</span><span class="sxs-lookup"><span data-stu-id="ad93c-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="ad93c-130">Al canalizar la salida al cmdlet `Get-Member`, se obtiene información sobre el objeto devuelto por `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="ad93c-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
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

<span data-ttu-id="ad93c-131">`Get-Location` devuelve un objeto **PathInfo** que contiene la ruta de acceso actual y otra información.</span><span class="sxs-lookup"><span data-stu-id="ad93c-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>
