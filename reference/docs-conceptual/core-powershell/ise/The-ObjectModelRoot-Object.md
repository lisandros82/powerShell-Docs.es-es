---
ms.date: 2017-08-25
keywords: powershell,cmdlet
title: El objeto ObjectModelRoot
ms.openlocfilehash: eb3424ff147c35364fa08543d59ebd30f6d2d857
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="a11f7-103">El objeto ObjectModelRoot</span><span class="sxs-lookup"><span data-stu-id="a11f7-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="a11f7-104">El objeto **$psISE**, que es el objeto raíz de entidad de seguridad en el Entorno de scripting integrado (ISE) de Windows PowerShell®, es una instancia de la clase Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="a11f7-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="a11f7-105">En este tema se describen las propiedades del objeto **ObjectModelRoot**.</span><span class="sxs-lookup"><span data-stu-id="a11f7-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="a11f7-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a11f7-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="a11f7-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="a11f7-107">CurrentFile</span></span>

> <span data-ttu-id="a11f7-108">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="a11f7-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="a11f7-109">La propiedad de solo lectura que obtiene el archivo, que está asociado a este objeto host que tiene actualmente el foco.</span><span class="sxs-lookup"><span data-stu-id="a11f7-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="a11f7-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="a11f7-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="a11f7-111">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="a11f7-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="a11f7-112">La propiedad de solo lectura que obtiene de la pestaña de PowerShell que tiene el foco.</span><span class="sxs-lookup"><span data-stu-id="a11f7-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="a11f7-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="a11f7-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="a11f7-114">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="a11f7-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="a11f7-115">La propiedad de solo lectura que obtiene la herramienta de complemento de Windows PowerShell ISE actualmente visible que se encuentra en el panel de herramientas horizontal en la parte inferior del editor.</span><span class="sxs-lookup"><span data-stu-id="a11f7-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="a11f7-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="a11f7-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="a11f7-117">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="a11f7-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="a11f7-118">La propiedad de solo lectura que obtiene la herramienta de complemento de Windows PowerShell ISE actualmente visible que se encuentra en el panel de herramientas vertical en el lado derecho del editor.</span><span class="sxs-lookup"><span data-stu-id="a11f7-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="a11f7-119">Options</span><span class="sxs-lookup"><span data-stu-id="a11f7-119">Options</span></span>

> <span data-ttu-id="a11f7-120">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="a11f7-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="a11f7-121">La propiedad de solo lectura que obtiene las distintas opciones que pueden cambiar la configuración de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a11f7-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="a11f7-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="a11f7-122">PowerShellTabs</span></span>

> <span data-ttu-id="a11f7-123">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="a11f7-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="a11f7-124">La propiedad de solo lectura que obtiene la colección de las pestañas de PowerShell que están abiertas en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a11f7-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="a11f7-125">De forma predeterminada, este objeto contiene una pestaña de PowerShell. Sin embargo, puede agregar más pestañas de PowerShell a este objeto mediante scripts o mediante los menús de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a11f7-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="a11f7-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="a11f7-126">See Also</span></span>

- [<span data-ttu-id="a11f7-127">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a11f7-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="a11f7-128">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a11f7-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="a11f7-129">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="a11f7-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
