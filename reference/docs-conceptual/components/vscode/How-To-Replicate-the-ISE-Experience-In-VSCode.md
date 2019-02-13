---
title: Cómo replicar la experiencia de ISE en Visual Studio Code
description: Cómo replicar la experiencia de ISE en Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681946"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="b821a-103">Cómo replicar la experiencia de ISE en Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b821a-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="b821a-104">Mientras que la extensión de PowerShell para VSCode no busca paridad completa con el ISE de PowerShell, hay características que hacen que la experiencia de VSCode más natural para los usuarios del ISE.</span><span class="sxs-lookup"><span data-stu-id="b821a-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="b821a-105">Este documento trata de lista, puede configurar en VSCode para que el usuario experimente un poco más conocidos en comparación con el ISE.</span><span class="sxs-lookup"><span data-stu-id="b821a-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="b821a-106">Enlaces de teclado</span><span class="sxs-lookup"><span data-stu-id="b821a-106">Key bindings</span></span>

| <span data-ttu-id="b821a-107">Función</span><span class="sxs-lookup"><span data-stu-id="b821a-107">Function</span></span>                              | <span data-ttu-id="b821a-108">Enlace de ISE</span><span class="sxs-lookup"><span data-stu-id="b821a-108">ISE Binding</span></span>                  | <span data-ttu-id="b821a-109">Enlace de VSCode</span><span class="sxs-lookup"><span data-stu-id="b821a-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="b821a-110">Interrupción y salto de depurador</span><span class="sxs-lookup"><span data-stu-id="b821a-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="b821a-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="b821a-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="b821a-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="b821a-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="b821a-113">Ejecutar texto/resaltado de línea actual</span><span class="sxs-lookup"><span data-stu-id="b821a-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="b821a-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="b821a-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="b821a-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="b821a-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="b821a-116">Lista de fragmentos de código disponibles</span><span class="sxs-lookup"><span data-stu-id="b821a-116">List available snippets</span></span>               | <span data-ttu-id="b821a-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="b821a-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="b821a-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="b821a-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="b821a-119">Enlaces de teclado personalizados</span><span class="sxs-lookup"><span data-stu-id="b821a-119">Custom Key bindings</span></span>

<span data-ttu-id="b821a-120">También puede [configurar sus propios enlaces claves](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) en VSCode también.</span><span class="sxs-lookup"><span data-stu-id="b821a-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="b821a-121">Finalización con tabulación</span><span class="sxs-lookup"><span data-stu-id="b821a-121">Tab completion</span></span>

<span data-ttu-id="b821a-122">Para habilitar más ISE similar a la finalización con tabulación, agregue esta configuración:</span><span class="sxs-lookup"><span data-stu-id="b821a-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="b821a-123">Esta configuración se ha agregado directamente en VSCode (en lugar de en la extensión).</span><span class="sxs-lookup"><span data-stu-id="b821a-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="b821a-124">Su comportamiento viene determinado por VSCode directamente y no se puede cambiar la extensión.</span><span class="sxs-lookup"><span data-stu-id="b821a-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="b821a-125">No se centran en la consola al ejecutar</span><span class="sxs-lookup"><span data-stu-id="b821a-125">No focus on console when executing</span></span>

<span data-ttu-id="b821a-126">Para mantener el foco en el editor cuando se ejecuta con <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="b821a-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="b821a-127">El valor predeterminado es `true` por motivos de accesibilidad.</span><span class="sxs-lookup"><span data-stu-id="b821a-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="b821a-128">No se inician consola integrada en el inicio</span><span class="sxs-lookup"><span data-stu-id="b821a-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="b821a-129">Para detener la consola integrada en el inicio, establezca:</span><span class="sxs-lookup"><span data-stu-id="b821a-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="b821a-130">Todavía se iniciará el proceso de PowerShell de fondo, ya proporciona IntelliSense, análisis de secuencia de comandos, navegación de símbolos, etcetera. Pero no se muestra la consola.</span><span class="sxs-lookup"><span data-stu-id="b821a-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="b821a-131">Se supone que los archivos están PowerShell de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="b821a-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="b821a-132">Para hacer que los archivos nuevos/sin título, registrar como PowerShell de forma predeterminada:</span><span class="sxs-lookup"><span data-stu-id="b821a-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="b821a-133">Combinación de colores</span><span class="sxs-lookup"><span data-stu-id="b821a-133">Color scheme</span></span>

<span data-ttu-id="b821a-134">Hay un número de temas ISE para VSCode hacer que el editor parezca mucho el ISE.</span><span class="sxs-lookup"><span data-stu-id="b821a-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="b821a-135">En el [paleta de comandos] tipo `theme` obtener `Preferences: Color Theme` y presione <kbd>ENTRAR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b821a-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="b821a-136">En la lista desplegable, seleccione `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="b821a-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="b821a-137">Puede establecer en este tema en la configuración con:</span><span class="sxs-lookup"><span data-stu-id="b821a-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="b821a-138">Explorador de comando de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b821a-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="b821a-139">Gracias a los trabajos de [ @corbob ](https://github.com/corbob), la extensión de PowerShell tiene los comienzos de su propio explorador de comando.</span><span class="sxs-lookup"><span data-stu-id="b821a-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="b821a-140">En el [paleta de comandos], escriba `PowerShell Command Explorer` y presione <kbd>ENTRAR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b821a-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="b821a-141">Abrir en el ISE</span><span class="sxs-lookup"><span data-stu-id="b821a-141">Open in the ISE</span></span>

<span data-ttu-id="b821a-142">Si finalmente desean abrir un archivo en el ISE de todos modos, puede usar <kbd>MAYÚS</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b821a-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="b821a-143">Otros recursos</span><span class="sxs-lookup"><span data-stu-id="b821a-143">Other resources</span></span>

- <span data-ttu-id="b821a-144">tiene 4sysops [un excelente artículo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sobre la configuración de VSCode para que sea más parecido del ISE.</span><span class="sxs-lookup"><span data-stu-id="b821a-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="b821a-145">Tiene Mike F Robbins [una excelente publicación](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sobre la configuración de VSCode.</span><span class="sxs-lookup"><span data-stu-id="b821a-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="b821a-146">Obtenga información sobre PowerShell tiene [una escritura excelente seguridad](https://www.learnpwsh.com/setup-vs-code-for-powershell/) en Introducción VSCode programa de instalación de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b821a-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="b821a-147">Más opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="b821a-147">More settings</span></span>

<span data-ttu-id="b821a-148">Si necesita más maneras de hacer que VSCode le resulte más familiar para los usuarios ISE, contribuyen a este documento. Si hay una configuración de compatibilidad que busca, pero no se puede encontrar alguna forma de habilitarlo, [abra una incidencia](https://github.com/PowerShell/vscode-powershell/issues/new/choose) y pregunte!</span><span class="sxs-lookup"><span data-stu-id="b821a-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="b821a-149">¡Siempre estamos encantados de Aceptar pr y contribuciones también!</span><span class="sxs-lookup"><span data-stu-id="b821a-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="b821a-150">Sugerencias de VSCode</span><span class="sxs-lookup"><span data-stu-id="b821a-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="b821a-151">Paleta de comandos</span><span class="sxs-lookup"><span data-stu-id="b821a-151">Command Palette</span></span>

<span data-ttu-id="b821a-152"><kbd>F1</kbd> o <kbd>Ctrl</kbd>+<kbd>MAYÚS</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Desplazar</kbd>+<kbd>P</kbd> en macOS)</span><span class="sxs-lookup"><span data-stu-id="b821a-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="b821a-153">Una forma práctica de ejecutar comandos en VSCode.</span><span class="sxs-lookup"><span data-stu-id="b821a-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="b821a-154">Para obtener más información, consulte [los documentos de VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="b821a-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Paleta de comandos]: #command-palette
[Command Palette]: #command-palette
