---
ms.date: 09/06/2019
keywords: powershell, cmdlet
title: Novedades de PowerShell 5.0 ISE
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746221"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="d22ac-103">Novedades de Windows PowerShell 5.0 ISE</span><span class="sxs-lookup"><span data-stu-id="d22ac-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="d22ac-104">En este tema se explican las características nuevas y actualizadas que se introdujeron en las versiones de Entorno de scripting integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d22ac-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="d22ac-105">Descripción de la característica</span><span class="sxs-lookup"><span data-stu-id="d22ac-105">Feature description</span></span>

<span data-ttu-id="d22ac-106">Windows PowerShell ISE es una aplicación host que permite escribir, ejecutar y probar scripts y módulos en un entorno gráfico e intuitivo.</span><span class="sxs-lookup"><span data-stu-id="d22ac-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="d22ac-107">Las características principales, como el coloreado de la sintaxis, el procedimiento para completar con el tabulador, la depuración visual, la compatibilidad con Unicode y la Ayuda contextual, proporcionan una rica experiencia de scripting.</span><span class="sxs-lookup"><span data-stu-id="d22ac-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="d22ac-108">Para obtener más información, consulte [Introducción a Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span><span class="sxs-lookup"><span data-stu-id="d22ac-108">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="d22ac-109">En la tabla siguiente se enumeran las características nuevas y modificadas de esta versión de Windows PowerShell ISE en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d22ac-109">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="d22ac-110">Intellisense</span><span class="sxs-lookup"><span data-stu-id="d22ac-110">IntelliSense</span></span>

> <span data-ttu-id="d22ac-111">Agregado en ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="d22ac-111">Added in ISE 3.0</span></span>

<span data-ttu-id="d22ac-112">IntelliSense es una característica de asistencia de finalización automática que forma parte de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d22ac-112">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="d22ac-113">Intellisense muestra menús en los que se pueden hacer clic de los cmdlets, parámetros, valores de parámetros, archivos o carpetas potencialmente coincidentes a medida que escribe.</span><span class="sxs-lookup"><span data-stu-id="d22ac-113">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="d22ac-114">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-114">**What value does this change add?**</span></span>

<span data-ttu-id="d22ac-115">Con la adición de IntelliSense, es más fácil detectar cmdlets y la sintaxis cuando se usa Windows PowerShell ISE para crear scripts.</span><span class="sxs-lookup"><span data-stu-id="d22ac-115">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="d22ac-116">También puede usar Windows PowerShell ISE para obtener información sobre Windows PowerShell al crear nuevos scripts.</span><span class="sxs-lookup"><span data-stu-id="d22ac-116">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="d22ac-117">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-117">**What works differently?**</span></span>

<span data-ttu-id="d22ac-118">Si escribe cmdlets en Windows PowerShell ISE, se muestra un menú desplazable en el que puede realizar sus selecciones, que permite examinar y seleccionar los comandos adecuados.</span><span class="sxs-lookup"><span data-stu-id="d22ac-118">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="d22ac-119">Fragmentos de código</span><span class="sxs-lookup"><span data-stu-id="d22ac-119">Snippets</span></span>

> <span data-ttu-id="d22ac-120">Agregado en ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="d22ac-120">Added in ISE 3.0</span></span>

<span data-ttu-id="d22ac-121">Los *fragmentos de código* son secciones de código de Windows PowerShell breves que puede insertar fácilmente en los scripts que crea en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d22ac-121">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="d22ac-122">Windows PowerShell ISE incluye un conjunto predeterminado de fragmentos de código.</span><span class="sxs-lookup"><span data-stu-id="d22ac-122">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="d22ac-123">Los fragmentos de código se pueden agregar mediante el cmdlet `New-Snippet` mientras se trabaja en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d22ac-123">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="d22ac-124">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-124">**What value does this change add?**</span></span>

<span data-ttu-id="d22ac-125">El uso de fragmentos de código permite ensamblar y crear rápidamente scripts para automatizar el entorno.</span><span class="sxs-lookup"><span data-stu-id="d22ac-125">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="d22ac-126">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-126">**What works differently?**</span></span>

<span data-ttu-id="d22ac-127">Para usar fragmentos de código en Windows PowerShell 3.0, o cualquier versión posterior, en el menú **Edición**, haga clic en **Iniciar fragmentos de código** o presione <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d22ac-127">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="d22ac-128">Herramientas de complemento</span><span class="sxs-lookup"><span data-stu-id="d22ac-128">Add-on tools</span></span>

> <span data-ttu-id="d22ac-129">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d22ac-129">Added in PowerShell 3.0</span></span>

<span data-ttu-id="d22ac-130">Windows PowerShell ISE ahora admite herramientas de complemento mediante el modelo de objetos.</span><span class="sxs-lookup"><span data-stu-id="d22ac-130">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="d22ac-131">Estos complementos son controles de Windows Presentation Foundation (WPF) que se muestran como un panel vertical u horizontal en la consola.</span><span class="sxs-lookup"><span data-stu-id="d22ac-131">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="d22ac-132">Si hay varias herramientas de complemento en un panel, se mostrarán como un control de pestaña.</span><span class="sxs-lookup"><span data-stu-id="d22ac-132">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="d22ac-133">También puede agregar o quitar herramientas de complemento no producidas por Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d22ac-133">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="d22ac-134">Para obtener más información, consulte [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span><span class="sxs-lookup"><span data-stu-id="d22ac-134">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="d22ac-135">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-135">**What value does this change add?**</span></span>

<span data-ttu-id="d22ac-136">Los complementos permiten ampliar y personalizar Windows PowerShell ISE con herramientas que agregan funcionalidad y mejoran su experiencia de scripting.</span><span class="sxs-lookup"><span data-stu-id="d22ac-136">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="d22ac-137">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-137">**What works differently?**</span></span>

<span data-ttu-id="d22ac-138">Windows PowerShell ISE 3.0 y versiones posteriores incluyen el complemento **Commands**.</span><span class="sxs-lookup"><span data-stu-id="d22ac-138">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="d22ac-139">El complemento **Commands** permite examinar cmdlets y acceder a la ayuda sobre los cmdlets en paralelo con los paneles de **scripts** y de **consola**.</span><span class="sxs-lookup"><span data-stu-id="d22ac-139">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="d22ac-140">Puede encontrar complementos adicionales mediante el comando **Abrir sitio web de herramientas de complemento** del menú **Complementos**.</span><span class="sxs-lookup"><span data-stu-id="d22ac-140">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="d22ac-141">Administrador de reinicio y Autoguardar</span><span class="sxs-lookup"><span data-stu-id="d22ac-141">Restart manager and auto-save</span></span>

> <span data-ttu-id="d22ac-142">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d22ac-142">Added in PowerShell 3.0</span></span>

<span data-ttu-id="d22ac-143">Windows PowerShell ISE ahora guarda automáticamente los scripts abiertos cada dos minutos en una ubicación aparte.</span><span class="sxs-lookup"><span data-stu-id="d22ac-143">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="d22ac-144">Al reiniciarse Windows PowerShell ISE tras un bloqueo o reinicio inesperado, recupera scripts que se abrieron en la última sesión, incluso si estos no se guardaron.</span><span class="sxs-lookup"><span data-stu-id="d22ac-144">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="d22ac-145">Para cambiar el intervalo de guardado automático, ejecute el siguiente comando en el panel de consola: `$psise.Options.AutoSaveMinuteInterval`.</span><span class="sxs-lookup"><span data-stu-id="d22ac-145">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="d22ac-146">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-146">**What value does this change add?**</span></span>

<span data-ttu-id="d22ac-147">Ahora puede trabajar en Windows PowerShell ISE con la tranquilidad de saber que los scripts abiertos se guardan automáticamente.</span><span class="sxs-lookup"><span data-stu-id="d22ac-147">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="d22ac-148">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-148">**What works differently?**</span></span>

<span data-ttu-id="d22ac-149">Windows PowerShell ISE 2.0 no guarda los scripts automáticamente.</span><span class="sxs-lookup"><span data-stu-id="d22ac-149">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="d22ac-150">Lista Usados más recientemente</span><span class="sxs-lookup"><span data-stu-id="d22ac-150">Most-recently used list</span></span>

> <span data-ttu-id="d22ac-151">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d22ac-151">Added in PowerShell 3.0</span></span>

<span data-ttu-id="d22ac-152">Windows PowerShell ISE tiene ahora una lista Usados más recientemente para los archivos.</span><span class="sxs-lookup"><span data-stu-id="d22ac-152">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="d22ac-153">Cuando se abre un archivo en Windows PowerShell ISE, este se agrega a la lista Usados más recientemente en el menú **Archivo**.</span><span class="sxs-lookup"><span data-stu-id="d22ac-153">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="d22ac-154">Para cambiar el número predeterminado de archivos en la lista Usados más recientemente, ejecute el siguiente comando en el panel de consola: `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="d22ac-154">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="d22ac-155">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-155">**What value does this change add?**</span></span>

<span data-ttu-id="d22ac-156">Ahora puede usar la lista Usados más recientemente para acceder fácilmente a los archivos que usa con frecuencia.</span><span class="sxs-lookup"><span data-stu-id="d22ac-156">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="d22ac-157">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-157">**What works differently?**</span></span>

<span data-ttu-id="d22ac-158">Windows PowerShell ISE 2.0 no tiene una lista Usados más recientemente.</span><span class="sxs-lookup"><span data-stu-id="d22ac-158">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="d22ac-159">Panel de consola</span><span class="sxs-lookup"><span data-stu-id="d22ac-159">Console Pane</span></span>

> <span data-ttu-id="d22ac-160">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d22ac-160">Added in PowerShell 3.0</span></span>

<span data-ttu-id="d22ac-161">Los paneles de comandos y de salida separados que estaban disponibles en la primera versión de Windows PowerShell ISE se combinaron en un solo panel de consola.</span><span class="sxs-lookup"><span data-stu-id="d22ac-161">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="d22ac-162">El panel de consola es similar en funciones y apariencia a una consola típica de Windows PowerShell, pero incluye las siguientes mejoras:</span><span class="sxs-lookup"><span data-stu-id="d22ac-162">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="d22ac-163">El color de la sintaxis del texto de entrada (no texto de salida), incluida la sintaxis XML</span><span class="sxs-lookup"><span data-stu-id="d22ac-163">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="d22ac-164">Intellisense</span><span class="sxs-lookup"><span data-stu-id="d22ac-164">IntelliSense</span></span>
- <span data-ttu-id="d22ac-165">Coincidencia de llaves</span><span class="sxs-lookup"><span data-stu-id="d22ac-165">Brace matching</span></span>
- <span data-ttu-id="d22ac-166">Indicación de errores</span><span class="sxs-lookup"><span data-stu-id="d22ac-166">Error indication</span></span>
- <span data-ttu-id="d22ac-167">Compatibilidad total con Unicode</span><span class="sxs-lookup"><span data-stu-id="d22ac-167">Full Unicode support</span></span>
- <span data-ttu-id="d22ac-168"><kbd>F1</kbd>: ayuda contextual</span><span class="sxs-lookup"><span data-stu-id="d22ac-168"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="d22ac-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd>: cmdlet Show-Command contextual</span><span class="sxs-lookup"><span data-stu-id="d22ac-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="d22ac-170">Compatibilidad con scripts complejos y de derecha a izquierda</span><span class="sxs-lookup"><span data-stu-id="d22ac-170">Complex script and right-to-left support</span></span>
- <span data-ttu-id="d22ac-171">Compatibilidad con fuentes</span><span class="sxs-lookup"><span data-stu-id="d22ac-171">Font support</span></span>
- <span data-ttu-id="d22ac-172">Zoom</span><span class="sxs-lookup"><span data-stu-id="d22ac-172">Zoom</span></span>
- <span data-ttu-id="d22ac-173">Modos de selección de líneas y bloques</span><span class="sxs-lookup"><span data-stu-id="d22ac-173">Line-select and block-select modes</span></span>
- <span data-ttu-id="d22ac-174">Conservación del contenido escrito en la línea de comandos cuando presiona la <kbd>Flecha arriba</kbd> para ver el historial en la consola</span><span class="sxs-lookup"><span data-stu-id="d22ac-174">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="d22ac-175">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-175">**What value does this change add?**</span></span>

<span data-ttu-id="d22ac-176">La adición de estos cambios del panel de consola proporciona una experiencia de scripting más coherente con la interfaz de la consola.</span><span class="sxs-lookup"><span data-stu-id="d22ac-176">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="d22ac-177">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-177">**What works differently?**</span></span>

<span data-ttu-id="d22ac-178">Windows PowerShell ISE 2.0 presenta paneles de comandos y de salida independientes.</span><span class="sxs-lookup"><span data-stu-id="d22ac-178">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="d22ac-179">Modificadores de línea de comandos</span><span class="sxs-lookup"><span data-stu-id="d22ac-179">Command-line switches</span></span>

> <span data-ttu-id="d22ac-180">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d22ac-180">Added in PowerShell 3.0</span></span>

<span data-ttu-id="d22ac-181">Si inicia Windows PowerShell ISE desde la línea de comandos (escribiendo **Powershell_ise.exe**), puede agregar los siguientes modificadores de línea de comandos nuevos.</span><span class="sxs-lookup"><span data-stu-id="d22ac-181">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="d22ac-182">`-NoProfile`: inicia Windows PowerShell ISE sin ejecutar `$profile`</span><span class="sxs-lookup"><span data-stu-id="d22ac-182">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="d22ac-183">`-Help`: muestra una ventana de Ayuda</span><span class="sxs-lookup"><span data-stu-id="d22ac-183">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="d22ac-184">`-mta`: inicia Windows PowerShell ISE en modo de contenedor multiproceso.</span><span class="sxs-lookup"><span data-stu-id="d22ac-184">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="d22ac-185">El modo de operación predeterminado de Windows PowerShell ISE es el modo de contenedor uniproceso o `-sta`.</span><span class="sxs-lookup"><span data-stu-id="d22ac-185">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="d22ac-186">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-186">**What value does this change add?**</span></span>

<span data-ttu-id="d22ac-187">La adición de estos modificadores de línea de comandos permite controlar el entorno en el que se ejecuta Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d22ac-187">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="d22ac-188">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-188">**What works differently?**</span></span>

<span data-ttu-id="d22ac-189">Windows PowerShell ISE 2.0 no reconoce estos modificadores de línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="d22ac-189">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="d22ac-190">Nuevas características del editor</span><span class="sxs-lookup"><span data-stu-id="d22ac-190">New editor features</span></span>

> <span data-ttu-id="d22ac-191">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d22ac-191">Added in PowerShell 3.0</span></span>

<span data-ttu-id="d22ac-192">Otras características de edición de Windows PowerShell ISE son:</span><span class="sxs-lookup"><span data-stu-id="d22ac-192">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="d22ac-193">**Color de la sintaxis XML**: Windows PowerShell ISE ahora colorea la sintaxis XML de la misma manera que la sintaxis de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d22ac-193">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="d22ac-194">**Coincidencia de llaves**: Windows PowerShell ISE incluye la coincidencia de llaves y el resaltado, y se pueden usar de las siguientes maneras: (por ejemplo, con el comando **Ir a Igualar** o <kbd>Ctrl</kbd>+<kbd>]</kbd> se localiza la llave de cierre, si hay alguna llave de apertura seleccionada).</span><span class="sxs-lookup"><span data-stu-id="d22ac-194">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="d22ac-195">**Vista Esquema**: el panel de scripts admite la esquematización, que permite expandir y contraer secciones de código al hacer clic en los signos más o menos en el margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="d22ac-195">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="d22ac-196">Puede usar llaves o las etiquetas `#region` y `#endregion` para marcar el inicio o el final de una sección contraíble.</span><span class="sxs-lookup"><span data-stu-id="d22ac-196">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="d22ac-197">Para expandir o contraer todas las regiones, presione <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d22ac-197">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="d22ac-198">**Edición de texto con arrastrar y colocar**: Windows PowerShell ISE permite ahora la edición de texto con arrastrar y colocar.</span><span class="sxs-lookup"><span data-stu-id="d22ac-198">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="d22ac-199">Puede seleccionar cualquier bloque de texto y arrastrar el texto a otra ubicación en el editor o la consola para mover el texto.</span><span class="sxs-lookup"><span data-stu-id="d22ac-199">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="d22ac-200">Si mantiene presionada la tecla <kbd>Ctrl</kbd> mientras arrastra el texto seleccionado, al soltar el botón del mouse, el texto se copiará en la nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="d22ac-200">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="d22ac-201">En esta versión de Windows PowerShell ISE, al arrastrar y colocar archivos en Windows PowerShell ISE, el archivo se abre.</span><span class="sxs-lookup"><span data-stu-id="d22ac-201">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="d22ac-202">**Presentación de errores de análisis**: los errores de análisis se indican con un subrayado rojo.</span><span class="sxs-lookup"><span data-stu-id="d22ac-202">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="d22ac-203">Cuando desplaza el cursor sobre un error indicado, el texto de información sobre herramientas muestra el problema que se encontró en el código.</span><span class="sxs-lookup"><span data-stu-id="d22ac-203">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="d22ac-204">**Zoom**: el porcentaje de zoom del contenido de la consola puede establecerse mediante el control deslizante del zoom (en la esquina inferior derecha de la ventana de Windows PowerShell ISE) o escribiendo el comando `$psise.options.Zoom` en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="d22ac-204">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="d22ac-205">**Copiar y pegar texto enriquecido**: la copia en el Portapapeles de Windows PowerShell ISE conserva la información de fuente, tamaño y color de la selección original.</span><span class="sxs-lookup"><span data-stu-id="d22ac-205">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="d22ac-206">**Selección de bloques**: para seleccionar un bloque de texto puede mantener presionada la tecla <kbd>ALT</kbd> y seleccionar texto en el panel de scripts con el mouse, o bien presionar <kbd>Alt</kbd>+<kbd>Mayús</kbd>+<kbd>Flecha</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d22ac-206">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="d22ac-207">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-207">**What value does this change add?**</span></span>

<span data-ttu-id="d22ac-208">Las características de edición adicionales proporcionan un entorno de edición más coherente y eficaz.</span><span class="sxs-lookup"><span data-stu-id="d22ac-208">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="d22ac-209">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-209">**What works differently?**</span></span>

<span data-ttu-id="d22ac-210">Estas mejoras de edición no estaban presentes en Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="d22ac-210">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="d22ac-211">Ventana del nuevo visor de Ayuda</span><span class="sxs-lookup"><span data-stu-id="d22ac-211">New Help viewer window</span></span>

> <span data-ttu-id="d22ac-212">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d22ac-212">Added in PowerShell 3.0</span></span>

<span data-ttu-id="d22ac-213">Si presiona <kbd>F1</kbd> cuando el cursor está en un cmdlet, o si tiene parte de un cmdlet resaltado, el nuevo visor de Ayuda abre la ayuda contextual sobre el cmdlet resaltado.</span><span class="sxs-lookup"><span data-stu-id="d22ac-213">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="d22ac-214">Para ver la Ayuda **acerca de** Windows PowerShell, escriba `operators` en el panel de consola y, después, presione <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d22ac-214">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="d22ac-215">Antes de usar esta característica, descargue la versión más actual de los temas de Ayuda de Windows PowerShell desde el sitio web de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d22ac-215">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="d22ac-216">El método más sencillo para la descarga de los temas de la Ayuda es ejecutar el cmdlet `Update-Help` en el panel de consola al ejecutar Windows PowerShell ISE como administrador.</span><span class="sxs-lookup"><span data-stu-id="d22ac-216">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="d22ac-217">Puede modificar donde busca ayuda la tecla <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d22ac-217">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="d22ac-218">En el menú **Herramientas**/**Opciones**, en la pestaña **Configuración general**, debajo de **Otra configuración**, puede activar o desactivar la casilla **Usar Ayuda local en lugar de contenido en línea**.</span><span class="sxs-lookup"><span data-stu-id="d22ac-218">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="d22ac-219">Al activarla, el cliente busca la Ayuda del cmdlet en la Ayuda descargada en la carpeta de módulos.</span><span class="sxs-lookup"><span data-stu-id="d22ac-219">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="d22ac-220">Si la casilla está desactivada, el cliente busca ayuda en línea.</span><span class="sxs-lookup"><span data-stu-id="d22ac-220">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="d22ac-221">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-221">**What value does this change add?**</span></span>

<span data-ttu-id="d22ac-222">La ayuda contextual sin salir del cmdlet o script actual proporciona una experiencia de aprendizaje integrada.</span><span class="sxs-lookup"><span data-stu-id="d22ac-222">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="d22ac-223">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-223">**What works differently?**</span></span>

<span data-ttu-id="d22ac-224">Al presionar <kbd>F1</kbd> en versiones anteriores de Windows PowerShell ISE, se abría el archivo de Ayuda en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="d22ac-224">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="d22ac-225">En Windows PowerShell ISE 3.0 y versiones posteriores, se abre una ventana que contiene la Ayuda del cmdlet, que es configurable y permite realizar búsquedas.</span><span class="sxs-lookup"><span data-stu-id="d22ac-225">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="d22ac-226">Esta experiencia de la Ayuda es una novedad de Windows PowerShell ISE 3.0 y la ayuda actualizable es una novedad de Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d22ac-226">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="d22ac-227">Cmdlet Show-Command</span><span class="sxs-lookup"><span data-stu-id="d22ac-227">Show-Command cmdlet</span></span>

> <span data-ttu-id="d22ac-228">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="d22ac-228">Added in PowerShell 3.0</span></span>

<span data-ttu-id="d22ac-229">El cmdlet `Show-Command` permite componer o ejecutar un cmdlet o una función rellenando un formulario gráfico.</span><span class="sxs-lookup"><span data-stu-id="d22ac-229">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="d22ac-230">El formato permite a los usuarios trabajar con Windows PowerShell en un entorno gráfico.</span><span class="sxs-lookup"><span data-stu-id="d22ac-230">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="d22ac-231">`Show-Command` también permite a los generadores de scripts avanzados crear una GUI rápida basada en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d22ac-231">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="d22ac-232">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-232">**What value does this change add?**</span></span>

<span data-ttu-id="d22ac-233">Si usa `Show-Command` en sus scripts de Windows PowerShell, puede proporcionar a los usuarios el entorno gráfico con el que están familiarizados.</span><span class="sxs-lookup"><span data-stu-id="d22ac-233">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="d22ac-234">`Show-Command` también puede ayudar a los nuevos usuarios a aprender Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d22ac-234">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="d22ac-235">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="d22ac-235">**What works differently?**</span></span>

<span data-ttu-id="d22ac-236">`Show-Command` es el nuevo Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="d22ac-236">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="d22ac-237">Vea también</span><span class="sxs-lookup"><span data-stu-id="d22ac-237">See also</span></span>

<span data-ttu-id="d22ac-238">Para obtener más información sobre cómo usar Windows PowerShell ISE, consulte [Exploración del Entorno de scripting integrado de Windows PowerShell](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span><span class="sxs-lookup"><span data-stu-id="d22ac-238">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span></span>
