---
title: Los módulos y complementos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860501"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="f1caf-102">Módulos y complementos</span><span class="sxs-lookup"><span data-stu-id="f1caf-102">Modules and Snap-ins</span></span>

<span data-ttu-id="f1caf-103">Los cmdlets se pueden agregar a una sesión mediante complementos o módulos (introducidos en Windows PowerShell 2.0). Una vez que el cmdlet se agrega a la sesión que se puede ejecutar mediante programación mediante una aplicación host o de forma interactiva en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="f1caf-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="f1caf-104">Se recomienda que use módulos como método de entrega para agregar cmdlets a una sesión por las razones siguientes:</span><span class="sxs-lookup"><span data-stu-id="f1caf-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="f1caf-105">Los módulos permiten agregar cmdlets al cargar el ensamblado donde se define el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1caf-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="f1caf-106">No hay ninguna necesidad de implementar una clase de complemento.</span><span class="sxs-lookup"><span data-stu-id="f1caf-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="f1caf-107">Los módulos permiten agregar otros recursos, como variables, funciones, scripts, tipos y formato archivos y mucho más.</span><span class="sxs-lookup"><span data-stu-id="f1caf-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="f1caf-108">Complementos pueden usarse únicamente para agregar los cmdlets y proveedores a la sesión.</span><span class="sxs-lookup"><span data-stu-id="f1caf-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1caf-109">Véase también</span><span class="sxs-lookup"><span data-stu-id="f1caf-109">See Also</span></span>

[<span data-ttu-id="f1caf-110">Escribir un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1caf-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="f1caf-111">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1caf-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
