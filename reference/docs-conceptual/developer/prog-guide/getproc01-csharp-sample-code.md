---
title: Código deC#ejemplo de GetProc01 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 06a24266eb8fda6e4f138f1f77ae702f7454e525
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366804"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="18e83-102">Código de ejemplo GetProc01 (C#)</span><span class="sxs-lookup"><span data-stu-id="18e83-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="18e83-103">En el código siguiente se muestra la implementación del cmdlet de ejemplo GetProc01.</span><span class="sxs-lookup"><span data-stu-id="18e83-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="18e83-104">Tenga en cuenta que el cmdlet se simplifica al mantener el trabajo real de la recuperación del proceso en el método [System. Diagnostics. Process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) .</span><span class="sxs-lookup"><span data-stu-id="18e83-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="18e83-105">Puede descargar el C# archivo de código fuente (getproc01.CS) para este cmdlet Get-proc mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="18e83-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="18e83-106">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="18e83-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="18e83-107">Los archivos de origen descargados están disponibles en el directorio **@no__t ejemplos de 1PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="18e83-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="18e83-108">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="18e83-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="18e83-109">Véase también</span><span class="sxs-lookup"><span data-stu-id="18e83-109">See Also</span></span>

[<span data-ttu-id="18e83-110">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="18e83-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="18e83-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="18e83-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
