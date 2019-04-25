---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Perfil de las reglas de ScriptAnalyzer para la Galería
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084596"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="90c20-103">Perfil de las reglas de ScriptAnalyzer para la Galería</span><span class="sxs-lookup"><span data-stu-id="90c20-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="90c20-104">Para garantizar la calidad de los paquetes que se publican en la Galería de PowerShell, ejecutamos reglas de [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) para determinar si se produce alguna infracción en los scripts que se envían.</span><span class="sxs-lookup"><span data-stu-id="90c20-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="90c20-105">Puede encontrar la lista de reglas que ejecutamos en la [página de GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) de ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="90c20-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="90c20-106">Si tiene alguna duda sobre las reglas que ejecutamos, póngase en contacto con los administradores de la Galería de PowerShell, o bien abra una incidencia para ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="90c20-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="90c20-107">Los resultados de ScriptAnalyzer se mostrarán en la página de cada paquete individual de la Galería en la siguiente versión.</span><span class="sxs-lookup"><span data-stu-id="90c20-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="90c20-108">Es muy recomendable que los propietarios de paquetes comprueben que sus paquetes publicados no contengan errores graves.</span><span class="sxs-lookup"><span data-stu-id="90c20-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
