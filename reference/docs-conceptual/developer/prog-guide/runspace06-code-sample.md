---
title: Código de ejemplo de RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: f0197e6ca3535b72f843ba52e97381c0f2531598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366494"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="c8edf-102">Ejemplo de código Runspace06</span><span class="sxs-lookup"><span data-stu-id="c8edf-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="c8edf-103">Este es el código fuente del ejemplo Runspace06 que se describe en [configuración de un espacio de ejecución mediante un complemento de Windows PowerShell](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="c8edf-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="c8edf-104">Esta aplicación de ejemplo crea un espacio de ejecución basado en un complemento de Windows PowerShell, que se usa para ejecutar una canalización con un solo comando.</span><span class="sxs-lookup"><span data-stu-id="c8edf-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="c8edf-105">Para ello, la aplicación crea la información de configuración del espacio de ejecución, crea un espacio de ejecución, crea una canalización con un solo comando y, a continuación, ejecuta la canalización.</span><span class="sxs-lookup"><span data-stu-id="c8edf-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="c8edf-106">Puede descargar el archivo C# de código fuente (runspace06.CS) mediante el kit de desarrollo de software de Windows para Windows Vista y los componentes de tiempo de ejecución de Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="c8edf-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c8edf-107">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c8edf-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c8edf-108">Los archivos de origen descargados están disponibles en el directorio **@no__t ejemplos de 1PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="c8edf-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c8edf-109">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="c8edf-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="c8edf-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="c8edf-110">See Also</span></span>

[<span data-ttu-id="c8edf-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8edf-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c8edf-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c8edf-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
