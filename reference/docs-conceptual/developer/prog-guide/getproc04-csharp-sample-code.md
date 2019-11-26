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
ms.openlocfilehash: 0ca2ccc5188f0c1784ec14ac204c1fdd624c2e66
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416114"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="e0d39-102">Código de ejemplo GetProc04 (C#)</span><span class="sxs-lookup"><span data-stu-id="e0d39-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="e0d39-103">En el código siguiente se muestra la implementación de un cmdlet `Get-Process` que informa de errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="e0d39-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="e0d39-104">Esta implementación llama al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) para informar de los errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="e0d39-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="e0d39-105">Puede descargar el C# archivo de código fuente (getprov04.CS) para este cmdlet Get-proc mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="e0d39-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e0d39-106">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e0d39-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e0d39-107">Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="e0d39-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e0d39-108">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="e0d39-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="e0d39-109">Vea también</span><span class="sxs-lookup"><span data-stu-id="e0d39-109">See Also</span></span>

[<span data-ttu-id="e0d39-110">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0d39-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e0d39-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e0d39-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
