---
title: Runspace01 (C#) ejemplo de código | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 2f1839d1ba578cdfe97f60c741c84b0a57f1d8f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854221"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="2b0d0-102">Ejemplo de código Runspace01 (C#)</span><span class="sxs-lookup"><span data-stu-id="2b0d0-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="2b0d0-103">Estos son los ejemplos de código para el espacio de ejecución descrito en [crear una aplicación de consola que ejecuta un comando especificado](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="2b0d0-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="2b0d0-104">Para ello, la aplicación invoca un espacio de ejecución y, a continuación, invoca un comando.</span><span class="sxs-lookup"><span data-stu-id="2b0d0-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="2b0d0-105">(Tenga en cuenta que esta aplicación no especifica información de configuración del espacio de ejecución ni explícitamente crear una canalización).</span><span class="sxs-lookup"><span data-stu-id="2b0d0-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="2b0d0-106">Es el comando que se invoca el `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b0d0-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>
<span data-ttu-id="2b0d0-107">Estos son los ejemplos de código para el espacio de ejecución descrito en [crear una aplicación de consola que ejecuta un comando especificado](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="2b0d0-107">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="2b0d0-108">Para ello, la aplicación invoca un espacio de ejecución y, a continuación, invoca un comando.</span><span class="sxs-lookup"><span data-stu-id="2b0d0-108">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="2b0d0-109">(Tenga en cuenta que esta aplicación no especifica información de configuración del espacio de ejecución ni explícitamente crear una canalización).</span><span class="sxs-lookup"><span data-stu-id="2b0d0-109">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="2b0d0-110">Es el comando que se invoca el `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b0d0-110">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="2b0d0-111">Puede descargar el C# (runspace01.cs) de archivo de código fuente para este espacio de ejecución usando el Microsoft Windows Software Development Kit para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="2b0d0-111">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2b0d0-112">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2b0d0-112">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="2b0d0-113">Puede descargar el C# (runspace01.cs) de archivo de código fuente para este espacio de ejecución usando el Microsoft Windows Software Development Kit para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="2b0d0-113">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2b0d0-114">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2b0d0-114">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2b0d0-115">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="2b0d0-115">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="2b0d0-116">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="2b0d0-116">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="2b0d0-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="2b0d0-117">See Also</span></span>

[<span data-ttu-id="2b0d0-118">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b0d0-118">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2b0d0-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2b0d0-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)