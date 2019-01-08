---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Scripting de PowerShell
ms.openlocfilehash: 07925ce8dcafd33970a703c9b241bf6f76f88d10
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402897"
---
# <a name="powershell"></a><span data-ttu-id="c29f7-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="c29f7-103">PowerShell</span></span>

<span data-ttu-id="c29f7-104">PowerShell es un shell de línea de comandos y un lenguaje de scripting basado en tareas integrado en .NET.</span><span class="sxs-lookup"><span data-stu-id="c29f7-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="c29f7-105">PowerShell ayuda a los administradores de sistemas y a los usuarios avanzados a automatizar rápidamente las tareas que administran sistemas operativos (Linux, macOS y Windows) y procesos.</span><span class="sxs-lookup"><span data-stu-id="c29f7-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="c29f7-106">Los comandos de PowerShell permiten administrar los equipos desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="c29f7-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="c29f7-107">Los proveedores de PowerShell permiten obtener acceso a almacenes de datos, como el Registro y el almacén de certificados, con la misma simplicidad con que se obtiene acceso al sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="c29f7-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="c29f7-108">PowerShell incluye un analizador de expresiones muy completo y un lenguaje de scripting totalmente desarrollado.</span><span class="sxs-lookup"><span data-stu-id="c29f7-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="c29f7-109">PowerShell es de código abierto</span><span class="sxs-lookup"><span data-stu-id="c29f7-109">PowerShell is open-source</span></span>

<span data-ttu-id="c29f7-110">El código fuente base de PowerShell ahora está disponible en GitHub y admite las contribuciones de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="c29f7-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="c29f7-111">Vea el [código de PowerShell en GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="c29f7-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="c29f7-112">Puede empezar con los fragmentos que necesita en [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) (Obtener PowerShell).</span><span class="sxs-lookup"><span data-stu-id="c29f7-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="c29f7-113">O, si lo prefiere, con el paseo introductorio incluido en esta [introducción](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="c29f7-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="c29f7-114">Objetivos de diseño de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c29f7-114">PowerShell design goals</span></span>

<span data-ttu-id="c29f7-115">PowerShell está diseñado para mejorar el entorno de scripting y línea de comandos mediante la eliminación de antiguos problemas y la adición de nuevas características.</span><span class="sxs-lookup"><span data-stu-id="c29f7-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="c29f7-116">Detectabilidad</span><span class="sxs-lookup"><span data-stu-id="c29f7-116">Discoverability</span></span>

<span data-ttu-id="c29f7-117">PowerShell facilita la detección de sus características.</span><span class="sxs-lookup"><span data-stu-id="c29f7-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="c29f7-118">Por ejemplo, para buscar una lista de cmdlets con la finalidad de ver y cambiar los servicios de Windows, escriba:</span><span class="sxs-lookup"><span data-stu-id="c29f7-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="c29f7-119">Tras detectar qué cmdlet lleva a cabo una tarea, si desea obtener más información sobre él, utilice el cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="c29f7-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="c29f7-120">Por ejemplo, para mostrar ayuda acerca del cmdlet `Get-Service`, escriba:</span><span class="sxs-lookup"><span data-stu-id="c29f7-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="c29f7-121">La mayoría de los cmdlets devuelven objetos que se pueden manipular y después representarse como texto para mostrar.</span><span class="sxs-lookup"><span data-stu-id="c29f7-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="c29f7-122">Para conocer a la perfección la salida de un cmdlet, canalice la salida al cmdlet `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="c29f7-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="c29f7-123">Por ejemplo, el siguiente comando muestra información acerca de los miembros de la salida del objeto mediante el cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="c29f7-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="c29f7-124">Consistency</span><span class="sxs-lookup"><span data-stu-id="c29f7-124">Consistency</span></span>

<span data-ttu-id="c29f7-125">La administración de sistemas puede ser una tarea compleja.</span><span class="sxs-lookup"><span data-stu-id="c29f7-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="c29f7-126">Las herramientas que tienen una interfaz coherente ayudan a controlar esa complejidad inherente.</span><span class="sxs-lookup"><span data-stu-id="c29f7-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="c29f7-127">Lamentablemente, ni las herramientas de línea de comandos ni los objetos COM que permiten ejecutar scripts son famosos por su coherencia.</span><span class="sxs-lookup"><span data-stu-id="c29f7-127">Unfortunately, command-line tools and scriptable COM objects aren't known for their consistency.</span></span>

<span data-ttu-id="c29f7-128">La coherencia de PowerShell es uno de sus activos principales.</span><span class="sxs-lookup"><span data-stu-id="c29f7-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="c29f7-129">Por ejemplo, si aprende a usar el cmdlet `Sort-Object`, podrá usar dicho conocimiento para ordenar la salida de cualquier cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c29f7-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="c29f7-130">No es necesario obtener información sobre las distintas rutinas de ordenación de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c29f7-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="c29f7-131">Además, los desarrolladores de cmdlets no tienen que diseñar características de ordenación para sus cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c29f7-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="c29f7-132">PowerShell proporciona una plataforma con las características básicas que aplican la coherencia.</span><span class="sxs-lookup"><span data-stu-id="c29f7-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="c29f7-133">La plataforma elimina algunas opciones que quedan para el desarrollador.</span><span class="sxs-lookup"><span data-stu-id="c29f7-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="c29f7-134">Pero, a cambio, hace que el desarrollo de los cmdlets sea mucho más sencillo.</span><span class="sxs-lookup"><span data-stu-id="c29f7-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="c29f7-135">Entornos interactivo y de scripting</span><span class="sxs-lookup"><span data-stu-id="c29f7-135">Interactive and scripting environments</span></span>

<span data-ttu-id="c29f7-136">El símbolo del sistema de Windows proporciona un shell interactivo con acceso a herramientas de línea de comandos y scripting básico.</span><span class="sxs-lookup"><span data-stu-id="c29f7-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="c29f7-137">Windows Script Host (WSH) tiene herramientas de línea de comandos que permiten ejecutar scripts y objetos de automatización COM, pero no proporciona un shell interactivo.</span><span class="sxs-lookup"><span data-stu-id="c29f7-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="c29f7-138">PowerShell combina un shell interactivo y un entorno de scripting.</span><span class="sxs-lookup"><span data-stu-id="c29f7-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="c29f7-139">PowerShell puede acceder a las herramientas de línea de comandos, objetos COM y bibliotecas de clases .NET.</span><span class="sxs-lookup"><span data-stu-id="c29f7-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="c29f7-140">Esta combinación de características amplía las funcionalidades del usuario interactivo, el escritor de scripts y el administrador del sistema.</span><span class="sxs-lookup"><span data-stu-id="c29f7-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="c29f7-141">Orientación a objetos</span><span class="sxs-lookup"><span data-stu-id="c29f7-141">Object orientation</span></span>

<span data-ttu-id="c29f7-142">PowerShell se basa en el objeto, no en el texto.</span><span class="sxs-lookup"><span data-stu-id="c29f7-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="c29f7-143">La salida de un comando es un objeto.</span><span class="sxs-lookup"><span data-stu-id="c29f7-143">The output of a command is an object.</span></span> <span data-ttu-id="c29f7-144">Puede enviar el objeto de salida a otro comando como entrada, a través de una canalización.</span><span class="sxs-lookup"><span data-stu-id="c29f7-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="c29f7-145">Esta canalización proporciona una interfaz familiar para las personas que tienen experiencia con otros shells.</span><span class="sxs-lookup"><span data-stu-id="c29f7-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="c29f7-146">PowerShell extiende este concepto mediante el envío de objetos en lugar de texto.</span><span class="sxs-lookup"><span data-stu-id="c29f7-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="c29f7-147">Transición sencilla al scripting</span><span class="sxs-lookup"><span data-stu-id="c29f7-147">Easy transition to scripting</span></span>

<span data-ttu-id="c29f7-148">La detectabilidad de comandos de PowerShell facilita la transición de la escritura interactiva de comandos a la creación y ejecución de scripts.</span><span class="sxs-lookup"><span data-stu-id="c29f7-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="c29f7-149">Las transcripciones y el historial de PowerShell facilitan la copia de comandos a un archivo para su uso como script.</span><span class="sxs-lookup"><span data-stu-id="c29f7-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
