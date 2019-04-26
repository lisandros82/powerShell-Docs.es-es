---
title: Ejemplos de código GetProc04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081672"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="26850-102">Ejemplos de código GetProc04</span><span class="sxs-lookup"><span data-stu-id="26850-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="26850-103">Estos son los ejemplos de código para el cmdlet de ejemplo GetProc04.</span><span class="sxs-lookup"><span data-stu-id="26850-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="26850-104">Se trata de la `Get-Process` ejemplo de cmdlet que se describen en [adición de no terminación informe de errores para el Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="26850-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="26850-105">Esto `Get-Process` cmdlet llamadas la [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método cada vez que se produce una excepción de operación no válida al recuperar la información de proceso.</span><span class="sxs-lookup"><span data-stu-id="26850-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="26850-106">Puede descargar el C# (getprov04.cs) de archivo de código fuente para este cmdlet Get-Proc usando el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="26850-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="26850-107">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="26850-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="26850-108">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="26850-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="26850-109">Para el código de ejemplo completo, vea los temas siguientes.</span><span class="sxs-lookup"><span data-stu-id="26850-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="26850-110">Language</span><span class="sxs-lookup"><span data-stu-id="26850-110">Language</span></span>|<span data-ttu-id="26850-111">Tema</span><span class="sxs-lookup"><span data-stu-id="26850-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="26850-112">C#</span><span class="sxs-lookup"><span data-stu-id="26850-112">C#</span></span>|[<span data-ttu-id="26850-113">GetProc04 (C#) código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="26850-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="26850-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="26850-114">VB.NET</span></span>|[<span data-ttu-id="26850-115">GetProc04 código de ejemplo (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="26850-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="26850-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="26850-116">See Also</span></span>

[<span data-ttu-id="26850-117">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="26850-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="26850-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="26850-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)