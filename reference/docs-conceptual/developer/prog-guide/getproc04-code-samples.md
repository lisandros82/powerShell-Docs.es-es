---
title: Ejemplos de código de GetProc04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360324"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="c7b33-102">Ejemplos de código GetProc04</span><span class="sxs-lookup"><span data-stu-id="c7b33-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="c7b33-103">Estos son los ejemplos de código para el cmdlet de ejemplo GetProc04.</span><span class="sxs-lookup"><span data-stu-id="c7b33-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="c7b33-104">Este es el ejemplo de cmdlet `Get-Process` que se describe en [Agregar informes de errores de no terminación al cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="c7b33-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="c7b33-105">Este cmdlet `Get-Process` llama al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) siempre que se produce una excepción de operación no válida al recuperar la información de proceso.</span><span class="sxs-lookup"><span data-stu-id="c7b33-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="c7b33-106">Puede descargar el C# archivo de código fuente (getprov04.CS) para este cmdlet Get-proc mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="c7b33-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c7b33-107">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c7b33-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c7b33-108">Los archivos de origen descargados están disponibles en el directorio **@no__t ejemplos de 1PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="c7b33-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="c7b33-109">Para obtener el código de ejemplo completo, vea los temas siguientes.</span><span class="sxs-lookup"><span data-stu-id="c7b33-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="c7b33-110">Language</span><span class="sxs-lookup"><span data-stu-id="c7b33-110">Language</span></span>|<span data-ttu-id="c7b33-111">Tema</span><span class="sxs-lookup"><span data-stu-id="c7b33-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="c7b33-112">C#</span><span class="sxs-lookup"><span data-stu-id="c7b33-112">C#</span></span>|[<span data-ttu-id="c7b33-113">Código deC#ejemplo GetProc04 ()</span><span class="sxs-lookup"><span data-stu-id="c7b33-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="c7b33-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="c7b33-114">VB.NET</span></span>|[<span data-ttu-id="c7b33-115">Código de ejemplo de GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="c7b33-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="c7b33-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="c7b33-116">See Also</span></span>

[<span data-ttu-id="c7b33-117">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7b33-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c7b33-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c7b33-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)