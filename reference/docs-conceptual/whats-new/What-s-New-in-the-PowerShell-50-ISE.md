---
ms.date: 09/06/2019
keywords: powershell, cmdlet
title: Novedades de PowerShell 5.0 ISE
ms.openlocfilehash: 8f15e99c5a6ae33aeae9bd33eb0cf58fb27e3b90
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416632"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="363df-103">Novedades de Windows PowerShell 5.0 ISE</span><span class="sxs-lookup"><span data-stu-id="363df-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="363df-104">En este tema se explican las características nuevas y actualizadas que se introdujeron en la versión 5.0 del Entorno de scripting integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="363df-104">This topic explains the new and updated features that have been introduced in version 5.0 of the Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

> [!NOTE]
> <span data-ttu-id="363df-105">PowerShell ISE ya no se incluye en el desarrollo activo de características.</span><span class="sxs-lookup"><span data-stu-id="363df-105">The PowerShell ISE is no longer in active feature development.</span></span> <span data-ttu-id="363df-106">Como componente que se envía con Windows, sigue siendo compatible oficialmente con las correcciones de servicios de seguridad y alta prioridad.</span><span class="sxs-lookup"><span data-stu-id="363df-106">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="363df-107">Aunque actualmente no está previsto quitar el ISE de Windows,</span><span class="sxs-lookup"><span data-stu-id="363df-107">We currently have no plans to remove the ISE from Windows.</span></span>
>
> <span data-ttu-id="363df-108">no existe ninguna compatibilidad con él a partir de PowerShell v6.</span><span class="sxs-lookup"><span data-stu-id="363df-108">There is no support for the ISE in PowerShell v6 and beyond.</span></span> <span data-ttu-id="363df-109">Los usuarios que quieran reemplazar el ISE deben usar [Visual Studio Code](https://code.visualstudio.com/) con la [extensión de PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).</span><span class="sxs-lookup"><span data-stu-id="363df-109">Users looking for replacement for the ISE should use [Visual Studio Code](https://code.visualstudio.com/) with the [PowerShell Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).</span></span>

## <a name="feature-description"></a><span data-ttu-id="363df-110">Descripción de la característica</span><span class="sxs-lookup"><span data-stu-id="363df-110">Feature description</span></span>

<span data-ttu-id="363df-111">Windows PowerShell ISE es una aplicación host que permite escribir, ejecutar y probar scripts y módulos en un entorno gráfico e intuitivo.</span><span class="sxs-lookup"><span data-stu-id="363df-111">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="363df-112">Las características principales, como el coloreado de la sintaxis, el procedimiento para completar con el tabulador, la depuración visual, la compatibilidad con Unicode y la Ayuda contextual, proporcionan una rica experiencia de scripting.</span><span class="sxs-lookup"><span data-stu-id="363df-112">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="363df-113">Para obtener más información, consulte [Introducción a Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span><span class="sxs-lookup"><span data-stu-id="363df-113">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="363df-114">En la tabla siguiente se enumeran las características nuevas y modificadas de esta versión de Windows PowerShell ISE en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="363df-114">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="363df-115">Intellisense</span><span class="sxs-lookup"><span data-stu-id="363df-115">IntelliSense</span></span>

> <span data-ttu-id="363df-116">Agregado en ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="363df-116">Added in ISE 3.0</span></span>

<span data-ttu-id="363df-117">IntelliSense es una característica de asistencia de finalización automática que forma parte de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="363df-117">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="363df-118">Intellisense muestra menús en los que se pueden hacer clic de los cmdlets, parámetros, valores de parámetros, archivos o carpetas potencialmente coincidentes a medida que escribe.</span><span class="sxs-lookup"><span data-stu-id="363df-118">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="363df-119">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="363df-119">**What value does this change add?**</span></span>

<span data-ttu-id="363df-120">Con la adición de IntelliSense, es más fácil detectar cmdlets y la sintaxis cuando se usa Windows PowerShell ISE para crear scripts.</span><span class="sxs-lookup"><span data-stu-id="363df-120">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="363df-121">También puede usar Windows PowerShell ISE para obtener información sobre Windows PowerShell al crear nuevos scripts.</span><span class="sxs-lookup"><span data-stu-id="363df-121">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="363df-122">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="363df-122">**What works differently?**</span></span>

<span data-ttu-id="363df-123">Si escribe cmdlets en Windows PowerShell ISE, se muestra un menú desplazable en el que puede realizar sus selecciones, que permite examinar y seleccionar los comandos adecuados.</span><span class="sxs-lookup"><span data-stu-id="363df-123">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="363df-124">Fragmentos de código</span><span class="sxs-lookup"><span data-stu-id="363df-124">Snippets</span></span>

> <span data-ttu-id="363df-125">Agregado en ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="363df-125">Added in ISE 3.0</span></span>

<span data-ttu-id="363df-126">Los *fragmentos de código* son secciones de código de Windows PowerShell breves que puede insertar fácilmente en los scripts que crea en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="363df-126">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="363df-127">Windows PowerShell ISE incluye un conjunto predeterminado de fragmentos de código.</span><span class="sxs-lookup"><span data-stu-id="363df-127">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="363df-128">Los fragmentos de código se pueden agregar mediante el cmdlet `New-Snippet` mientras se trabaja en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="363df-128">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="363df-129">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="363df-129">**What value does this change add?**</span></span>

<span data-ttu-id="363df-130">El uso de fragmentos de código permite ensamblar y crear rápidamente scripts para automatizar el entorno.</span><span class="sxs-lookup"><span data-stu-id="363df-130">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="363df-131">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="363df-131">**What works differently?**</span></span>

<span data-ttu-id="363df-132">Para usar fragmentos de código en Windows PowerShell 3.0, o cualquier versión posterior, en el menú **Edición**, haga clic en **Iniciar fragmentos de código** o presione <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="363df-132">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="363df-133">Herramientas de complemento</span><span class="sxs-lookup"><span data-stu-id="363df-133">Add-on tools</span></span>

> <span data-ttu-id="363df-134">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="363df-134">Added in PowerShell 3.0</span></span>

<span data-ttu-id="363df-135">Windows PowerShell ISE ahora admite herramientas de complemento mediante el modelo de objetos.</span><span class="sxs-lookup"><span data-stu-id="363df-135">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="363df-136">Estos complementos son controles de Windows Presentation Foundation (WPF) que se muestran como un panel vertical u horizontal en la consola.</span><span class="sxs-lookup"><span data-stu-id="363df-136">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="363df-137">Si hay varias herramientas de complemento en un panel, se mostrarán como un control de pestaña.</span><span class="sxs-lookup"><span data-stu-id="363df-137">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="363df-138">También puede agregar o quitar herramientas de complemento no producidas por Microsoft.</span><span class="sxs-lookup"><span data-stu-id="363df-138">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="363df-139">Para obtener más información, consulte [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span><span class="sxs-lookup"><span data-stu-id="363df-139">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="363df-140">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="363df-140">**What value does this change add?**</span></span>

<span data-ttu-id="363df-141">Los complementos permiten ampliar y personalizar Windows PowerShell ISE con herramientas que agregan funcionalidad y mejoran su experiencia de scripting.</span><span class="sxs-lookup"><span data-stu-id="363df-141">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="363df-142">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="363df-142">**What works differently?**</span></span>

<span data-ttu-id="363df-143">Windows PowerShell ISE 3.0 y versiones posteriores incluyen el complemento **Commands**.</span><span class="sxs-lookup"><span data-stu-id="363df-143">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="363df-144">El complemento **Commands** permite examinar cmdlets y acceder a la ayuda sobre los cmdlets en paralelo con los paneles de **scripts** y de **consola**.</span><span class="sxs-lookup"><span data-stu-id="363df-144">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="363df-145">Puede encontrar complementos adicionales mediante el comando **Abrir sitio web de herramientas de complemento** del menú **Complementos**.</span><span class="sxs-lookup"><span data-stu-id="363df-145">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="363df-146">Administrador de reinicio y Autoguardar</span><span class="sxs-lookup"><span data-stu-id="363df-146">Restart manager and auto-save</span></span>

> <span data-ttu-id="363df-147">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="363df-147">Added in PowerShell 3.0</span></span>

<span data-ttu-id="363df-148">Windows PowerShell ISE ahora guarda automáticamente los scripts abiertos cada dos minutos en una ubicación aparte.</span><span class="sxs-lookup"><span data-stu-id="363df-148">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="363df-149">Al reiniciarse Windows PowerShell ISE tras un bloqueo o reinicio inesperado, recupera scripts que se abrieron en la última sesión, incluso si estos no se guardaron.</span><span class="sxs-lookup"><span data-stu-id="363df-149">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="363df-150">Para cambiar el intervalo de guardado automático, ejecute el siguiente comando en el panel de consola: `$psise.Options.AutoSaveMinuteInterval`.</span><span class="sxs-lookup"><span data-stu-id="363df-150">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="363df-151">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="363df-151">**What value does this change add?**</span></span>

<span data-ttu-id="363df-152">Ahora puede trabajar en Windows PowerShell ISE con la tranquilidad de saber que los scripts abiertos se guardan automáticamente.</span><span class="sxs-lookup"><span data-stu-id="363df-152">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="363df-153">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="363df-153">**What works differently?**</span></span>

<span data-ttu-id="363df-154">Windows PowerShell ISE 2.0 no guarda los scripts automáticamente.</span><span class="sxs-lookup"><span data-stu-id="363df-154">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="363df-155">Lista Usados más recientemente</span><span class="sxs-lookup"><span data-stu-id="363df-155">Most-recently used list</span></span>

> <span data-ttu-id="363df-156">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="363df-156">Added in PowerShell 3.0</span></span>

<span data-ttu-id="363df-157">Windows PowerShell ISE tiene ahora una lista Usados más recientemente para los archivos.</span><span class="sxs-lookup"><span data-stu-id="363df-157">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="363df-158">Cuando se abre un archivo en Windows PowerShell ISE, este se agrega a la lista Usados más recientemente en el menú **Archivo**.</span><span class="sxs-lookup"><span data-stu-id="363df-158">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="363df-159">Para cambiar el número predeterminado de archivos en la lista Usados más recientemente, ejecute el siguiente comando en el panel de consola: `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="363df-159">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="363df-160">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="363df-160">**What value does this change add?**</span></span>

<span data-ttu-id="363df-161">Ahora puede usar la lista Usados más recientemente para acceder fácilmente a los archivos que usa con frecuencia.</span><span class="sxs-lookup"><span data-stu-id="363df-161">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="363df-162">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="363df-162">**What works differently?**</span></span>

<span data-ttu-id="363df-163">Windows PowerShell ISE 2.0 no tiene una lista Usados más recientemente.</span><span class="sxs-lookup"><span data-stu-id="363df-163">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="363df-164">Panel de consola</span><span class="sxs-lookup"><span data-stu-id="363df-164">Console Pane</span></span>

> <span data-ttu-id="363df-165">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="363df-165">Added in PowerShell 3.0</span></span>

<span data-ttu-id="363df-166">Los paneles de comandos y de salida separados que estaban disponibles en la primera versión de Windows PowerShell ISE se combinaron en un solo panel de consola.</span><span class="sxs-lookup"><span data-stu-id="363df-166">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="363df-167">El panel de consola es similar en funciones y apariencia a una consola típica de Windows PowerShell, pero incluye las siguientes mejoras:</span><span class="sxs-lookup"><span data-stu-id="363df-167">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="363df-168">El color de la sintaxis del texto de entrada (no texto de salida), incluida la sintaxis XML</span><span class="sxs-lookup"><span data-stu-id="363df-168">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="363df-169">Intellisense</span><span class="sxs-lookup"><span data-stu-id="363df-169">IntelliSense</span></span>
- <span data-ttu-id="363df-170">Coincidencia de llaves</span><span class="sxs-lookup"><span data-stu-id="363df-170">Brace matching</span></span>
- <span data-ttu-id="363df-171">Indicación de errores</span><span class="sxs-lookup"><span data-stu-id="363df-171">Error indication</span></span>
- <span data-ttu-id="363df-172">Compatibilidad total con Unicode</span><span class="sxs-lookup"><span data-stu-id="363df-172">Full Unicode support</span></span>
- <span data-ttu-id="363df-173"><kbd>F1</kbd>: ayuda contextual</span><span class="sxs-lookup"><span data-stu-id="363df-173"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="363df-174"><kbd>Ctrl</kbd>+<kbd>F1</kbd>: cmdlet Show-Command contextual</span><span class="sxs-lookup"><span data-stu-id="363df-174"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="363df-175">Compatibilidad con scripts complejos y de derecha a izquierda</span><span class="sxs-lookup"><span data-stu-id="363df-175">Complex script and right-to-left support</span></span>
- <span data-ttu-id="363df-176">Compatibilidad con fuentes</span><span class="sxs-lookup"><span data-stu-id="363df-176">Font support</span></span>
- <span data-ttu-id="363df-177">Zoom</span><span class="sxs-lookup"><span data-stu-id="363df-177">Zoom</span></span>
- <span data-ttu-id="363df-178">Modos de selección de líneas y bloques</span><span class="sxs-lookup"><span data-stu-id="363df-178">Line-select and block-select modes</span></span>
- <span data-ttu-id="363df-179">Conservación del contenido escrito en la línea de comandos cuando presiona la <kbd>Flecha arriba</kbd> para ver el historial en la consola</span><span class="sxs-lookup"><span data-stu-id="363df-179">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="363df-180">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="363df-180">**What value does this change add?**</span></span>

<span data-ttu-id="363df-181">La adición de estos cambios del panel de consola proporciona una experiencia de scripting más coherente con la interfaz de la consola.</span><span class="sxs-lookup"><span data-stu-id="363df-181">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="363df-182">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="363df-182">**What works differently?**</span></span>

<span data-ttu-id="363df-183">Windows PowerShell ISE 2.0 presenta paneles de comandos y de salida independientes.</span><span class="sxs-lookup"><span data-stu-id="363df-183">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="363df-184">Modificadores de línea de comandos</span><span class="sxs-lookup"><span data-stu-id="363df-184">Command-line switches</span></span>

> <span data-ttu-id="363df-185">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="363df-185">Added in PowerShell 3.0</span></span>

<span data-ttu-id="363df-186">Si inicia Windows PowerShell ISE desde la línea de comandos (escribiendo **Powershell_ise.exe**), puede agregar los siguientes modificadores de línea de comandos nuevos.</span><span class="sxs-lookup"><span data-stu-id="363df-186">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="363df-187">`-NoProfile`: inicia Windows PowerShell ISE sin ejecutar `$profile`</span><span class="sxs-lookup"><span data-stu-id="363df-187">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="363df-188">`-Help`: muestra una ventana de Ayuda</span><span class="sxs-lookup"><span data-stu-id="363df-188">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="363df-189">`-mta`: inicia Windows PowerShell ISE en modo de contenedor multiproceso.</span><span class="sxs-lookup"><span data-stu-id="363df-189">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="363df-190">El modo de operación predeterminado de Windows PowerShell ISE es el modo de contenedor uniproceso o `-sta`.</span><span class="sxs-lookup"><span data-stu-id="363df-190">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="363df-191">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="363df-191">**What value does this change add?**</span></span>

<span data-ttu-id="363df-192">La adición de estos modificadores de línea de comandos permite controlar el entorno en el que se ejecuta Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="363df-192">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="363df-193">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="363df-193">**What works differently?**</span></span>

<span data-ttu-id="363df-194">Windows PowerShell ISE 2.0 no reconoce estos modificadores de línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="363df-194">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="363df-195">Nuevas características del editor</span><span class="sxs-lookup"><span data-stu-id="363df-195">New editor features</span></span>

> <span data-ttu-id="363df-196">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="363df-196">Added in PowerShell 3.0</span></span>

<span data-ttu-id="363df-197">Otras características de edición de Windows PowerShell ISE son:</span><span class="sxs-lookup"><span data-stu-id="363df-197">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="363df-198">**Color de la sintaxis XML**: Windows PowerShell ISE ahora colorea la sintaxis XML de la misma manera que la sintaxis de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="363df-198">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="363df-199">**Coincidencia de llaves**: Windows PowerShell ISE incluye la coincidencia de llaves y el resaltado, y se pueden usar de las siguientes maneras: (por ejemplo, con el comando **Ir a Igualar** o <kbd>Ctrl</kbd>+<kbd>]</kbd> se localiza la llave de cierre, si hay alguna llave de apertura seleccionada).</span><span class="sxs-lookup"><span data-stu-id="363df-199">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="363df-200">**Vista Esquema**: el panel de scripts admite la esquematización, que permite expandir y contraer secciones de código al hacer clic en los signos más o menos en el margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="363df-200">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="363df-201">Puede usar llaves o las etiquetas `#region` y `#endregion` para marcar el inicio o el final de una sección contraíble.</span><span class="sxs-lookup"><span data-stu-id="363df-201">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="363df-202">Para expandir o contraer todas las regiones, presione <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span><span class="sxs-lookup"><span data-stu-id="363df-202">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="363df-203">**Edición de texto con arrastrar y colocar**: Windows PowerShell ISE permite ahora la edición de texto con arrastrar y colocar.</span><span class="sxs-lookup"><span data-stu-id="363df-203">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="363df-204">Puede seleccionar cualquier bloque de texto y arrastrar el texto a otra ubicación en el editor o la consola para mover el texto.</span><span class="sxs-lookup"><span data-stu-id="363df-204">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="363df-205">Si mantiene presionada la tecla <kbd>Ctrl</kbd> mientras arrastra el texto seleccionado, al soltar el botón del mouse, el texto se copiará en la nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="363df-205">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="363df-206">En esta versión de Windows PowerShell ISE, al arrastrar y colocar archivos en Windows PowerShell ISE, el archivo se abre.</span><span class="sxs-lookup"><span data-stu-id="363df-206">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="363df-207">**Presentación de errores de análisis**: los errores de análisis se indican con un subrayado rojo.</span><span class="sxs-lookup"><span data-stu-id="363df-207">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="363df-208">Cuando desplaza el cursor sobre un error indicado, el texto de información sobre herramientas muestra el problema que se encontró en el código.</span><span class="sxs-lookup"><span data-stu-id="363df-208">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="363df-209">**Zoom**: el porcentaje de zoom del contenido de la consola puede establecerse mediante el control deslizante del zoom (en la esquina inferior derecha de la ventana de Windows PowerShell ISE) o escribiendo el comando `$psise.options.Zoom` en el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="363df-209">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="363df-210">**Copiar y pegar texto enriquecido**: la copia en el Portapapeles de Windows PowerShell ISE conserva la información de fuente, tamaño y color de la selección original.</span><span class="sxs-lookup"><span data-stu-id="363df-210">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="363df-211">**Selección de bloques**: para seleccionar un bloque de texto puede mantener presionada la tecla <kbd>ALT</kbd> y seleccionar texto en el panel de scripts con el mouse, o bien presionar <kbd>Alt</kbd>+<kbd>Mayús</kbd>+<kbd>Flecha</kbd>.</span><span class="sxs-lookup"><span data-stu-id="363df-211">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="363df-212">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="363df-212">**What value does this change add?**</span></span>

<span data-ttu-id="363df-213">Las características de edición adicionales proporcionan un entorno de edición más coherente y eficaz.</span><span class="sxs-lookup"><span data-stu-id="363df-213">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="363df-214">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="363df-214">**What works differently?**</span></span>

<span data-ttu-id="363df-215">Estas mejoras de edición no estaban presentes en Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="363df-215">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="363df-216">Ventana del nuevo visor de Ayuda</span><span class="sxs-lookup"><span data-stu-id="363df-216">New Help viewer window</span></span>

> <span data-ttu-id="363df-217">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="363df-217">Added in PowerShell 3.0</span></span>

<span data-ttu-id="363df-218">Si presiona <kbd>F1</kbd> cuando el cursor está en un cmdlet, o si tiene parte de un cmdlet resaltado, el nuevo visor de Ayuda abre la ayuda contextual sobre el cmdlet resaltado.</span><span class="sxs-lookup"><span data-stu-id="363df-218">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="363df-219">Para ver la Ayuda **acerca de** Windows PowerShell, escriba `operators` en el panel de consola y, después, presione <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="363df-219">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="363df-220">Antes de usar esta característica, descargue la versión más actual de los temas de Ayuda de Windows PowerShell desde el sitio web de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="363df-220">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="363df-221">El método más sencillo para la descarga de los temas de la Ayuda es ejecutar el cmdlet `Update-Help` en el panel de consola al ejecutar Windows PowerShell ISE como administrador.</span><span class="sxs-lookup"><span data-stu-id="363df-221">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="363df-222">Puede modificar donde busca ayuda la tecla <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="363df-222">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="363df-223">En el menú **Herramientas**/**Opciones**, en la pestaña **Configuración general**, debajo de **Otra configuración**, puede activar o desactivar la casilla **Usar Ayuda local en lugar de contenido en línea**.</span><span class="sxs-lookup"><span data-stu-id="363df-223">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="363df-224">Al activarla, el cliente busca la Ayuda del cmdlet en la Ayuda descargada en la carpeta de módulos.</span><span class="sxs-lookup"><span data-stu-id="363df-224">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="363df-225">Si la casilla está desactivada, el cliente busca ayuda en línea.</span><span class="sxs-lookup"><span data-stu-id="363df-225">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="363df-226">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="363df-226">**What value does this change add?**</span></span>

<span data-ttu-id="363df-227">La ayuda contextual sin salir del cmdlet o script actual proporciona una experiencia de aprendizaje integrada.</span><span class="sxs-lookup"><span data-stu-id="363df-227">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="363df-228">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="363df-228">**What works differently?**</span></span>

<span data-ttu-id="363df-229">Al presionar <kbd>F1</kbd> en versiones anteriores de Windows PowerShell ISE, se abría el archivo de Ayuda en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="363df-229">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="363df-230">En Windows PowerShell ISE 3.0 y versiones posteriores, se abre una ventana que contiene la Ayuda del cmdlet, que es configurable y permite realizar búsquedas.</span><span class="sxs-lookup"><span data-stu-id="363df-230">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="363df-231">Esta experiencia de la Ayuda es una novedad de Windows PowerShell ISE 3.0 y la ayuda actualizable es una novedad de Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="363df-231">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="363df-232">Cmdlet Show-Command</span><span class="sxs-lookup"><span data-stu-id="363df-232">Show-Command cmdlet</span></span>

> <span data-ttu-id="363df-233">Agregado en PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="363df-233">Added in PowerShell 3.0</span></span>

<span data-ttu-id="363df-234">El cmdlet `Show-Command` permite componer o ejecutar un cmdlet o una función rellenando un formulario gráfico.</span><span class="sxs-lookup"><span data-stu-id="363df-234">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="363df-235">El formato permite a los usuarios trabajar con Windows PowerShell en un entorno gráfico.</span><span class="sxs-lookup"><span data-stu-id="363df-235">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="363df-236">`Show-Command` también permite a los generadores de scripts avanzados crear una GUI rápida basada en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="363df-236">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="363df-237">**¿Qué valor aporta este cambio?**</span><span class="sxs-lookup"><span data-stu-id="363df-237">**What value does this change add?**</span></span>

<span data-ttu-id="363df-238">Si usa `Show-Command` en sus scripts de Windows PowerShell, puede proporcionar a los usuarios el entorno gráfico con el que están familiarizados.</span><span class="sxs-lookup"><span data-stu-id="363df-238">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="363df-239">`Show-Command` también puede ayudar a los nuevos usuarios a aprender Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="363df-239">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="363df-240">**¿Qué funciona de manera diferente?**</span><span class="sxs-lookup"><span data-stu-id="363df-240">**What works differently?**</span></span>

<span data-ttu-id="363df-241">`Show-Command` es el nuevo Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="363df-241">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="363df-242">Vea también</span><span class="sxs-lookup"><span data-stu-id="363df-242">See also</span></span>

<span data-ttu-id="363df-243">Para obtener más información sobre cómo usar Windows PowerShell ISE, consulte [Exploración del Entorno de scripting integrado de Windows PowerShell](../components/ise/exploring-the-windows-powershell-ise.md).</span><span class="sxs-lookup"><span data-stu-id="363df-243">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../components/ise/exploring-the-windows-powershell-ise.md).</span></span>
