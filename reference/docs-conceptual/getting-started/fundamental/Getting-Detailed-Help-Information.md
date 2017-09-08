---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Obtener información de ayuda detallada"
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: c786ce089073abccdf186dc1d9e8ee383f83655d
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2017
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="47479-103">Obtener información de ayuda detallada</span><span class="sxs-lookup"><span data-stu-id="47479-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="47479-104">Windows PowerShell incluye temas de ayuda detallados que explican conceptos de Windows PowerShell y el lenguaje de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47479-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="47479-105">También hay temas de Ayuda para cada cmdlet y proveedor y temas de Ayuda para muchas funciones y scripts.</span><span class="sxs-lookup"><span data-stu-id="47479-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="47479-106">Puede ver estos temas de Ayuda en el símbolo del sistema o ver las versiones actualizadas más recientemente de estos temas en la biblioteca de Microsoft Technet.</span><span class="sxs-lookup"><span data-stu-id="47479-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="47479-107">Muchos programas que hospedan Windows PowerShell, como el Entorno de scripting integrado de Windows PowerShell, proporcionan características adicionales de ayuda, como la ayuda contextual y el archivo de ayuda compilado (.chm).</span><span class="sxs-lookup"><span data-stu-id="47479-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="47479-108">Obtener ayuda para cmdlets</span><span class="sxs-lookup"><span data-stu-id="47479-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="47479-109">Para obtener ayuda acerca de los cmdlets de Windows PowerShell, use el cmdlet [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2).</span><span class="sxs-lookup"><span data-stu-id="47479-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="47479-110">Por ejemplo, para obtener ayuda para el cmdlet [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc), escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="47479-111">o</span><span class="sxs-lookup"><span data-stu-id="47479-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="47479-112">También puede obtener ayuda sobre el cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="47479-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="47479-113">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="47479-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="47479-114">Para obtener una lista de todos los temas de Ayuda de cmdlets de la sesión, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="47479-115">Para mostrar una página de cada tema de Ayuda cada vez, use la función **help** o su alias **man**.</span><span class="sxs-lookup"><span data-stu-id="47479-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="47479-116">Por ejemplo, para mostrar la Ayuda del cmdlet Get-ChildItem, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="47479-117">o</span><span class="sxs-lookup"><span data-stu-id="47479-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="47479-118">Para mostrar información detallada sobre un cmdlet, una función o un script, incluidas las descripciones de sus parámetros y ejemplos de su uso, emplee el parámetro *Detailed* del cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="47479-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="47479-119">Por ejemplo, para obtener información detallada sobre el cmdlet Get-ChildItem, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="47479-120">Para mostrar todo el contenido del tema de Ayuda, use el parámetro *Full* del cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="47479-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="47479-121">Por ejemplo, para mostrar todo el contenido del tema de Ayuda para el cmdlet Get-ChildItem, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="47479-122">Para obtener Ayuda detallada sobre los parámetros de un cmdlet, use el parámetro *Parameter* del cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="47479-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="47479-123">Por ejemplo, para obtener Ayuda detallada de todos los parámetros del cmdlet Get-ChildItem, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="47479-124">Para mostrar solo los ejemplos de un tema de Ayuda, use el parámetro *Example* de Get-Help.</span><span class="sxs-lookup"><span data-stu-id="47479-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="47479-125">Por ejemplo, para mostrar solo los ejemplos del tema de Ayuda para el cmdlet Get-ChildItem, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="47479-126">Para obtener información sobre cómo escribir temas de ayuda para los cmdlets que escribe, vea [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Cómo escribir ayuda para cmdlet) en la biblioteca de MSDN.</span><span class="sxs-lookup"><span data-stu-id="47479-126">For information about how to write Help topics for the cmdlets that you write, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="47479-127">Obtener ayuda conceptual</span><span class="sxs-lookup"><span data-stu-id="47479-127">Getting Conceptual Help</span></span>
<span data-ttu-id="47479-128">El cmdlet Get-Help también muestra información sobre temas conceptuales en Windows PowerShell, incluidos los temas sobre el lenguaje de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47479-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="47479-129">Los temas de Ayuda conceptual comienzan por el prefijo "about_", como about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="47479-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="47479-130">(Los nombres de temas conceptuales deben especificarse en inglés, incluso en versiones no inglesas de Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="47479-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="47479-131">Para mostrar una lista de temas conceptuales, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="47479-132">Para mostrar un tema de Ayuda determinado, escriba el nombre del tema, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="47479-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="47479-133">Los parámetros de Get-Help, como *Detailed*, *Parameter* y *Examples*, no tienen ningún efecto en la presentación de temas de Ayuda conceptuales.</span><span class="sxs-lookup"><span data-stu-id="47479-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="47479-134">Obtener ayuda acerca de los proveedores</span><span class="sxs-lookup"><span data-stu-id="47479-134">Getting Help About Providers</span></span>
<span data-ttu-id="47479-135">El cmdlet Get-Help muestra información sobre los proveedores de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47479-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="47479-136">Para obtener ayuda sobre un proveedor, escriba "Get-Help" seguido del nombre del proveedor.</span><span class="sxs-lookup"><span data-stu-id="47479-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="47479-137">Por ejemplo, para obtener ayuda sobre el proveedor del Registro, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="47479-138">Para obtener una lista de todos los temas de Ayuda de la sesión, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="47479-139">Los parámetros de Get\-Help, como *Detailed*, *Parameter* y *Examples*, no tienen ningún efecto en la presentación de temas de Ayuda de proveedor.</span><span class="sxs-lookup"><span data-stu-id="47479-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="47479-140">Obtener ayuda acerca de scripts y funciones</span><span class="sxs-lookup"><span data-stu-id="47479-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="47479-141">Muchos scripts y funciones de Windows PowerShell tienen temas de Ayuda.</span><span class="sxs-lookup"><span data-stu-id="47479-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="47479-142">Use el cmdlet Get-Help para visualizar los temas de Ayuda de scripts y funciones.</span><span class="sxs-lookup"><span data-stu-id="47479-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="47479-143">Para visualizar la Ayuda de una función, escriba "get-help" seguido del nombre de función.</span><span class="sxs-lookup"><span data-stu-id="47479-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="47479-144">Por ejemplo, para obtener Ayuda para la función Disable-PSRemoting, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="47479-145">Para visualizar la Ayuda de un script, escriba la ruta de acceso completa al archivo de script.</span><span class="sxs-lookup"><span data-stu-id="47479-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="47479-146">Si el script está en una ruta de acceso que aparece en la variable de entorno Path, puede omitir la ruta de acceso del comando.</span><span class="sxs-lookup"><span data-stu-id="47479-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="47479-147">Por ejemplo, si tiene un script denominado "TestScript.ps1" en el directorio C:\\PS-Test, para visualizar el tema de Ayuda del script, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="47479-148">Los parámetros diseñados para mostrar la Ayuda de cmdlets, como *Detailed*, *Full*, *Examples* y *Parameter*, también funcionan para la Ayuda de scripts y funciones.</span><span class="sxs-lookup"><span data-stu-id="47479-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="47479-149">Sin embargo, al escribir "get-help \*" para que se muestre toda la Ayuda, la Ayuda de funciones y scripts no aparece.</span><span class="sxs-lookup"><span data-stu-id="47479-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="47479-150">Para obtener información sobre cómo escribir la Ayuda de scripts y funciones, vea [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af) y [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span><span class="sxs-lookup"><span data-stu-id="47479-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="47479-151">Obtener ayuda en línea</span><span class="sxs-lookup"><span data-stu-id="47479-151">Getting Help Online</span></span>
<span data-ttu-id="47479-152">Si está conectado a Internet, una de las mejores formas de obtener Ayuda es ver los temas de Ayuda en línea.</span><span class="sxs-lookup"><span data-stu-id="47479-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="47479-153">Dado que los temas en línea son fáciles de actualizar, es probable que proporcionen el contenido más actualizado.</span><span class="sxs-lookup"><span data-stu-id="47479-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="47479-154">Para obtener Ayuda en línea, pruebe el parámetro *Online* del cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="47479-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="47479-155">El parámetro *Online* del cmdlet Get-Help funciona solo para la Ayuda de cmdlets, funciones y scripts.</span><span class="sxs-lookup"><span data-stu-id="47479-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="47479-156">No se puede usar el parámetro *Online* con temas conceptuales (Acerca de) ni temas de Ayuda de proveedor.</span><span class="sxs-lookup"><span data-stu-id="47479-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="47479-157">Además, dado que esta característica es opcional, no funciona con todos los temas de Ayuda de cmdlets, funciones o scripts.</span><span class="sxs-lookup"><span data-stu-id="47479-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="47479-158">Sin embargo, todos los temas de Ayuda que se suministran con Windows PowerShell, incluidos los temas de Ayuda de proveedor y los temas de Ayuda conceptuales (Acerca de), están disponibles en línea en la sección [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) de la biblioteca de Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="47479-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="47479-159">Para usar el parámetro *Online* del cmdlet Get-Help, emplee el siguiente formato de comando.</span><span class="sxs-lookup"><span data-stu-id="47479-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="47479-160">Por ejemplo, para obtener la versión en línea del tema de Ayuda sobre el cmdlet Get-ChildItem, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="47479-161">Si está disponible una versión en línea del tema de Ayuda, se abrirá en el explorador predeterminado.</span><span class="sxs-lookup"><span data-stu-id="47479-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="47479-162">Si se admite la Ayuda en línea para un tema de Ayuda, también puede ver la dirección de Internet (URL) del tema de Ayuda.</span><span class="sxs-lookup"><span data-stu-id="47479-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="47479-163">La dirección de Internet aparece en la sección Vínculos relacionados de un tema de Ayuda.</span><span class="sxs-lookup"><span data-stu-id="47479-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="47479-164">Por ejemplo, para ver la dirección URL de la versión en línea del cmdlet Add-Computer, escriba:</span><span class="sxs-lookup"><span data-stu-id="47479-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="47479-165">A continuación, se muestra la primera línea de la sección Vínculos relacionados del tema.</span><span class="sxs-lookup"><span data-stu-id="47479-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="47479-166">Para obtener información sobre cómo proporcionar soporte técnico en línea para sus temas de ayuda, vea [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf) y [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Cómo escribir ayuda para cmdlet) en la biblioteca de MSDN.</span><span class="sxs-lookup"><span data-stu-id="47479-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="47479-167">Véase también</span><span class="sxs-lookup"><span data-stu-id="47479-167">See Also</span></span>
- [<span data-ttu-id="47479-168">about_Functions [m2]</span><span class="sxs-lookup"><span data-stu-id="47479-168">about_Functions [m2]</span></span>](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [<span data-ttu-id="47479-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="47479-169">about_Scripts</span></span>](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="47479-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="47479-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [<span data-ttu-id="47479-171">Get-Help [m2]</span><span class="sxs-lookup"><span data-stu-id="47479-171">Get-Help [m2]</span></span>](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)

