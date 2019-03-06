---
title: GetProc01 código de ejemplo (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 2411642c39737e7dc03bd0bb4ea753ed27783732
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429795"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="f7e05-102">Código de ejemplo GetProc01 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="f7e05-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="f7e05-103">El código siguiente muestra la implementación del cmdlet de ejemplo GetProc01.</span><span class="sxs-lookup"><span data-stu-id="f7e05-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="f7e05-104">Tenga en cuenta que el cmdlet se ha simplificado al dejar el trabajo real de recuperación de proceso para el [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) método.</span><span class="sxs-lookup"><span data-stu-id="f7e05-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="f7e05-105">Puede descargar el C# (getproc01.cs) de archivo de código fuente para este cmdlet Get-Proc usando el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="f7e05-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f7e05-106">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="f7e05-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f7e05-107">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="f7e05-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f7e05-108">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="f7e05-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="f7e05-109">Véase también</span><span class="sxs-lookup"><span data-stu-id="f7e05-109">See Also</span></span>

[<span data-ttu-id="f7e05-110">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7e05-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f7e05-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f7e05-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)