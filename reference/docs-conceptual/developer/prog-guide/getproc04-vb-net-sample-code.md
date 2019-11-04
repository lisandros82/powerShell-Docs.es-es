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
ms.openlocfilehash: 0d0d1a3f82bc2cee025139d69fee02eb601fa563
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360304"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="3747f-102">Código de ejemplo GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="3747f-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="3747f-103">En el código siguiente se muestra la implementación de un cmdlet `Get-Process` que informa de errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="3747f-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="3747f-104">Esta implementación llama al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) para informar de los errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="3747f-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="3747f-105">Puede descargar el C# archivo de código fuente (getprov04.CS) para este cmdlet Get-proc mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="3747f-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3747f-106">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3747f-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3747f-107">Los archivos de origen descargados están disponibles en el directorio **@no__t ejemplos de 1PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="3747f-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3747f-108">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="3747f-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="3747f-109">Véase también</span><span class="sxs-lookup"><span data-stu-id="3747f-109">See Also</span></span>

[<span data-ttu-id="3747f-110">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3747f-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3747f-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3747f-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)