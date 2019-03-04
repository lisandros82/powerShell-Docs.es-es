---
title: GetProc03 (C#) código de ejemplo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: c24d18a2b80f8f9b62b5418fed35f54f7c7da23c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855411"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="ec440-102">Código de ejemplo GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="ec440-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="ec440-103">El código siguiente muestra la implementación de un `Get-Process` cmdlet que puede aceptar canaliza la entrada.</span><span class="sxs-lookup"><span data-stu-id="ec440-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="ec440-104">Esta implementación define un `Name` parámetro que acepta la entrada de la canalización, recupera información de proceso del equipo local en función de los nombres proporcionados y, a continuación, usa el [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como el mecanismo de salida para enviar objetos a la canalización.</span><span class="sxs-lookup"><span data-stu-id="ec440-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="ec440-105">Puede descargar el C# (getprov03.cs) de archivo de código fuente para este cmdlet Get-Proc usando el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="ec440-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ec440-106">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="ec440-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="ec440-107">Puede descargar el C# (getprov03.cs) de archivo de código fuente para este cmdlet Get-Proc usando el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="ec440-107">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ec440-108">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="ec440-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ec440-109">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="ec440-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ec440-110">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="ec440-110">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="ec440-111">Véase también</span><span class="sxs-lookup"><span data-stu-id="ec440-111">See Also</span></span>

[<span data-ttu-id="ec440-112">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec440-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ec440-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ec440-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)