---
title: Conceptos de informes de errores | Microsoft Docs
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
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364624"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="eaef1-102">Conceptos de los informes de errores</span><span class="sxs-lookup"><span data-stu-id="eaef1-102">Error Reporting Concepts</span></span>

<span data-ttu-id="eaef1-103">Windows PowerShell proporciona dos mecanismos para notificar errores: un mecanismo para *Finalizar errores* y otro mecanismo para *errores de no terminación*.</span><span class="sxs-lookup"><span data-stu-id="eaef1-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="eaef1-104">Es importante que el cmdlet informe de los errores correctamente para que la aplicación host que ejecuta los cmdlets pueda reaccionar de manera adecuada.</span><span class="sxs-lookup"><span data-stu-id="eaef1-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="eaef1-105">El cmdlet debe llamar al método [System. Management. Automation. cmdlet. Throwterminatingerror \*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) cuando se produce un error que no permite que el cmdlet continúe procesando sus objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="eaef1-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="eaef1-106">El cmdlet debe llamar al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) para informar de los errores de no terminación cuando el cmdlet puede seguir procesando los objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="eaef1-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="eaef1-107">Ambos métodos proporcionan un registro de errores que la aplicación host puede usar para investigar la causa del error.</span><span class="sxs-lookup"><span data-stu-id="eaef1-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="eaef1-108">Utilice las siguientes directrices para determinar si un error es un error de terminación o de no terminación.</span><span class="sxs-lookup"><span data-stu-id="eaef1-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="eaef1-109">Un error es un error de terminación si impide que el cmdlet continúe procesando el objeto actual o procesa correctamente cualquier otro objeto de entrada, independientemente de su contenido.</span><span class="sxs-lookup"><span data-stu-id="eaef1-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="eaef1-110">Un error es un error de terminación si no desea que el cmdlet continúe procesando el objeto actual o cualquier otro objeto de entrada, independientemente de su contenido.</span><span class="sxs-lookup"><span data-stu-id="eaef1-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="eaef1-111">Un error es un error de terminación en caso de que se produzca en un cmdlet que no acepte o devuelva un objeto o que se produzca en un cmdlet que acepte o devuelva un solo objeto.</span><span class="sxs-lookup"><span data-stu-id="eaef1-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="eaef1-112">Un error es un error de no terminación si desea que el cmdlet siga procesando el objeto actual y los objetos de entrada adicionales.</span><span class="sxs-lookup"><span data-stu-id="eaef1-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="eaef1-113">Un error es un error de no terminación si está relacionado con un objeto de entrada o un subconjunto de objetos de entrada específicos.</span><span class="sxs-lookup"><span data-stu-id="eaef1-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="eaef1-114">Véase también</span><span class="sxs-lookup"><span data-stu-id="eaef1-114">See Also</span></span>

[<span data-ttu-id="eaef1-115">System. Management. Automation. cmdlet. Throwterminatingerror \*</span><span class="sxs-lookup"><span data-stu-id="eaef1-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="eaef1-116">System. Management. Automation. cmdlet. WriteError</span><span class="sxs-lookup"><span data-stu-id="eaef1-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="eaef1-117">Registros de errores de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eaef1-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="eaef1-118">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eaef1-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
