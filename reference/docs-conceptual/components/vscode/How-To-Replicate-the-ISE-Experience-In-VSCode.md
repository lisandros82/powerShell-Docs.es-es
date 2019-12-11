---
title: Cómo replicar la experiencia de ISE en Visual Studio Code
description: Cómo replicar la experiencia de ISE en Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117489"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="fde0d-103">Cómo replicar la experiencia de ISE en Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fde0d-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="fde0d-104">Si bien la extensión de PowerShell para VSCode no busca una paridad de características completa con el ISE de PowerShell, existen características para hacer que la experiencia de VSCode sea más natural para los usuarios de ISE.</span><span class="sxs-lookup"><span data-stu-id="fde0d-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="fde0d-105">El objetivo de este documento es confeccionar un listado con las opciones que puede configurar en VSCode para que la experiencia del usuario sea un poco más familiar en comparación con el ISE.</span><span class="sxs-lookup"><span data-stu-id="fde0d-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="fde0d-106">Enlaces de teclado</span><span class="sxs-lookup"><span data-stu-id="fde0d-106">Key bindings</span></span>

| <span data-ttu-id="fde0d-107">Función</span><span class="sxs-lookup"><span data-stu-id="fde0d-107">Function</span></span>                              | <span data-ttu-id="fde0d-108">Enlace de ISE</span><span class="sxs-lookup"><span data-stu-id="fde0d-108">ISE Binding</span></span>                  | <span data-ttu-id="fde0d-109">Enlace de VSCode</span><span class="sxs-lookup"><span data-stu-id="fde0d-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="fde0d-110">Depurador de interrupción</span><span class="sxs-lookup"><span data-stu-id="fde0d-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="fde0d-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="fde0d-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="fde0d-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="fde0d-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="fde0d-113">Ejecutar línea actual/texto resaltado</span><span class="sxs-lookup"><span data-stu-id="fde0d-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="fde0d-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="fde0d-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="fde0d-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="fde0d-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="fde0d-116">Lista de fragmentos de código disponibles</span><span class="sxs-lookup"><span data-stu-id="fde0d-116">List available snippets</span></span>               | <span data-ttu-id="fde0d-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="fde0d-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="fde0d-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="fde0d-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="fde0d-119">Enlaces de teclado personalizados</span><span class="sxs-lookup"><span data-stu-id="fde0d-119">Custom Key bindings</span></span>

<span data-ttu-id="fde0d-120">En VSCode también puede [configurar sus propios enlaces de teclado](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings).</span><span class="sxs-lookup"><span data-stu-id="fde0d-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="fde0d-121">Interfaz de usuario de tipo ISE simplificada</span><span class="sxs-lookup"><span data-stu-id="fde0d-121">Simplified ISE-like UI</span></span>

<span data-ttu-id="fde0d-122">Si quiere simplificar la interfaz de usuario de Visual Studio Code para que se asemeje más a la interfaz de usuario del ISE, aplique estas dos configuraciones:</span><span class="sxs-lookup"><span data-stu-id="fde0d-122">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

<span data-ttu-id="fde0d-123">Se ocultarán las secciones de la barra de actividades y la barra lateral de depuración que se encuentran debajo del cuadro rojo:</span><span class="sxs-lookup"><span data-stu-id="fde0d-123">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![La sección resaltada incluye la barra de actividades y la barra lateral de depuración](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="fde0d-125">El resultado final tiene el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="fde0d-125">The end result looks like this:</span></span>

![Vista simplificada de VS Code](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="fde0d-127">Finalización con tabulación</span><span class="sxs-lookup"><span data-stu-id="fde0d-127">Tab completion</span></span>

<span data-ttu-id="fde0d-128">Para habilitar una finalización con tabulación más similar a ISE, agregue este parámetro:</span><span class="sxs-lookup"><span data-stu-id="fde0d-128">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="fde0d-129">Esta configuración se ha agregado directamente a VSCode (y no a la extensión).</span><span class="sxs-lookup"><span data-stu-id="fde0d-129">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="fde0d-130">Su comportamiento viene determinado por VSCode directamente y no se puede cambiar por la extensión.</span><span class="sxs-lookup"><span data-stu-id="fde0d-130">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="fde0d-131">No centrarse en la consola al ejecutar</span><span class="sxs-lookup"><span data-stu-id="fde0d-131">No focus on console when executing</span></span>

<span data-ttu-id="fde0d-132">Para mantener el foco en el editor cuando se ejecuta con <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="fde0d-132">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="fde0d-133">El valor predeterminado es `true` por motivos de accesibilidad.</span><span class="sxs-lookup"><span data-stu-id="fde0d-133">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="fde0d-134">No iniciar la consola integrada en el inicio</span><span class="sxs-lookup"><span data-stu-id="fde0d-134">Don't start integrated console on startup</span></span>

<span data-ttu-id="fde0d-135">Para detener la consola integrada en el inicio, configure:</span><span class="sxs-lookup"><span data-stu-id="fde0d-135">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="fde0d-136">El proceso de PowerShell en segundo plano seguirá iniciándose, ya que proporciona IntelliSense, análisis de scripts, navegación de símbolos, etc. Pero la consola no se mostrará.</span><span class="sxs-lookup"><span data-stu-id="fde0d-136">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="fde0d-137">Suponer que los archivos son de PowerShell de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="fde0d-137">Assume files are PowerShell by default</span></span>

<span data-ttu-id="fde0d-138">Para tener archivos nuevos/sin título, regístrelos como de PowerShell de forma predeterminada:</span><span class="sxs-lookup"><span data-stu-id="fde0d-138">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a><span data-ttu-id="fde0d-139">Combinación de colores</span><span class="sxs-lookup"><span data-stu-id="fde0d-139">Color scheme</span></span>

<span data-ttu-id="fde0d-140">Hay una serie de temas de ISE disponibles para VSCode para que el editor se parezca mucho más a ISE.</span><span class="sxs-lookup"><span data-stu-id="fde0d-140">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="fde0d-141">En la [Paleta de comandos], escriba `theme` para obtener `Preferences: Color Theme` y presione <kbd>Entrar</kbd>.</span><span class="sxs-lookup"><span data-stu-id="fde0d-141">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="fde0d-142">En la lista desplegable, seleccione `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="fde0d-142">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="fde0d-143">Puede establecer en este tema en la configuración con:</span><span class="sxs-lookup"><span data-stu-id="fde0d-143">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="fde0d-144">Explorador de comandos de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fde0d-144">PowerShell Command Explorer</span></span>

<span data-ttu-id="fde0d-145">Gracias al trabajo de [@corbob](https://github.com/corbob), la extensión de PowerShell tiene un incipiente explorador de comandos propio.</span><span class="sxs-lookup"><span data-stu-id="fde0d-145">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="fde0d-146">En la [Paleta de comandos], escriba `PowerShell Command Explorer` y presione <kbd>Entrar</kbd>.</span><span class="sxs-lookup"><span data-stu-id="fde0d-146">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="fde0d-147">Abrir en el ISE</span><span class="sxs-lookup"><span data-stu-id="fde0d-147">Open in the ISE</span></span>

<span data-ttu-id="fde0d-148">Si finalmente desea abrir un archivo en el ISE de todos modos, puede usar <kbd>Mayús</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="fde0d-148">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="fde0d-149">Otros recursos</span><span class="sxs-lookup"><span data-stu-id="fde0d-149">Other resources</span></span>

- <span data-ttu-id="fde0d-150">4sysops tiene [un excelente artículo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sobre la configuración de VSCode para que sea más parecido al ISE.</span><span class="sxs-lookup"><span data-stu-id="fde0d-150">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="fde0d-151">Mike F Robbins tiene [una excelente publicación](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sobre la configuración de VSCode.</span><span class="sxs-lookup"><span data-stu-id="fde0d-151">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="fde0d-152">Learn PowerShell tiene un [excelente documento](https://www.learnpwsh.com/setup-vs-code-for-powershell/) sobre la configuración de VSCode para PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fde0d-152">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="fde0d-153">Más opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="fde0d-153">More settings</span></span>

<span data-ttu-id="fde0d-154">Si conoce más formas de hacer que VSCode resulte más familiar para los usuarios de ISE, haga su aportación a este documento. Si busca una configuración de compatibilidad pero no encuentra la manera de habilitarla, [abra una incidencia](https://github.com/PowerShell/vscode-powershell/issues/new/choose) y pregunte.</span><span class="sxs-lookup"><span data-stu-id="fde0d-154">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="fde0d-155">Siempre estamos encantados de aceptar solicitudes de incorporación de cambios y aportaciones.</span><span class="sxs-lookup"><span data-stu-id="fde0d-155">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="fde0d-156">Sugerencias de VSCode</span><span class="sxs-lookup"><span data-stu-id="fde0d-156">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="fde0d-157">Paleta de comandos</span><span class="sxs-lookup"><span data-stu-id="fde0d-157">Command Palette</span></span>

<span data-ttu-id="fde0d-158"><kbd>F1</kbd> O <kbd>Ctrl</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd> en macOS)</span><span class="sxs-lookup"><span data-stu-id="fde0d-158"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="fde0d-159">Una forma práctica de ejecutar comandos en VSCode.</span><span class="sxs-lookup"><span data-stu-id="fde0d-159">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="fde0d-160">Para obtener más información, vea [la documentación de VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="fde0d-160">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Paleta de comandos]: #command-palette
[Command Palette]: #command-palette
