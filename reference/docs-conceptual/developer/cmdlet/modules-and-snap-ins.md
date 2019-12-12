---
title: Módulos y complementos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365374"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="f2025-102">Módulos y complementos</span><span class="sxs-lookup"><span data-stu-id="f2025-102">Modules and Snap-ins</span></span>

<span data-ttu-id="f2025-103">Los cmdlets se pueden agregar a una sesión mediante módulos (introducidos por Windows PowerShell 2,0) o complementos. Una vez que el cmdlet se agrega a la sesión, se puede ejecutar mediante programación en una aplicación host o de forma interactiva en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="f2025-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="f2025-104">Se recomienda usar módulos como método de entrega para agregar cmdlets a una sesión por los siguientes motivos:</span><span class="sxs-lookup"><span data-stu-id="f2025-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="f2025-105">Los módulos permiten agregar cmdlets cargando el ensamblado donde se define el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2025-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="f2025-106">No es necesario implementar una clase de complemento.</span><span class="sxs-lookup"><span data-stu-id="f2025-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="f2025-107">Los módulos permiten agregar otros recursos, como variables, funciones, scripts, tipos y archivos de formato, etc.</span><span class="sxs-lookup"><span data-stu-id="f2025-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="f2025-108">Los complementos solo se pueden usar para agregar cmdlets y proveedores a la sesión.</span><span class="sxs-lookup"><span data-stu-id="f2025-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2025-109">Véase también</span><span class="sxs-lookup"><span data-stu-id="f2025-109">See Also</span></span>

[<span data-ttu-id="f2025-110">Escribir un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2025-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="f2025-111">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2025-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
