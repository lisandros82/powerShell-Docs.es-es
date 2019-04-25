---
title: GetProc04 código de ejemplo (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 0d0d1a3f82bc2cee025139d69fee02eb601fa563
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081536"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="ecea8-102">Código de ejemplo GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="ecea8-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="ecea8-103">El código siguiente muestra la implementación de un `Get-Process` cmdlet que informa de errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="ecea8-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="ecea8-104">Esta implementación llama a la [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método para notificar errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="ecea8-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="ecea8-105">Puede descargar el C# (getprov04.cs) de archivo de código fuente para este cmdlet Get-Proc usando el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="ecea8-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ecea8-106">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="ecea8-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ecea8-107">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="ecea8-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ecea8-108">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="ecea8-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="ecea8-109">Véase también</span><span class="sxs-lookup"><span data-stu-id="ecea8-109">See Also</span></span>

[<span data-ttu-id="ecea8-110">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ecea8-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ecea8-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ecea8-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)