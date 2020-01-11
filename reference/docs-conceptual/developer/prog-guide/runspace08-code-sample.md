---
title: Código de ejemplo de RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 2e9cd80f1869e0d859187eea89eca414a84cb4ab
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870596"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="af2cb-102">Ejemplo de código Runspace08</span><span class="sxs-lookup"><span data-stu-id="af2cb-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="af2cb-103">Este es el código fuente del ejemplo Runspace08 que se describe en [crear una aplicación de consola que agrega parámetros a un comando](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="af2cb-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="af2cb-104">En esta aplicación de ejemplo se crea un espacio de ejecución, se crea una canalización, se agregan dos comandos a la canalización, se agregan dos parámetros al segundo comando y, a continuación, se ejecuta la canalización.</span><span class="sxs-lookup"><span data-stu-id="af2cb-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="af2cb-105">Los comandos que se agregan a la canalización son los cmdlets `Get-Process` y `Sort-Object`.</span><span class="sxs-lookup"><span data-stu-id="af2cb-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="af2cb-106">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="af2cb-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="af2cb-107">Vea también</span><span class="sxs-lookup"><span data-stu-id="af2cb-107">See Also</span></span>

[<span data-ttu-id="af2cb-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="af2cb-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
