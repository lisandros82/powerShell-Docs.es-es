---
title: Uso de módulos de Cmdlets de importación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859151"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="67c2a-102">Cómo importar cmdlets mediante módulos</span><span class="sxs-lookup"><span data-stu-id="67c2a-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="67c2a-103">Este tema describe cómo importar los cmdlets en una sesión de Windows PowerShell mediante el uso de un módulo binario.</span><span class="sxs-lookup"><span data-stu-id="67c2a-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="67c2a-104">Pueden incluir los miembros de los módulos de cmdlets, proveedores, funciones, variables, alias y mucho más.</span><span class="sxs-lookup"><span data-stu-id="67c2a-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="67c2a-105">Complementos solo pueden contener cmdlets y proveedores.</span><span class="sxs-lookup"><span data-stu-id="67c2a-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="67c2a-106">Cómo cargar mediante un módulo de cmdlets</span><span class="sxs-lookup"><span data-stu-id="67c2a-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="67c2a-107">Cree una carpeta de módulo que tiene el mismo nombre que el archivo de ensamblado en el que se implementan los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="67c2a-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="67c2a-108">En este procedimiento, se crea la carpeta del módulo en el `system32` carpeta.</span><span class="sxs-lookup"><span data-stu-id="67c2a-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="67c2a-109">Asegúrese de que el `PSModulePath` variable de entorno incluye la ruta de acceso a la nueva carpeta de módulo.</span><span class="sxs-lookup"><span data-stu-id="67c2a-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="67c2a-110">De forma predeterminada, la carpeta del sistema se ha agregado a la `PSModulePath` variable de entorno.</span><span class="sxs-lookup"><span data-stu-id="67c2a-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="67c2a-111">Copie el ensamblado de cmdlet en la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="67c2a-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="67c2a-112">Ejecute el siguiente comando para agregar los cmdlets a la sesión:</span><span class="sxs-lookup"><span data-stu-id="67c2a-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="67c2a-113">Este procedimiento puede usarse para probar sus cmdlets.</span><span class="sxs-lookup"><span data-stu-id="67c2a-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="67c2a-114">Agrega todos los cmdlets en el ensamblado a la sesión.</span><span class="sxs-lookup"><span data-stu-id="67c2a-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="67c2a-115">Para obtener más información acerca de los módulos, vea los distintos tipos de módulos, las distintas formas de cargar los módulos y cómo restringir los elementos de un módulo que se exportan, [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="67c2a-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67c2a-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="67c2a-116">See Also</span></span>

[<span data-ttu-id="67c2a-117">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="67c2a-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="67c2a-118">Instalación de módulos</span><span class="sxs-lookup"><span data-stu-id="67c2a-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)