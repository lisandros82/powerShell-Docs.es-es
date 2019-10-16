---
title: Informe de errores de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364274"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="d2e7a-102">Informes de errores de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2e7a-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="d2e7a-103">En los temas de esta sección se describe el modo en que los cmdlets notifican errores.</span><span class="sxs-lookup"><span data-stu-id="d2e7a-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d2e7a-104">En esta sección</span><span class="sxs-lookup"><span data-stu-id="d2e7a-104">In This Section</span></span>

<span data-ttu-id="d2e7a-105">[Conceptos de informes de errores](./error-reporting-concepts.md) Describe los dos mecanismos que los cmdlets pueden usar para notificar los errores.</span><span class="sxs-lookup"><span data-stu-id="d2e7a-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="d2e7a-106">[Errores de terminación](./terminating-errors.md) Describe el método utilizado para notificar los errores de terminación, donde se puede llamar a ese método desde dentro del cmdlet y excepciones que el tiempo de ejecución de Windows PowerShell puede devolver cuando se llama al método.</span><span class="sxs-lookup"><span data-stu-id="d2e7a-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="d2e7a-107">[Errores de no terminación](./non-terminating-errors.md) Describe el método utilizado para notificar los errores de no terminación y dónde se puede llamar al método desde dentro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d2e7a-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="d2e7a-108">[Mostrar información de errores por categoría](./displaying-error-information.md) Describe las formas en que los usuarios pueden mostrar errores.</span><span class="sxs-lookup"><span data-stu-id="d2e7a-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="d2e7a-109">[Registros de errores de Windows PowerShell](./windows-powershell-error-records.md) Describe los componentes de un registro de error.</span><span class="sxs-lookup"><span data-stu-id="d2e7a-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="d2e7a-110">[Interpretar objetos ErrorRecord](./interpreting-errorrecord-objects.md) Describe cómo se interpretan los objetos ErrorRecord.</span><span class="sxs-lookup"><span data-stu-id="d2e7a-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2e7a-111">Véase también</span><span class="sxs-lookup"><span data-stu-id="d2e7a-111">See Also</span></span>

[<span data-ttu-id="d2e7a-112">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2e7a-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
