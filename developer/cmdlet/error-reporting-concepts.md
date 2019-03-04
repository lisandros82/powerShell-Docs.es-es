---
title: Conceptos de los informes de errores | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: aac6b7b6ac8a0fad15194b6d3f92c434524fabdb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855081"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="ac445-102">Conceptos de los informes de errores</span><span class="sxs-lookup"><span data-stu-id="ac445-102">Error Reporting Concepts</span></span>

<span data-ttu-id="ac445-103">Windows PowerShell proporciona dos mecanismos para notificar errores: un mecanismo para *la terminación* y otro mecanismo para *errores de no terminación*.</span><span class="sxs-lookup"><span data-stu-id="ac445-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="ac445-104">Es importante para el cmdlet para notificar los errores correctamente para que la aplicación host que se está ejecutando los cmdlets puede reaccionar de manera adecuada.</span><span class="sxs-lookup"><span data-stu-id="ac445-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="ac445-105">El cmdlet debe llamar a la [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método cuando produce un error que no tiene o no debe permitir que el cmdlet para continuar procesando sus objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="ac445-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="ac445-106">El cmdlet debe llamar a la [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método para informar de errores de no terminación cuando el cmdlet puede continuar procesando los objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="ac445-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="ac445-107">Ambos métodos proporcionan un registro de errores que la aplicación host puede utilizar para investigar la causa del error.</span><span class="sxs-lookup"><span data-stu-id="ac445-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="ac445-108">Utilice las siguientes directrices para determinar si un error es un carácter de terminación o error de no terminación.</span><span class="sxs-lookup"><span data-stu-id="ac445-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="ac445-109">Un error es un error de terminación si impide que el cmdlet dejar de procesar el objeto actual o procesar correctamente los objetos de entrada aún más, independientemente de su contenido.</span><span class="sxs-lookup"><span data-stu-id="ac445-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="ac445-110">Un error es un error de terminación si no desea que el cmdlet para continuar procesando el objeto actual o cualquier objeto de entrada adicional, independientemente de su contenido.</span><span class="sxs-lookup"><span data-stu-id="ac445-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="ac445-111">Un error es un error de terminación si se produce en un cmdlet que no se aceptan o devuelven un objeto o si se produce en un cmdlet que acepte o devuelve un único objeto.</span><span class="sxs-lookup"><span data-stu-id="ac445-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="ac445-112">Un error es un error de no terminación si desea que el cmdlet para continuar procesando el objeto actual y los objetos aún más la entrada.</span><span class="sxs-lookup"><span data-stu-id="ac445-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="ac445-113">Un error es un error de no terminación si está relacionado con un objeto de entrada específico o un subconjunto de objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="ac445-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac445-114">Véase también</span><span class="sxs-lookup"><span data-stu-id="ac445-114">See Also</span></span>

[<span data-ttu-id="ac445-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="ac445-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="ac445-116">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="ac445-116">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="ac445-117">Registros de errores de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="ac445-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="ac445-118">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac445-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
