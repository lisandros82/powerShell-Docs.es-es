---
title: Instrucciones para el desarrollo de cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- development guidelines [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], development guidelines
ms.assetid: c30cc3c0-e958-4a8f-b81f-1e38de772f13
caps.latest.revision: 14
ms.openlocfilehash: 89c7682e87fa6f389349fc44275be0d2ffc83957
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369924"
---
# <a name="cmdlet-development-guidelines"></a><span data-ttu-id="5a4c9-102">Directrices de desarrollo del cmdlet</span><span class="sxs-lookup"><span data-stu-id="5a4c9-102">Cmdlet Development Guidelines</span></span>

<span data-ttu-id="5a4c9-103">En los temas de esta sección se proporcionan instrucciones de desarrollo que puede usar para generar cmdlets correctos.</span><span class="sxs-lookup"><span data-stu-id="5a4c9-103">The topics in this section provide development guidelines that you can use to produce well-formed cmdlets.</span></span> <span data-ttu-id="5a4c9-104">Al aprovechar la funcionalidad común proporcionada por el tiempo de ejecución de Windows PowerShell y siguiendo estas instrucciones, puede desarrollar cmdlets sólidos con un esfuerzo mínimo y proporcionar al usuario una experiencia coherente.</span><span class="sxs-lookup"><span data-stu-id="5a4c9-104">By leveraging the common functionality provided by the Windows PowerShell runtime and by following these guidelines, you can develop robust cmdlets with minimal effort and provide the user with a consistent experience.</span></span> <span data-ttu-id="5a4c9-105">Además, reducirá la carga de pruebas porque la funcionalidad común no requiere una reprueba.</span><span class="sxs-lookup"><span data-stu-id="5a4c9-105">Additionally, you will reduce the test burden because common functionality does not require retesting.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5a4c9-106">En esta sección</span><span class="sxs-lookup"><span data-stu-id="5a4c9-106">In This Section</span></span>

- [<span data-ttu-id="5a4c9-107">Instrucciones de desarrollo necesarias</span><span class="sxs-lookup"><span data-stu-id="5a4c9-107">Required Development Guidelines</span></span>](./required-development-guidelines.md)

- [<span data-ttu-id="5a4c9-108">Instrucciones de desarrollo muy recomendables</span><span class="sxs-lookup"><span data-stu-id="5a4c9-108">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

- [<span data-ttu-id="5a4c9-109">Instrucciones para el desarrollo de asesoría</span><span class="sxs-lookup"><span data-stu-id="5a4c9-109">Advisory Development Guidelines</span></span>](./advisory-development-guidelines.md)

## <a name="see-also"></a><span data-ttu-id="5a4c9-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="5a4c9-110">See Also</span></span>

[<span data-ttu-id="5a4c9-111">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a4c9-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="5a4c9-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5a4c9-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
