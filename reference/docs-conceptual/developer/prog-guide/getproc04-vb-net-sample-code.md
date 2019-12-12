---
title: Código de ejemplo de GetProc04 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: f2164b97e4f3b3346e66d00834aa299659b62b33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416096"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="309c8-102">Código de ejemplo GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="309c8-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="309c8-103">En el código siguiente se muestra la implementación de un cmdlet `Get-Process` que informa de errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="309c8-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="309c8-104">Esta implementación llama al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) para informar de los errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="309c8-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="309c8-105">Puede descargar el C# archivo de código fuente (getprov04.CS) para este cmdlet Get-proc mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="309c8-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="309c8-106">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="309c8-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="309c8-107">Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="309c8-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="309c8-108">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="309c8-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="309c8-109">Véase también</span><span class="sxs-lookup"><span data-stu-id="309c8-109">See Also</span></span>

[<span data-ttu-id="309c8-110">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="309c8-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="309c8-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="309c8-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
