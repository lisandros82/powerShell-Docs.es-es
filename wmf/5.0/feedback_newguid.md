---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225596"
---
# <a name="new-guid"></a><span data-ttu-id="d95fc-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="d95fc-102">New-Guid</span></span>
<span data-ttu-id="d95fc-103">A menudo en un script (o quizás al escribir un recurso de DSC), tiene la necesidad de un identificador único.</span><span class="sxs-lookup"><span data-stu-id="d95fc-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="d95fc-104">Los GUID funcionan bien y es fácil llamar a la clase Guid de .NET Framework para generar uno. No obstante, tener un cmdlet facilita la detección a los usuarios finales que todavía no están familiarizados con la clase de .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d95fc-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="d95fc-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="d95fc-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="d95fc-106">GUID</span><span class="sxs-lookup"><span data-stu-id="d95fc-106">Guid</span></span>

----

<span data-ttu-id="d95fc-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="d95fc-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
