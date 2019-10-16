---
title: Escribir un módulo de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360624"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="cb4da-102">Escritura de un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4da-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="cb4da-103">Este documento está escrito para administradores, desarrolladores de scripts y desarrolladores de cmdlets que necesitan empaquetar y distribuir sus cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb4da-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="cb4da-104">Mediante el uso de módulos de Windows PowerShell, puede empaquetar y distribuir sus soluciones de Windows PowerShell sin usar un lenguaje compilado.</span><span class="sxs-lookup"><span data-stu-id="cb4da-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="cb4da-105">Los módulos de Windows PowerShell le permiten particionar, organizar y abstraer su código de Windows PowerShell en unidades reutilizables independientes.</span><span class="sxs-lookup"><span data-stu-id="cb4da-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="cb4da-106">Con estas unidades reutilizables, puede compartir fácilmente sus módulos directamente con otros.</span><span class="sxs-lookup"><span data-stu-id="cb4da-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="cb4da-107">Si es desarrollador de script, también puede volver a empaquetar módulos de terceros para crear aplicaciones personalizadas basadas en scripts.</span><span class="sxs-lookup"><span data-stu-id="cb4da-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="cb4da-108">Los módulos, similares a los módulos de otros lenguajes de scripting, como Perl y Python, habilitan soluciones de scripting listas para producción que usan componentes redistribuibles reutilizables, con la ventaja adicional de permitirle volver a empaquetar y abstraer varios componentes en crear soluciones personalizadas.</span><span class="sxs-lookup"><span data-stu-id="cb4da-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="cb4da-109">En su mayor parte, Windows PowerShell tratará cualquier código de script válido de Windows PowerShell guardado en un archivo. psm1 como módulo.</span><span class="sxs-lookup"><span data-stu-id="cb4da-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="cb4da-110">PowerShell también tratará automáticamente cualquier ensamblado de cmdlet binario como módulo.</span><span class="sxs-lookup"><span data-stu-id="cb4da-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="cb4da-111">Sin embargo, también puede usar un módulo (o más concretamente, un manifiesto de módulo) para agrupar una solución completa.</span><span class="sxs-lookup"><span data-stu-id="cb4da-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="cb4da-112">En los siguientes escenarios se describen los usos típicos de los módulos de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb4da-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="cb4da-113">Bibliotecas</span><span class="sxs-lookup"><span data-stu-id="cb4da-113">Libraries</span></span>

<span data-ttu-id="cb4da-114">Los módulos se pueden usar para empaquetar y distribuir bibliotecas coherentes de funciones que realizan tareas comunes.</span><span class="sxs-lookup"><span data-stu-id="cb4da-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="cb4da-115">Normalmente, los nombres de estas funciones comparten uno o más sustantivos que reflejan la tarea común para la que se usan.</span><span class="sxs-lookup"><span data-stu-id="cb4da-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="cb4da-116">Estas funciones también pueden ser similares a las clases de .NET Framework en que pueden tener miembros públicos y privados.</span><span class="sxs-lookup"><span data-stu-id="cb4da-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="cb4da-117">Por ejemplo, una biblioteca puede contener un conjunto de funciones para las transferencias de archivos.</span><span class="sxs-lookup"><span data-stu-id="cb4da-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="cb4da-118">En este caso, el sustantivo que refleja la tarea común podría ser "File".</span><span class="sxs-lookup"><span data-stu-id="cb4da-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="cb4da-119">Configuración</span><span class="sxs-lookup"><span data-stu-id="cb4da-119">Configuration</span></span>

<span data-ttu-id="cb4da-120">Los módulos se pueden usar para personalizar el entorno mediante la adición de cmdlets, proveedores, funciones y variables específicos.</span><span class="sxs-lookup"><span data-stu-id="cb4da-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="cb4da-121">Desarrollo y distribución de código compilado</span><span class="sxs-lookup"><span data-stu-id="cb4da-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="cb4da-122">Los desarrolladores de cmdlets y proveedores pueden usar módulos para probar y distribuir su código compilado sin necesidad de crear complementos. Pueden importar el ensamblado que contiene el código compilado como un módulo (un módulo binario) sin necesidad de crear y registrar complementos.</span><span class="sxs-lookup"><span data-stu-id="cb4da-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb4da-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="cb4da-123">See Also</span></span>

[<span data-ttu-id="cb4da-124">Descripción de un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4da-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="cb4da-125">Cómo escribir un módulo de script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4da-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="cb4da-126">Cómo escribir un módulo binario de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4da-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="cb4da-127">Cómo escribir un manifiesto de módulo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4da-127">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="cb4da-128">Modificación de la ruta de instalación de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="cb4da-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="cb4da-129">Importar un módulo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4da-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="cb4da-130">Instalación de un módulo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4da-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
