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
ms.openlocfilehash: 20032913969606f722f3768b0433775aeaa8c3a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366484"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="34971-102">Ejemplo de código Runspace08</span><span class="sxs-lookup"><span data-stu-id="34971-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="34971-103">Este es el código fuente del ejemplo Runspace08 que se describe en [crear una aplicación de consola que agrega parámetros a un comando](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="34971-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="34971-104">En esta aplicación de ejemplo se crea un espacio de ejecución, se crea una canalización, se agregan dos comandos a la canalización, se agregan dos parámetros al segundo comando y, a continuación, se ejecuta la canalización.</span><span class="sxs-lookup"><span data-stu-id="34971-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="34971-105">Los comandos que se agregan a la canalización son los cmdlets `Get-Process` y `Sort-Object`.</span><span class="sxs-lookup"><span data-stu-id="34971-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="34971-106">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="34971-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="34971-107">Véase también</span><span class="sxs-lookup"><span data-stu-id="34971-107">See Also</span></span>

[<span data-ttu-id="34971-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="34971-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
