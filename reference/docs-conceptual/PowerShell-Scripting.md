---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Scripting de PowerShell
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094058"
---
# <a name="powershell"></a><span data-ttu-id="72d8f-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="72d8f-103">PowerShell</span></span>

<span data-ttu-id="72d8f-104">PowerShell, basado en .NET Framework, es un lenguaje de scripting y shell de línea de comandos basado en tareas. Está diseñado específicamente para que los administradores del sistema y los usuarios avanzados automaticen rápidamente la administración de varios sistemas operativos (Linux, macOS, Unix y Windows) y los procesos relacionados con las aplicaciones que se ejecutan en dichos sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="72d8f-104">Built on the .NET Framework, PowerShell is a task-based command-line shell and scripting language; it is designed specifically for system administrators and power-users, to rapidly automate the administration of multiple operating systems (Linux, macOS, Unix, and Windows) and the processes related to the applications that run on those operating systems.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="72d8f-105">PowerShell es de código abierto</span><span class="sxs-lookup"><span data-stu-id="72d8f-105">PowerShell is open source</span></span>

<span data-ttu-id="72d8f-106">El código fuente base de PowerShell ahora está disponible en GitHub y admite las contribuciones de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="72d8f-106">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="72d8f-107">Vea el [código de PowerShell en GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="72d8f-107">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="72d8f-108">Puede empezar con los fragmentos que necesita en [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) (Obtener PowerShell).</span><span class="sxs-lookup"><span data-stu-id="72d8f-108">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="72d8f-109">o, si lo prefiere, con el paseo introductorio incluido en esta [introducción](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="72d8f-109">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="72d8f-110">Objetivos de diseño de PowerShell</span><span class="sxs-lookup"><span data-stu-id="72d8f-110">PowerShell design goals</span></span>
<span data-ttu-id="72d8f-111">PowerShell está diseñado para mejorar el entorno de scripting y línea de comandos mediante la eliminación de antiguos problemas y la adición de nuevas características.</span><span class="sxs-lookup"><span data-stu-id="72d8f-111">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="72d8f-112">Detectabilidad</span><span class="sxs-lookup"><span data-stu-id="72d8f-112">Discoverability</span></span>
<span data-ttu-id="72d8f-113">PowerShell facilita la detección de sus características.</span><span class="sxs-lookup"><span data-stu-id="72d8f-113">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="72d8f-114">Por ejemplo, para buscar una lista de cmdlets con la finalidad de ver y cambiar los servicios de Windows, escriba:</span><span class="sxs-lookup"><span data-stu-id="72d8f-114">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="72d8f-115">Tras detectar qué cmdlet lleva a cabo una tarea, si desea obtener más información sobre él, utilice el cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="72d8f-115">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span>
<span data-ttu-id="72d8f-116">Por ejemplo, para mostrar ayuda acerca del cmdlet `Get-Service`, escriba:</span><span class="sxs-lookup"><span data-stu-id="72d8f-116">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```
<span data-ttu-id="72d8f-117">La mayoría de los cmdlets emiten objetos que se pueden manipular y después representar en texto para mostrar.</span><span class="sxs-lookup"><span data-stu-id="72d8f-117">Most cmdlets emit objects which can be manipulated and then rendered into text for display.</span></span>
<span data-ttu-id="72d8f-118">Para conocer a la perfección la salida de dicho cmdlet, canalice su salida al cmdlet `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="72d8f-118">To fully understand the output of that cmdlet, pipe its output to the `Get-Member` cmdlet.</span></span>
<span data-ttu-id="72d8f-119">Por ejemplo, el siguiente comando muestra información acerca de los miembros de la salida del objeto mediante el cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="72d8f-119">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="72d8f-120">Consistency</span><span class="sxs-lookup"><span data-stu-id="72d8f-120">Consistency</span></span>
<span data-ttu-id="72d8f-121">La administración de sistemas puede ser una tarea muy compleja y las herramientas con una interfaz coherente ayudan a controlar esa complejidad inherente.</span><span class="sxs-lookup"><span data-stu-id="72d8f-121">Managing systems can be a complex endeavor and tools that have a consistent interface help to control the inherent complexity.</span></span>
<span data-ttu-id="72d8f-122">Lamentablemente, ni las herramientas de línea de comandos ni los objetos COM que permiten ejecutar scripts son famosos por su coherencia.</span><span class="sxs-lookup"><span data-stu-id="72d8f-122">Unfortunately, neither command-line tools nor scriptable COM objects have been known for their consistency.</span></span>

<span data-ttu-id="72d8f-123">La coherencia de PowerShell es uno de sus activos principales.</span><span class="sxs-lookup"><span data-stu-id="72d8f-123">The consistency of PowerShell is one of its primary assets.</span></span>
<span data-ttu-id="72d8f-124">Por ejemplo, si aprende a usar el cmdlet `Sort-Object`, podrá usar dicho conocimiento para ordenar la salida de cualquier cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72d8f-124">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span>
<span data-ttu-id="72d8f-125">No es necesario obtener información sobre las distintas rutinas de ordenación de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72d8f-125">You do not have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="72d8f-126">Además, los desarrolladores de cmdlets no tienen que diseñar características de ordenación para sus cmdlets.</span><span class="sxs-lookup"><span data-stu-id="72d8f-126">In addition, cmdlet developers do not have to design sorting features for their cmdlets.</span></span>
<span data-ttu-id="72d8f-127">PowerShell les proporciona un marco que proporciona las características básicas y les obliga a ser coherentes en muchos aspectos de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="72d8f-127">PowerShell gives them a framework that provides the basic features and forces them to be consistent about many aspects of the interface.</span></span>
<span data-ttu-id="72d8f-128">El marco elimina algunas de las opciones que se suelen dejar al desarrollador, pero a cambio simplifica el desarrollo de cmdlets sólidos y fáciles de usar.</span><span class="sxs-lookup"><span data-stu-id="72d8f-128">The framework eliminates some of the choices that are typically left to the developer, but, in return, it makes the development of robust and easy-to-use cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="72d8f-129">Entornos interactivo y de scripting</span><span class="sxs-lookup"><span data-stu-id="72d8f-129">Interactive and Scripting Environments</span></span>
<span data-ttu-id="72d8f-130">PowerShell es un entorno interactivo y de scripting combinado que ofrece acceso a las herramientas de línea de comandos y a los objetos COM, y que permite aprovechar la eficacia de la biblioteca de clases .NET Framework (FCL).</span><span class="sxs-lookup"><span data-stu-id="72d8f-130">PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL).</span></span>

<span data-ttu-id="72d8f-131">Este entorno mejora en el Símbolo del sistema de Windows, que proporciona un entorno interactivo con varias herramientas de línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="72d8f-131">This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools.</span></span>
<span data-ttu-id="72d8f-132">También mejora en los scripts de Windows Script Host (WSH), que permiten usar varias herramientas de línea de comandos y objetos de automatización COM, pero no proporcionan un entorno interactivo.</span><span class="sxs-lookup"><span data-stu-id="72d8f-132">It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.</span></span>

<span data-ttu-id="72d8f-133">Al combinar el acceso a todas estas características, PowerShell amplía la capacidad del usuario interactivo y el escritor de scripts, y facilita la administración del sistema.</span><span class="sxs-lookup"><span data-stu-id="72d8f-133">By combining access to all of these features, PowerShell extends the ability of the interactive user and the script writer, and makes system administration more manageable.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="72d8f-134">Orientación a objetos</span><span class="sxs-lookup"><span data-stu-id="72d8f-134">Object Orientation</span></span>
<span data-ttu-id="72d8f-135">Aunque interactúa con PowerShell escribiendo comandos de texto, PowerShell se basa en objetos, no en texto.</span><span class="sxs-lookup"><span data-stu-id="72d8f-135">Although you interact with PowerShell by typing commands in text, PowerShell is based on objects, not text.</span></span>
<span data-ttu-id="72d8f-136">La salida de un comando es un objeto.</span><span class="sxs-lookup"><span data-stu-id="72d8f-136">The output of a command is an object.</span></span>
<span data-ttu-id="72d8f-137">Puede enviar el objeto de salida a otro comando como entrada.</span><span class="sxs-lookup"><span data-stu-id="72d8f-137">You can send the output object to another command as its input.</span></span>
<span data-ttu-id="72d8f-138">Como resultado, PowerShell proporciona una interfaz conocida a usuarios que tienen experiencia con otros shells, a la vez que introduce un paradigma de línea de comandos nuevo y eficaz.</span><span class="sxs-lookup"><span data-stu-id="72d8f-138">As a result, PowerShell provides a familiar interface to people experienced with other shells, while introducing a new and powerful command-line paradigm.</span></span>
<span data-ttu-id="72d8f-139">Amplía el concepto de envío de datos entre comandos, ya que permite enviar objetos, en lugar de texto.</span><span class="sxs-lookup"><span data-stu-id="72d8f-139">It extends the concept of sending data between commands by enabling you to send objects, rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="72d8f-140">Transición sencilla al scripting</span><span class="sxs-lookup"><span data-stu-id="72d8f-140">Easy Transition to Scripting</span></span>
<span data-ttu-id="72d8f-141">PowerShell facilita la transición de la escritura interactiva de comandos a la creación y ejecución de scripts.</span><span class="sxs-lookup"><span data-stu-id="72d8f-141">PowerShell makes it easy to transition from typing commands interactively to creating and running scripts.</span></span>
<span data-ttu-id="72d8f-142">Puede escribir comandos en el símbolo del sistema de PowerShell para detectar los comandos que realizan una tarea.</span><span class="sxs-lookup"><span data-stu-id="72d8f-142">You can type commands at the PowerShell command prompt to discover the commands that perform a task.</span></span>
<span data-ttu-id="72d8f-143">A continuación, puede guardar esos comandos en una transcripción o un historial antes de copiarlos en un archivo para su uso como un script.</span><span class="sxs-lookup"><span data-stu-id="72d8f-143">Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.</span></span>
