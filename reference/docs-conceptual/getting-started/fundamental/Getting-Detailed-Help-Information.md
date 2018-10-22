---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Obtener información de ayuda detallada
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: d2578604ec7c01c0b2734bd180e1babaca58b153
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851279"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="cd92d-103">Obtener información de ayuda detallada</span><span class="sxs-lookup"><span data-stu-id="cd92d-103">Getting detailed help information</span></span>

<span data-ttu-id="cd92d-104">PowerShell incluye temas de ayuda detallados que explican conceptos de PowerShell y el lenguaje de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd92d-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="cd92d-105">También hay artículos de Ayuda para cada cmdlet y proveedor, así como para muchas funciones y scripts.</span><span class="sxs-lookup"><span data-stu-id="cd92d-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="cd92d-106">Puede ver estos artículos de Ayuda en el símbolo del sistema o ver las versiones actualizadas más recientemente de estos artículos en la documentación en línea de [PowerShell](/powershell/scripting/powershell-scripting).</span><span class="sxs-lookup"><span data-stu-id="cd92d-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/powershell-scripting) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="cd92d-107">Obtención de ayuda para cmdlets</span><span class="sxs-lookup"><span data-stu-id="cd92d-107">Getting help for cmdlets</span></span>

<span data-ttu-id="cd92d-108">Para obtener ayuda acerca de los cmdlets de PowerShell, use el cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help).</span><span class="sxs-lookup"><span data-stu-id="cd92d-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="cd92d-109">Por ejemplo, para obtener ayuda para el cmdlet `Get-ChildItem`, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="cd92d-110">o</span><span class="sxs-lookup"><span data-stu-id="cd92d-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="cd92d-111">También puede obtener ayuda sobre el cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="cd92d-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="cd92d-112">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="cd92d-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="cd92d-113">Para obtener una lista de todos los artículos de Ayuda de cmdlets de la sesión, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="cd92d-114">Para mostrar una página de cada artículo de Ayuda cada vez, use la función `help` o su alias `man`.</span><span class="sxs-lookup"><span data-stu-id="cd92d-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="cd92d-115">Por ejemplo, para mostrar la Ayuda acerca del cmdlet `Get-ChildItem`, escriba</span><span class="sxs-lookup"><span data-stu-id="cd92d-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="cd92d-116">o</span><span class="sxs-lookup"><span data-stu-id="cd92d-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="cd92d-117">Para mostrar información detallada, use el parámetro **Detailed** del cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="cd92d-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="cd92d-118">Por ejemplo, para obtener información detallada acerca del cmdlet `Get-ChildItem`, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="cd92d-119">Para mostrar todo el contenido del artículo de Ayuda, use el parámetro **Full** del cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="cd92d-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="cd92d-120">Por ejemplo, para mostrar todo el contenido del artículo de Ayuda para el cmdlet `Get-ChildItem`, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="cd92d-121">Para obtener ayuda detallada acerca de los parámetros de un cmdlet, use el parámetro **Parameter** del cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="cd92d-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="cd92d-122">Por ejemplo, para obtener ayuda detallada acerca de todos los parámetros del cmdlet `Get-ChildItem`, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="cd92d-123">Para mostrar solo los ejemplos de un artículo de Ayuda, use el parámetro **Examples** de `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="cd92d-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="cd92d-124">Por ejemplo, para mostrar solo los ejemplos del artículo de Ayuda para el cmdlet `Get-ChildItem `, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-124">For example, to display only the examples in the Help article for the `Get-ChildItem `cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="cd92d-125">Para obtener información sobre cómo escribir artículos de Ayuda para los cmdlets que escribe, consulte [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets) (Cómo escribir ayuda para cmdlet).</span><span class="sxs-lookup"><span data-stu-id="cd92d-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="cd92d-126">Obtención de ayuda conceptual</span><span class="sxs-lookup"><span data-stu-id="cd92d-126">Getting conceptual help</span></span>

<span data-ttu-id="cd92d-127">El cmdlet `Get-Help` también muestra información acerca de artículos conceptuales en PowerShell, incluidos los artículos sobre el lenguaje de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd92d-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="cd92d-128">Los artículos de Ayuda conceptual comienzan por el prefijo "about_", como about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="cd92d-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="cd92d-129">(Los nombres de artículos conceptuales deben especificarse en inglés, incluso en versiones no inglesas de PowerShell).</span><span class="sxs-lookup"><span data-stu-id="cd92d-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="cd92d-130">Para mostrar una lista de artículos conceptuales, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="cd92d-131">Para mostrar un artículo de Ayuda determinado, escriba el nombre del artículo, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="cd92d-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="cd92d-132">Los parámetros de `Get-Help`, como **Detailed**, **Parameter** y **Examples**, no tienen ningún efecto en la presentación de artículos de Ayuda conceptuales.</span><span class="sxs-lookup"><span data-stu-id="cd92d-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="cd92d-133">Obtención de ayuda acerca de los proveedores</span><span class="sxs-lookup"><span data-stu-id="cd92d-133">Getting help about providers</span></span>

<span data-ttu-id="cd92d-134">El cmdlet `Get-Help` muestra información sobre los proveedores de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd92d-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="cd92d-135">Para obtener ayuda sobre un proveedor, escriba `Get-Help` seguido del nombre del proveedor.</span><span class="sxs-lookup"><span data-stu-id="cd92d-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="cd92d-136">Por ejemplo, para obtener ayuda sobre el proveedor del Registro, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="cd92d-137">Para obtener una lista de todos los artículos de Ayuda de proveedor de la sesión, escriba</span><span class="sxs-lookup"><span data-stu-id="cd92d-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="cd92d-138">Los parámetros de `Get-Help`, como **Detailed**, **Parameter** y **Examples**, no tienen ningún efecto en la presentación de artículos de Ayuda de proveedor.</span><span class="sxs-lookup"><span data-stu-id="cd92d-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="cd92d-139">Obtención de ayuda acerca de scripts y funciones</span><span class="sxs-lookup"><span data-stu-id="cd92d-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="cd92d-140">Muchos scripts y funciones de PowerShell tienen artículos de Ayuda.</span><span class="sxs-lookup"><span data-stu-id="cd92d-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="cd92d-141">Use el cmdlet `Get-Help` para mostrar los artículos de Ayuda de scripts y funciones.</span><span class="sxs-lookup"><span data-stu-id="cd92d-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="cd92d-142">Para mostrar la Ayuda de una función, escriba `Get-Help` seguido del nombre de función.</span><span class="sxs-lookup"><span data-stu-id="cd92d-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="cd92d-143">Por ejemplo, para obtener ayuda para la función `Disable-PSRemoting`, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="cd92d-144">Para mostrar la Ayuda de un script, escriba la ruta de acceso al archivo de script.</span><span class="sxs-lookup"><span data-stu-id="cd92d-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="cd92d-145">Si el script no está en una ruta de acceso mencionada en la variable de entorno Path, debe utilizar la ruta de acceso completa.</span><span class="sxs-lookup"><span data-stu-id="cd92d-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="cd92d-146">Por ejemplo, si tiene un script denominado "TestScript.ps1" en el directorio C:\\PS-Test, para mostrar el artículo de Ayuda del script, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="cd92d-147">Los parámetros que están diseñados para mostrar la ayuda del cmdlet también funcionan para la ayuda del script y de la función.</span><span class="sxs-lookup"><span data-stu-id="cd92d-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="cd92d-148">Sin embargo, la ayuda para las funciones y los scripts no se muestra cuando se ejecuta `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="cd92d-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="cd92d-149">Para obtener información sobre cómo escribir artículos de ayuda para sus funciones y scripts, consulte los siguientes artículos:</span><span class="sxs-lookup"><span data-stu-id="cd92d-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="cd92d-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="cd92d-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="cd92d-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="cd92d-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="cd92d-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="cd92d-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="cd92d-153">Obtención de ayuda en línea</span><span class="sxs-lookup"><span data-stu-id="cd92d-153">Getting help online</span></span>

<span data-ttu-id="cd92d-154">La visualización de los artículos de la Ayuda en línea es una de las mejores maneras de obtener ayuda.</span><span class="sxs-lookup"><span data-stu-id="cd92d-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="cd92d-155">Los artículos en línea son más fáciles de actualizar y proporcionan el contenido más actual.</span><span class="sxs-lookup"><span data-stu-id="cd92d-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="cd92d-156">Para obtener ayuda en línea, pruebe el parámetro **Online** del cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="cd92d-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="cd92d-157">Todos los artículos de Ayuda que vienen con PowerShell, como la Ayuda de proveedores y los artículos de Ayuda conceptual (Acerca de), están disponibles en línea en la documentación de [PowerShell](/powershell/scripting/powershell-scripting).</span><span class="sxs-lookup"><span data-stu-id="cd92d-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="cd92d-158">No se puede usar el parámetro **Online** con temas conceptuales (about_\*) ni artículos de Ayuda de proveedor.</span><span class="sxs-lookup"><span data-stu-id="cd92d-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="cd92d-159">La ayuda en línea es opcional, por tanto no funciona para todos los cmdlets, funciones o scripts.</span><span class="sxs-lookup"><span data-stu-id="cd92d-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="cd92d-160">Por ejemplo, para obtener la versión en línea del tema de Ayuda sobre el cmdlet `Get-ChildItem`, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="cd92d-161">PowerShell abre el artículo en el explorador predeterminado.</span><span class="sxs-lookup"><span data-stu-id="cd92d-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="cd92d-162">Si se admite la Ayuda en línea para un artículo de Ayuda, también puede ver la dirección URL del artículo de Ayuda.</span><span class="sxs-lookup"><span data-stu-id="cd92d-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="cd92d-163">La dirección URL aparece en la sección Vínculos relacionados de un artículo de Ayuda.</span><span class="sxs-lookup"><span data-stu-id="cd92d-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="cd92d-164">Por ejemplo, para ver la dirección URL de la versión en línea del cmdlet Add-Computer, escriba:</span><span class="sxs-lookup"><span data-stu-id="cd92d-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="cd92d-165">A continuación, se muestra la primera línea de la sección Vínculos relacionados del artículo.</span><span class="sxs-lookup"><span data-stu-id="cd92d-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="cd92d-166">Para más información sobre cómo proporcionar soporte técnico en línea para los artículos de Ayuda, consulte [about_Comment_Based_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="cd92d-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd92d-167">Vea también</span><span class="sxs-lookup"><span data-stu-id="cd92d-167">See also</span></span>

- [<span data-ttu-id="cd92d-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="cd92d-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="cd92d-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="cd92d-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="cd92d-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="cd92d-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="cd92d-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="cd92d-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
