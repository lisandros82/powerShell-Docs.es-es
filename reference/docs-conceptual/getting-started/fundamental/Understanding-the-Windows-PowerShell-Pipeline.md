---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Descripción de la canalización de Windows PowerShell"
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 6d152e52d2fcfb9dd592eb9ac40500615f2186cb
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="understanding-the-windows-powershell-pipeline"></a><span data-ttu-id="30ac6-103">Descripción de la canalización de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="30ac6-103">Understanding the Windows PowerShell Pipeline</span></span>
<span data-ttu-id="30ac6-104">La canalización funciona prácticamente en cualquier lugar en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30ac6-104">Piping works virtually everywhere in Windows PowerShell.</span></span> <span data-ttu-id="30ac6-105">Aunque se ve texto en la pantalla, Windows PowerShell no canaliza texto entre los comandos.</span><span class="sxs-lookup"><span data-stu-id="30ac6-105">Although you see text on the screen, Windows PowerShell does not pipe text between commands.</span></span> <span data-ttu-id="30ac6-106">En su lugar, canaliza objetos.</span><span class="sxs-lookup"><span data-stu-id="30ac6-106">Instead, it pipes objects.</span></span>

<span data-ttu-id="30ac6-107">La notación usada para las canalizaciones es similar a la que se usa en otros shells, por lo que, a primera vista, puede que no sea evidente que Windows PowerShell presenta algo nuevo.</span><span class="sxs-lookup"><span data-stu-id="30ac6-107">The notation used for pipelines is similar to that used in other shells, so at first glance, it may not be apparent that Windows PowerShell introduces something new.</span></span> <span data-ttu-id="30ac6-108">Por ejemplo, si usa el cmdlet **Out-Host** para forzar una presentación página por página de la salida de otro comando, la salida tiene el aspecto del texto normal que se muestra en la pantalla, dividida en páginas:</span><span class="sxs-lookup"><span data-stu-id="30ac6-108">For example, if you use the **Out-Host** cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="30ac6-109">El comando Out-Host -Paging es un elemento de la canalización útil siempre que tiene una salida larga que le gustaría mostrar lentamente.</span><span class="sxs-lookup"><span data-stu-id="30ac6-109">The Out-Host -Paging command is a useful pipeline element whenever you have lengthy output that you would like to display slowly.</span></span> <span data-ttu-id="30ac6-110">Es especialmente útil si la operación consume una gran cantidad de CPU.</span><span class="sxs-lookup"><span data-stu-id="30ac6-110">It is especially useful if the operation is very CPU-intensive.</span></span> <span data-ttu-id="30ac6-111">Dado que el procesamiento se transfiere al cmdlet Out-Host cuando tiene una página completa lista para mostrar, los cmdlets que lo preceden en la canalización detienen la operación hasta que la siguiente página de salida esté disponible.</span><span class="sxs-lookup"><span data-stu-id="30ac6-111">Because processing is transferred to the Out-Host cmdlet when it has a complete page ready to display, cmdlets that precede it in the pipeline halt operation until the next page of output is available.</span></span> <span data-ttu-id="30ac6-112">Puede verlo si usa el Administrador de tareas de Windows para supervisar el uso de la CPU y la memoria de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30ac6-112">You can see this if you use the Windows Task Manager to monitor CPU and memory use by Windows PowerShell.</span></span>

<span data-ttu-id="30ac6-113">Ejecute el siguiente comando: **Get-ChildItem C:\\Windows -Recurse**.</span><span class="sxs-lookup"><span data-stu-id="30ac6-113">Run the following command: **Get-ChildItem C:\\Windows -Recurse**.</span></span> <span data-ttu-id="30ac6-114">Compare el uso de la CPU y la memoria con este comando: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span><span class="sxs-lookup"><span data-stu-id="30ac6-114">Compare the CPU and memory usage to this command: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span></span> <span data-ttu-id="30ac6-115">Lo que ve en la pantalla es texto, lo que se debe a la necesidad de representar objetos como texto en una ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="30ac6-115">What you see on the screen is text, but that is because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="30ac6-116">Se trata simplemente de una representación de lo que sucede realmente en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30ac6-116">This is just a representation of what is really going on inside Windows PowerShell.</span></span> <span data-ttu-id="30ac6-117">Por ejemplo, considere el cmdlet Get-Location.</span><span class="sxs-lookup"><span data-stu-id="30ac6-117">For example, consider the Get-Location cmdlet.</span></span> <span data-ttu-id="30ac6-118">Si escribe **Get-Location** mientras la ubicación actual es la raíz de la unidad C, verá la siguiente salida:</span><span class="sxs-lookup"><span data-stu-id="30ac6-118">If you type **Get-Location** while your current location is the root of the C drive, you would see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="30ac6-119">Si Windows PowerShell canaliza texto, al emitir un comando como **Get-Location | Out-Host**, pasará de **Get-Location** a **Out-Host** un conjunto de caracteres en el orden en que se muestran en la pantalla.</span><span class="sxs-lookup"><span data-stu-id="30ac6-119">If Windows PowerShell pipelined text, issuing a command such as **Get-Location | Out-Host**, would pass from **Get-Location** to **Out-Host** a set of characters in the order they are displayed onscreen.</span></span> <span data-ttu-id="30ac6-120">En otras palabras, si fuera a ignorar la información de encabezado, **Out-Host** recibiría primero el carácter '**C'**, luego el carácter '**:'** y, finalmente, el carácter '**\\'**.</span><span class="sxs-lookup"><span data-stu-id="30ac6-120">In other words, if you were to ignore the heading information, **Out-Host** would first receive the character '**C'**, then the character '**:'**, then the character '**\\'**.</span></span> <span data-ttu-id="30ac6-121">El cmdlet **Out-Host** no pudo determinar el significado que debía asociarse a los caracteres emitidos por el cmdlet **Get-Location**.</span><span class="sxs-lookup"><span data-stu-id="30ac6-121">The **Out-Host** cmdlet could not determine what meaning to associate with the characters output by the **Get-Location** cmdlet.</span></span>

<span data-ttu-id="30ac6-122">En lugar de utilizar texto para permitir que los comandos de una canalización se comuniquen, Windows PowerShell usa objetos.</span><span class="sxs-lookup"><span data-stu-id="30ac6-122">Instead of using text to let commands in a pipeline communicate, Windows PowerShell uses objects.</span></span> <span data-ttu-id="30ac6-123">Desde el punto de vista de un usuario, los objetos empaquetan información relacionada en un formulario que facilita la manipulación de la información como una unidad y la extracción de los elementos específicos que necesita.</span><span class="sxs-lookup"><span data-stu-id="30ac6-123">From the standpoint of a user, objects package related information into a form that makes it easier to manipulate the information as a unit, and extract specific items that you need.</span></span>

<span data-ttu-id="30ac6-124">El comando **Get-Location** no devuelve el texto que contenga la ruta de acceso actual.</span><span class="sxs-lookup"><span data-stu-id="30ac6-124">The **Get-Location** command does not return text that contains the current path.</span></span> <span data-ttu-id="30ac6-125">Devuelve un conjunto de información denominado objeto **PathInfo** que contiene la ruta de acceso actual junto con otra información.</span><span class="sxs-lookup"><span data-stu-id="30ac6-125">It returns a package of information called a **PathInfo** object that contains the current path along with some other information.</span></span> <span data-ttu-id="30ac6-126">El cmdlet **Out-Host** envía luego este objeto **PathInfo** a la pantalla y Windows PowerShell decide qué información se mostrará y cómo se mostrará en función de sus reglas de formato.</span><span class="sxs-lookup"><span data-stu-id="30ac6-126">The **Out-Host** cmdlet then sends this **PathInfo** object to the screen, and Windows PowerShell decides what information to display and how to display it based on its formatting rules.</span></span>

<span data-ttu-id="30ac6-127">De hecho, la información de encabezado generada por el cmdlet **Get-Location** se agrega solo al final del proceso, como parte del proceso de formato de los datos para su presentación en pantalla.</span><span class="sxs-lookup"><span data-stu-id="30ac6-127">In fact, the heading information output by the **Get-Location** cmdlet is added only at the end of the process, as part of the process of formatting the data for onscreen display.</span></span> <span data-ttu-id="30ac6-128">Lo que ve en la pantalla es un resumen de la información y no una representación completa del objeto de salida.</span><span class="sxs-lookup"><span data-stu-id="30ac6-128">What you see onscreen is a summary of information, and not a complete representation of the output object.</span></span>

<span data-ttu-id="30ac6-129">Dado que puede haber más información devuelta por un comando de Windows PowerShell de la que vemos en la ventana de la consola, ¿cómo podemos recuperar los elementos no visibles?</span><span class="sxs-lookup"><span data-stu-id="30ac6-129">Given that there may be more information output from a Windows PowerShell command than what we see displayed in the console window, how can you retrieve the non-visible elements?</span></span> <span data-ttu-id="30ac6-130">¿Cómo se pueden ver los datos adicionales?</span><span class="sxs-lookup"><span data-stu-id="30ac6-130">How do you view the extra data?</span></span> <span data-ttu-id="30ac6-131">¿Qué ocurre si quiere ver los datos en un formato diferente al que suele usar Windows PowerShell?</span><span class="sxs-lookup"><span data-stu-id="30ac6-131">And what if you want to view the data in a format different than the one Windows PowerShell normally uses?</span></span>

<span data-ttu-id="30ac6-132">En lo que queda de este capítulo explicaremos cómo puede detectar la estructura de objetos específicos de Windows PowerShell, seleccionar elementos específicos y darles formato para mostrarlos más fácilmente, y cómo enviar esta información a ubicaciones de salida alternativas, como archivos e impresoras.</span><span class="sxs-lookup"><span data-stu-id="30ac6-132">The rest of this chapter discusses how you can discover the structure of specific Windows PowerShell objects, selecting specific items and formatting them for easier display, and how to send this information to alternative output locations such as files and printers.</span></span>

