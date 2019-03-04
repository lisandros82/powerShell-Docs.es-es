---
title: Ejemplo de código RunSpace09 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854051"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="ba181-102">Ejemplo de código Runspace09</span><span class="sxs-lookup"><span data-stu-id="ba181-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="ba181-103">Aquí está el código fuente para el ejemplo Runspace09 que se describen en [creación de una consola de aplicación que invoca una canalización de forma asincrónica](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="ba181-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="ba181-104">Esta aplicación de ejemplo crea y abre un espacio de ejecución, crea y lo invoca una canalización de forma asincrónica y, a continuación, la canalización usa eventos para procesar la secuencia de comandos de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="ba181-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="ba181-105">El script que se ejecuta esta aplicación crea los enteros del 1 al 10 en intervalos de 0,5 segundos (500 ms).</span><span class="sxs-lookup"><span data-stu-id="ba181-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="ba181-106">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="ba181-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="ba181-107">Véase también</span><span class="sxs-lookup"><span data-stu-id="ba181-107">See Also</span></span>

[<span data-ttu-id="ba181-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ba181-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)