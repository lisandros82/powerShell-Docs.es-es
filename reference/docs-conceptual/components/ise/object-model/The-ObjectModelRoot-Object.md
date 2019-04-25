---
ms.date: 08/25/2017
keywords: powershell, cmdlet
title: El objeto ObjectModelRoot
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086789"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="f35f5-103">El objeto ObjectModelRoot</span><span class="sxs-lookup"><span data-stu-id="f35f5-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="f35f5-104">El objeto **$psISE**, que es el objeto raíz de entidad de seguridad en el Entorno de scripting integrado (ISE) de Windows PowerShell®, es una instancia de la clase Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="f35f5-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="f35f5-105">En este tema se describen las propiedades del objeto **ObjectModelRoot**.</span><span class="sxs-lookup"><span data-stu-id="f35f5-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="f35f5-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="f35f5-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="f35f5-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="f35f5-107">CurrentFile</span></span>

> <span data-ttu-id="f35f5-108">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="f35f5-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f35f5-109">La propiedad de solo lectura que obtiene el archivo, que está asociado a este objeto host que tiene actualmente el foco.</span><span class="sxs-lookup"><span data-stu-id="f35f5-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="f35f5-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="f35f5-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="f35f5-111">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="f35f5-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f35f5-112">La propiedad de solo lectura que obtiene de la pestaña de PowerShell que tiene el foco.</span><span class="sxs-lookup"><span data-stu-id="f35f5-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="f35f5-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="f35f5-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="f35f5-114">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="f35f5-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f35f5-115">La propiedad de solo lectura que obtiene la herramienta de complemento de Windows PowerShell ISE actualmente visible que se encuentra en el panel de herramientas horizontal en la parte inferior del editor.</span><span class="sxs-lookup"><span data-stu-id="f35f5-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="f35f5-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="f35f5-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="f35f5-117">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="f35f5-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f35f5-118">La propiedad de solo lectura que obtiene la herramienta de complemento de Windows PowerShell ISE actualmente visible que se encuentra en el panel de herramientas vertical en el lado derecho del editor.</span><span class="sxs-lookup"><span data-stu-id="f35f5-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="f35f5-119">Options</span><span class="sxs-lookup"><span data-stu-id="f35f5-119">Options</span></span>

> <span data-ttu-id="f35f5-120">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="f35f5-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f35f5-121">La propiedad de solo lectura que obtiene las distintas opciones que pueden cambiar la configuración de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f35f5-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="f35f5-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="f35f5-122">PowerShellTabs</span></span>

> <span data-ttu-id="f35f5-123">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="f35f5-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f35f5-124">La propiedad de solo lectura que obtiene la colección de las pestañas de PowerShell que están abiertas en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f35f5-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="f35f5-125">De forma predeterminada, este objeto contiene una pestaña de PowerShell. Sin embargo, puede agregar más pestañas de PowerShell a este objeto mediante scripts o mediante los menús de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f35f5-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="f35f5-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="f35f5-126">See Also</span></span>

- [<span data-ttu-id="f35f5-127">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f35f5-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f35f5-128">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="f35f5-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)