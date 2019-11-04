---
title: Ejemplo deC#código Runspace01 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 39e7d49b51942da51a581ab33dbe46ab848ca1c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366644"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="13e3b-102">Ejemplo de código Runspace01 (C#)</span><span class="sxs-lookup"><span data-stu-id="13e3b-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="13e3b-103">Estos son los ejemplos de código para el espacio de ejecución que se describe en [crear una aplicación de consola que ejecuta un comando especificado](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="13e3b-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="13e3b-104">Para ello, la aplicación invoca un espacio de ejecución y, a continuación, invoca un comando.</span><span class="sxs-lookup"><span data-stu-id="13e3b-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="13e3b-105">(Tenga en cuenta que esta aplicación no especifica información de configuración del espacio de ejecución ni crea explícitamente una canalización).</span><span class="sxs-lookup"><span data-stu-id="13e3b-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="13e3b-106">El comando que se invoca es el cmdlet `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="13e3b-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="13e3b-107">Puede descargar el C# archivo de código fuente (runspace01.CS) de este espacio de ejecución mediante el kit de desarrollo de software de Microsoft Windows para los componentes de tiempo de ejecución de Windows Vista y Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="13e3b-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="13e3b-108">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="13e3b-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="13e3b-109">Los archivos de origen descargados están disponibles en el directorio **@no__t ejemplos de 1PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="13e3b-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="13e3b-110">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="13e3b-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="13e3b-111">Véase también</span><span class="sxs-lookup"><span data-stu-id="13e3b-111">See Also</span></span>

[<span data-ttu-id="13e3b-112">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="13e3b-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="13e3b-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="13e3b-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)