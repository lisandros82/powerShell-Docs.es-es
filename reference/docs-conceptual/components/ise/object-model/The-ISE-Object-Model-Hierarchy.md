---
ms.date: 12/31/2019
keywords: powershell, cmdlet
title: La jerarquía del modelo de objetos de ISE
ms.openlocfilehash: 1ec5810fc5e7b765c2a08af83bce0415dd61a54b
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737039"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="1f0af-103">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="1f0af-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="1f0af-104">En este tema se muestra la jerarquía de objetos que forman parte del Entorno de scripting integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f0af-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="1f0af-105">Windows PowerShell ISE se incluye en Windows PowerShell 3.0, 4.0 y 5.1.</span><span class="sxs-lookup"><span data-stu-id="1f0af-105">Windows PowerShell ISE is included in Windows PowerShell 3.0, 4.0, and 5.1.</span></span> <span data-ttu-id="1f0af-106">Haga clic en un objeto para ir a la documentación de referencia de la clase que define el objeto.</span><span class="sxs-lookup"><span data-stu-id="1f0af-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="1f0af-107">Objeto $psISE</span><span class="sxs-lookup"><span data-stu-id="1f0af-107">$psISE Object</span></span>

<span data-ttu-id="1f0af-108">El objeto `$psISE` es el [objeto raíz](The-ObjectModelRoot-Object.md) de la jerarquía de objetos de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1f0af-108">The `$psISE` object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="1f0af-109">Ubicado en el nivel superior, este objeto hace que estén disponibles para scripting los objetos siguientes:</span><span class="sxs-lookup"><span data-stu-id="1f0af-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="1f0af-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="1f0af-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="1f0af-111">El objeto `$psISE.CurrentFile` es una instancia de la clase [ISEFile](The-ISEFile-Object.md).</span><span class="sxs-lookup"><span data-stu-id="1f0af-111">The `$psISE.CurrentFile` object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="1f0af-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="1f0af-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="1f0af-113">El objeto `$psISE.CurrentPowerShellTab` es una instancia de la clase [PowerShellTab](The-PowerShellTab-Object.md).</span><span class="sxs-lookup"><span data-stu-id="1f0af-113">The `$psISE.CurrentPowerShellTab` object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="1f0af-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="1f0af-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="1f0af-115">El objeto `$psISE.CurrentVisibleHorizontalTool` es una instancia de la clase [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="1f0af-115">The `$psISE.CurrentVisibleHorizontalTool` object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="1f0af-116">Representa la herramienta de complemento instalada que actualmente está acoplada al borde superior de la ventana de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1f0af-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="1f0af-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="1f0af-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="1f0af-118">El objeto `$psISE.CurrentVisibleHorizontalTool` es una instancia de la clase [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="1f0af-118">The `$psISE.CurrentVisibleHorizontalTool` object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="1f0af-119">Representa la herramienta de complemento instalada que actualmente está acoplada al borde derecho de la ventana de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1f0af-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="1f0af-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="1f0af-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="1f0af-121">El objeto `$psISE.Options` es una instancia de la clase [ISEOptions](The-ISEOptions-Object.md).</span><span class="sxs-lookup"><span data-stu-id="1f0af-121">The `$psISE.Options` object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span> <span data-ttu-id="1f0af-122">El objeto ISEOptions representa distintas configuraciones de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1f0af-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="1f0af-123">Es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="1f0af-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="1f0af-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="1f0af-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="1f0af-125">El objeto `$psISE.PowerShellTabs` es una instancia de la clase [PowerShellTabCollection](The-PowerShellTabCollection-Object.md).</span><span class="sxs-lookup"><span data-stu-id="1f0af-125">The `$psISE.PowerShellTabs` object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="1f0af-126">Es una colección de todas las pestañas de PowerShell abiertas actualmente que representan los entornos de ejecución de Windows PowerShell disponibles en el equipo local o en equipos remotos conectados.</span><span class="sxs-lookup"><span data-stu-id="1f0af-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="1f0af-127">Cada miembro de la colección es una instancia de la clase [PowerShellTab](The-PowerShellTab-Object.md).</span><span class="sxs-lookup"><span data-stu-id="1f0af-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f0af-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1f0af-128">See Also</span></span>

- [<span data-ttu-id="1f0af-129">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1f0af-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="1f0af-130">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="1f0af-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
