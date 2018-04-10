---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_scriptanalyzer_rule_profile
ms.openlocfilehash: ff575ab56f07312658d111bccd7793b64ac071ea
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a><span data-ttu-id="6a6d3-103">Perfil de las reglas ScryptAnalyzer para la Galería</span><span class="sxs-lookup"><span data-stu-id="6a6d3-103">ScriptAnazlyer Rule Profile for Gallery</span></span>
<span data-ttu-id="6a6d3-104">Para garantizar la calidad de los elementos que se publican en la Galería de PowerShell, ejecutamos reglas de [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) para determinar si se produce alguna infracción en los scripts que se envían.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="6a6d3-105">Puede encontrar la lista de reglas que ejecutamos en la [página de GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) de ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="6a6d3-106">Si tiene alguna duda sobre las reglas que ejecutamos, póngase en contacto con los administradores de la Galería de PowerShell, o bien abra una incidencia para ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="6a6d3-107">Los resultados de ScriptAnalyzer se mostrarán en la página de cada elemento individual de la Galería en la siguiente versión.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="6a6d3-108">Es muy recomendable que los propietarios de elementos comprueben que sus elementos publicados no contengan errores graves.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>