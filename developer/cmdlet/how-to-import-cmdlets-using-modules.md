---
title: Cómo importar cmdlets mediante módulos | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215262"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="c94c2-102">Cómo importar cmdlets mediante módulos</span><span class="sxs-lookup"><span data-stu-id="c94c2-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="c94c2-103">En este artículo se describe cómo importar cmdlets en una sesión de PowerShell con un módulo binario.</span><span class="sxs-lookup"><span data-stu-id="c94c2-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="c94c2-104">Los miembros de los módulos pueden incluir cmdlets, proveedores, funciones, variables, alias y mucho más.</span><span class="sxs-lookup"><span data-stu-id="c94c2-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="c94c2-105">Los complementos solo pueden contener cmdlets y proveedores.</span><span class="sxs-lookup"><span data-stu-id="c94c2-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="c94c2-106">Cómo cargar cmdlets mediante un módulo</span><span class="sxs-lookup"><span data-stu-id="c94c2-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="c94c2-107">Cree una carpeta de módulo que tenga el mismo nombre que el archivo de ensamblado en el que se implementan los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c94c2-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="c94c2-108">En este procedimiento, se crea la carpeta del módulo en la `system32` carpeta Windows.</span><span class="sxs-lookup"><span data-stu-id="c94c2-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="c94c2-109">Asegúrese de que la `PSModulePath` variable de entorno incluya la ruta de acceso a la nueva carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="c94c2-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="c94c2-110">De forma predeterminada, la carpeta del sistema ya está agregada a la `PSModulePath` variable de entorno.</span><span class="sxs-lookup"><span data-stu-id="c94c2-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="c94c2-111">Para ver el `PSModulePath`, escriba: `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="c94c2-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="c94c2-112">Copie el ensamblado del cmdlet en la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="c94c2-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="c94c2-113">Agregue un archivo de manifiesto del`.psd1`módulo () en la carpeta raíz del módulo.</span><span class="sxs-lookup"><span data-stu-id="c94c2-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="c94c2-114">PowerShell usa el manifiesto del módulo para importar el módulo.</span><span class="sxs-lookup"><span data-stu-id="c94c2-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="c94c2-115">Para obtener más información, vea [Cómo escribir un manifiesto del módulo de PowerShell](../module/how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="c94c2-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="c94c2-116">Ejecute el siguiente comando para agregar los cmdlets a la sesión:</span><span class="sxs-lookup"><span data-stu-id="c94c2-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="c94c2-117">Este procedimiento se puede usar para probar los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c94c2-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="c94c2-118">Agrega todos los cmdlets del ensamblado a la sesión.</span><span class="sxs-lookup"><span data-stu-id="c94c2-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="c94c2-119">Para obtener más información sobre los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="c94c2-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c94c2-120">Vea también</span><span class="sxs-lookup"><span data-stu-id="c94c2-120">See also</span></span>

[<span data-ttu-id="c94c2-121">Cómo escribir un manifiesto de módulo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c94c2-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="c94c2-122">Importar un módulo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c94c2-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="c94c2-123">Import-Module</span><span class="sxs-lookup"><span data-stu-id="c94c2-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="c94c2-124">Instalación de módulos</span><span class="sxs-lookup"><span data-stu-id="c94c2-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="c94c2-125">Modificación de la ruta de instalación de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="c94c2-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="c94c2-126">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c94c2-126">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
