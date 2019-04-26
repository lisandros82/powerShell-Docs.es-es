---
title: Errores de no terminación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067661"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="b9093-102">Errores de no terminación</span><span class="sxs-lookup"><span data-stu-id="b9093-102">Non-Terminating Errors</span></span>

<span data-ttu-id="b9093-103">En este tema se describe el método utilizado para notificar errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="b9093-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="b9093-104">También se explica cómo llamar al método desde el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b9093-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="b9093-105">Cuando se produce un error de no terminación, el cmdlet debe informar de este error mediante una llamada a la [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método.</span><span class="sxs-lookup"><span data-stu-id="b9093-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="b9093-106">Cuando el cmdlet notifica un error de no terminación, el cmdlet puede seguir funcionando en este objeto de entrada y en la entrada más objetos de canalización.</span><span class="sxs-lookup"><span data-stu-id="b9093-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="b9093-107">Si el cmdlet llama a la [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método, el cmdlet puede escribir un registro de error que describe la condición que provocó el error de no terminación.</span><span class="sxs-lookup"><span data-stu-id="b9093-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="b9093-108">Para obtener más información acerca de los registros de error, consulte [registros de Error de Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="b9093-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="b9093-109">Puede llamar los cmdlets [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) según sea necesario desde dentro de su métodos de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="b9093-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="b9093-110">Sin embargo, puede llamar los cmdlets [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) solo desde el subproceso que llama el [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="b9093-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="b9093-111">No llame a [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) desde otro subproceso.</span><span class="sxs-lookup"><span data-stu-id="b9093-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="b9093-112">En su lugar, comunicar errores hacia el subproceso principal.</span><span class="sxs-lookup"><span data-stu-id="b9093-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9093-113">Véase también</span><span class="sxs-lookup"><span data-stu-id="b9093-113">See Also</span></span>

[<span data-ttu-id="b9093-114">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="b9093-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="b9093-115">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="b9093-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="b9093-116">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="b9093-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="b9093-117">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="b9093-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="b9093-118">Registros de errores de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="b9093-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="b9093-119">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9093-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
