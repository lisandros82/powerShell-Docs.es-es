---
title: Escribir un módulo de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857941"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="42210-102">Escritura de un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="42210-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="42210-103">Este documento está dirigido a administradores, desarrolladores de la secuencia de comandos y los desarrolladores de cmdlets que necesitan para empaquetar y distribuir sus cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42210-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="42210-104">Mediante el uso de módulos de Windows PowerShell, puede empaquetar y distribuir sus soluciones de Windows PowerShell sin usar un lenguaje compilado.</span><span class="sxs-lookup"><span data-stu-id="42210-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="42210-105">Módulos de Windows PowerShell permiten a la partición, organizar y abstraer el código de Windows PowerShell en unidades independientes y reutilizables.</span><span class="sxs-lookup"><span data-stu-id="42210-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="42210-106">Con estas unidades reutilizables, pueden compartir fácilmente los módulos directamente con otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="42210-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="42210-107">Si es un desarrollador de script, también puede volver a empaquetar los módulos de terceros para crear aplicaciones personalizadas basadas en la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="42210-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="42210-108">Los módulos, similares a los módulos en otros lenguajes de secuencias de comandos como Perl y Python, habilitar soluciones de scripting para entornos de producción que usan componentes reutilizables, redistribuibles, con la ventaja añadida de que le permite volver a empaquetar y abstraer varios componentes a crear soluciones personalizadas.</span><span class="sxs-lookup"><span data-stu-id="42210-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="42210-109">En su más básica, Windows PowerShell tratará cualquier código válido de secuencia de comandos Windows PowerShell guarda en un archivo. psm1 como un módulo.</span><span class="sxs-lookup"><span data-stu-id="42210-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="42210-110">PowerShell también automáticamente tratará a cualquier ensamblado cmdlet binario como un módulo.</span><span class="sxs-lookup"><span data-stu-id="42210-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="42210-111">Sin embargo, también puede usar un módulo (o más específicamente, un manifiesto de módulo) para agrupar una solución completa.</span><span class="sxs-lookup"><span data-stu-id="42210-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="42210-112">Los escenarios siguientes describen los usos típicos de módulos de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42210-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="42210-113">Bibliotecas</span><span class="sxs-lookup"><span data-stu-id="42210-113">Libraries</span></span>

<span data-ttu-id="42210-114">Módulos pueden utilizarse para empaquetar y distribuir cohesivas bibliotecas de funciones que realizan tareas comunes.</span><span class="sxs-lookup"><span data-stu-id="42210-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="42210-115">Normalmente, los nombres de estas funciones comparten uno o varios nombres que reflejan la tarea habitual que se usan para.</span><span class="sxs-lookup"><span data-stu-id="42210-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="42210-116">Estas funciones también pueden ser similares a las clases de .NET Framework en que pueden tener miembros públicos y privados.</span><span class="sxs-lookup"><span data-stu-id="42210-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="42210-117">Por ejemplo, una biblioteca puede contener un conjunto de funciones para las transferencias de archivos.</span><span class="sxs-lookup"><span data-stu-id="42210-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="42210-118">En este caso, el nombre que refleje la tarea habitual podría ser "file".</span><span class="sxs-lookup"><span data-stu-id="42210-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="42210-119">Configuración</span><span class="sxs-lookup"><span data-stu-id="42210-119">Configuration</span></span>

<span data-ttu-id="42210-120">Los módulos se pueden usar para personalizar su entorno mediante la adición de variables, proveedores, funciones y cmdlets específicos.</span><span class="sxs-lookup"><span data-stu-id="42210-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="42210-121">Desarrollo de código compilado y distribución</span><span class="sxs-lookup"><span data-stu-id="42210-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="42210-122">Los desarrolladores de cmdlet y proveedor pueden utilizar módulos para probar y distribuir su código compilado sin necesidad de crear complementos. Puede importar el ensamblado que contiene el código compilado como un módulo (un módulo binario) sin necesidad de crear y registrar complementos.</span><span class="sxs-lookup"><span data-stu-id="42210-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="42210-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="42210-123">See Also</span></span>

[<span data-ttu-id="42210-124">Descripción de un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="42210-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="42210-125">Cómo escribir un módulo de Script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="42210-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="42210-126">Cómo escribir un módulo binario de PowerShell</span><span class="sxs-lookup"><span data-stu-id="42210-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="42210-127">Cómo escribir un manifiesto de módulo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="42210-127">How to Write a PowerShell Module Manifest</span></span>](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[<span data-ttu-id="42210-128">Modificar la ruta de instalación PSModulePath</span><span class="sxs-lookup"><span data-stu-id="42210-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="42210-129">Importar un módulo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="42210-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="42210-130">Instalación de un módulo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="42210-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
