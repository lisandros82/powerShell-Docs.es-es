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
ms.openlocfilehash: 499a688ce5e8daa78baff58c454ad237836bbe48
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416160"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="0e6dd-102">Código de ejemplo GetProc01 (C#)</span><span class="sxs-lookup"><span data-stu-id="0e6dd-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="0e6dd-103">En el código siguiente se muestra la implementación del cmdlet de ejemplo GetProc01.</span><span class="sxs-lookup"><span data-stu-id="0e6dd-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="0e6dd-104">Tenga en cuenta que el cmdlet se simplifica al mantener el trabajo real de la recuperación del proceso en el método [System. Diagnostics. Process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) .</span><span class="sxs-lookup"><span data-stu-id="0e6dd-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="0e6dd-105">Puede descargar el C# archivo de código fuente (getproc01.CS) para este cmdlet Get-proc mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="0e6dd-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0e6dd-106">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0e6dd-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0e6dd-107">Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="0e6dd-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0e6dd-108">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="0e6dd-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="0e6dd-109">Vea también</span><span class="sxs-lookup"><span data-stu-id="0e6dd-109">See Also</span></span>

[<span data-ttu-id="0e6dd-110">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e6dd-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0e6dd-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0e6dd-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
