---
title: Informes de errores de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856161"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="65c39-102">Informes de errores de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="65c39-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="65c39-103">Los temas de esta sección describen cómo los cmdlets informan de errores.</span><span class="sxs-lookup"><span data-stu-id="65c39-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="65c39-104">En esta sección</span><span class="sxs-lookup"><span data-stu-id="65c39-104">In This Section</span></span>

<span data-ttu-id="65c39-105">[Conceptos de error Reporting](./error-reporting-concepts.md) se describen los dos mecanismos que puede usar los cmdlets para informar de errores.</span><span class="sxs-lookup"><span data-stu-id="65c39-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="65c39-106">[La terminación](./terminating-errors.md) describe el método utilizado para notificar la terminación de errores, donde ese método puede llamarse desde dentro el cmdlet y las excepciones que se pueden devolver el tiempo de ejecución de Windows PowerShell cuando se llama al método.</span><span class="sxs-lookup"><span data-stu-id="65c39-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="65c39-107">[Errores de no terminación](./non-terminating-errors.md) describe el método utilizado para notificar errores de no terminación y que ese método puede llamarse desde dentro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="65c39-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="65c39-108">[Mostrar información de Error por categoría](./displaying-error-information.md) se describen las formas en que los usuarios pueden mostrar el error.</span><span class="sxs-lookup"><span data-stu-id="65c39-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="65c39-109">[Registros de Error de Windows PowerShell](./windows-powershell-error-records.md) describe los componentes de un registro de errores.</span><span class="sxs-lookup"><span data-stu-id="65c39-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="65c39-110">[Interpretación de los objetos de ErrorRecord](./interpreting-errorrecord-objects.md) explica cómo se interpretan ErrorRecord objetos.</span><span class="sxs-lookup"><span data-stu-id="65c39-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="65c39-111">Véase también</span><span class="sxs-lookup"><span data-stu-id="65c39-111">See Also</span></span>

[<span data-ttu-id="65c39-112">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="65c39-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
