---
title: GetProc01 (C#) código de ejemplo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 32c8214935a8c9f455426b76966d8c7fb33353d4
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430084"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="91f1e-102">Código de ejemplo GetProc01 (C#)</span><span class="sxs-lookup"><span data-stu-id="91f1e-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="91f1e-103">El código siguiente muestra la implementación del cmdlet de ejemplo GetProc01.</span><span class="sxs-lookup"><span data-stu-id="91f1e-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="91f1e-104">Tenga en cuenta que el cmdlet se ha simplificado al dejar el trabajo real de recuperación de proceso para el [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) método.</span><span class="sxs-lookup"><span data-stu-id="91f1e-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="91f1e-105">Puede descargar el C# (getproc01.cs) de archivo de código fuente para este cmdlet Get-Proc usando el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="91f1e-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="91f1e-106">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="91f1e-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="91f1e-107">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="91f1e-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="91f1e-108">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="91f1e-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="91f1e-109">Véase también</span><span class="sxs-lookup"><span data-stu-id="91f1e-109">See Also</span></span>

[<span data-ttu-id="91f1e-110">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="91f1e-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="91f1e-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="91f1e-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)