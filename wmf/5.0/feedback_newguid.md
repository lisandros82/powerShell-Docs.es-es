---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a><span data-ttu-id="0d201-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="0d201-102">New-Guid</span></span>
<span data-ttu-id="0d201-103">A menudo en un script (o quizás al escribir un recurso de DSC), tiene la necesidad de un identificador único.</span><span class="sxs-lookup"><span data-stu-id="0d201-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="0d201-104">Los GUID funcionan bien y es fácil llamar a la clase Guid de .NET Framework para generar uno. No obstante, tener un cmdlet facilita la detección a los usuarios finales que todavía no están familiarizados con la clase de .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0d201-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="0d201-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="0d201-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="0d201-106">GUID</span><span class="sxs-lookup"><span data-stu-id="0d201-106">Guid</span></span>

----

<span data-ttu-id="0d201-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="0d201-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>

