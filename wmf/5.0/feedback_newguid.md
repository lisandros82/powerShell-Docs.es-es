---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680377"
---
# <a name="new-guid"></a><span data-ttu-id="63e04-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="63e04-102">New-Guid</span></span>
<span data-ttu-id="63e04-103">A menudo en un script (o quizás al escribir un recurso de DSC), tiene la necesidad de un identificador único.</span><span class="sxs-lookup"><span data-stu-id="63e04-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="63e04-104">Los GUID funcionan bien y es fácil llamar a la clase Guid de .NET Framework para generar uno. No obstante, tener un cmdlet facilita la detección a los usuarios finales que todavía no están familiarizados con la clase de .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="63e04-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="63e04-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="63e04-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="63e04-106">GUID</span><span class="sxs-lookup"><span data-stu-id="63e04-106">Guid</span></span>

----

<span data-ttu-id="63e04-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="63e04-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
