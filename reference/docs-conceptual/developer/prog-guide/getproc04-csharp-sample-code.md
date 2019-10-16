---
title: Código deC#ejemplo de GetProc04 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: e8d9ae69c0d9da23b3e9a807e30ee76ba83af604
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366784"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="e0fb0-102">Código de ejemplo GetProc04 (C#)</span><span class="sxs-lookup"><span data-stu-id="e0fb0-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="e0fb0-103">En el código siguiente se muestra la implementación de un cmdlet `Get-Process` que informa de errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="e0fb0-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="e0fb0-104">Esta implementación llama al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) para informar de los errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="e0fb0-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="e0fb0-105">Puede descargar el C# archivo de código fuente (getprov04.CS) para este cmdlet Get-proc mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="e0fb0-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e0fb0-106">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e0fb0-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e0fb0-107">Los archivos de origen descargados están disponibles en el directorio **@no__t ejemplos de 1PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="e0fb0-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e0fb0-108">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="e0fb0-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="e0fb0-109">Véase también</span><span class="sxs-lookup"><span data-stu-id="e0fb0-109">See Also</span></span>

[<span data-ttu-id="e0fb0-110">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0fb0-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e0fb0-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e0fb0-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
