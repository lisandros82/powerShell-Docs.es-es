---
title: Código de ejemplo de RunSpace09 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 122a40dea93d874a7c131774e3d1abb148bcd4fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360134"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="42364-102">Ejemplo de código Runspace09</span><span class="sxs-lookup"><span data-stu-id="42364-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="42364-103">Este es el código fuente del ejemplo Runspace09 que se describe en [crear una aplicación de consola que invoca una canalización de forma asincrónica](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="42364-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="42364-104">En esta aplicación de ejemplo se crea y se abre un espacio de ejecución, se crea y se invoca de forma asincrónica una canalización y, a continuación, se usan eventos de canalización para procesar el script de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="42364-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="42364-105">El script que ejecuta esta aplicación crea los enteros comprendidos entre 1 y 10 en intervalos de 0,5 segundos (500 ms).</span><span class="sxs-lookup"><span data-stu-id="42364-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="42364-106">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="42364-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="42364-107">Véase también</span><span class="sxs-lookup"><span data-stu-id="42364-107">See Also</span></span>

[<span data-ttu-id="42364-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="42364-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
