---
title: Ejemplo de código RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: 2874f9df3f5166fbe14deb5b128674540c0d6701
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854041"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="99426-102">Ejemplo de código Runspace06</span><span class="sxs-lookup"><span data-stu-id="99426-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="99426-103">Aquí está el código fuente para el ejemplo Runspace06 que se describen en [configurar un espacio de ejecución mediante un Windows PowerShell Snap-in](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="99426-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="99426-104">Esta aplicación de ejemplo crea un espacio de ejecución en función de un complemento de Windows PowerShell, que, a continuación, se usa para ejecutar una canalización con un solo comando.</span><span class="sxs-lookup"><span data-stu-id="99426-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="99426-105">Para ello, la aplicación crea la información de configuración del espacio de ejecución, crea un espacio de ejecución, crea una canalización con un solo comando y, a continuación, ejecuta la canalización.</span><span class="sxs-lookup"><span data-stu-id="99426-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="99426-106">Puede descargar el C# el archivo de código fuente (runspace06.cs) mediante el Kit del desarrollo de Software de Windows para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="99426-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="99426-107">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="99426-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="99426-108">Puede descargar el C# el archivo de código fuente (runspace06.cs) mediante el Kit del desarrollo de Software de Windows para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="99426-108">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="99426-109">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="99426-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="99426-110">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="99426-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="99426-111">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="99426-111">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="99426-112">Véase también</span><span class="sxs-lookup"><span data-stu-id="99426-112">See Also</span></span>

[<span data-ttu-id="99426-113">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="99426-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="99426-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="99426-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)