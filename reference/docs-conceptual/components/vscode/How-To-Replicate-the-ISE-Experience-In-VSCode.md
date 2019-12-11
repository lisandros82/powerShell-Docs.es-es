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
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Cómo replicar la experiencia de ISE en Visual Studio Code

Si bien la extensión de PowerShell para VSCode no busca una paridad de características completa con el ISE de PowerShell, existen características para hacer que la experiencia de VSCode sea más natural para los usuarios de ISE.

El objetivo de este documento es confeccionar un listado con las opciones que puede configurar en VSCode para que la experiencia del usuario sea un poco más familiar en comparación con el ISE.

## <a name="key-bindings"></a>Enlaces de teclado

| Función                              | Enlace de ISE                  | Enlace de VSCode                              |
| ----------------                      | -----------                  | --------------                              |
| Depurador de interrupción          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Ejecutar línea actual/texto resaltado | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Lista de fragmentos de código disponibles               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Enlaces de teclado personalizados

En VSCode también puede [configurar sus propios enlaces de teclado](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings).

## <a name="simplified-ise-like-ui"></a>Interfaz de usuario de tipo ISE simplificada

Si quiere simplificar la interfaz de usuario de Visual Studio Code para que se asemeje más a la interfaz de usuario del ISE, aplique estas dos configuraciones:

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

Se ocultarán las secciones de la barra de actividades y la barra lateral de depuración que se encuentran debajo del cuadro rojo:

![La sección resaltada incluye la barra de actividades y la barra lateral de depuración](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

El resultado final tiene el siguiente aspecto:

![Vista simplificada de VS Code](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>Finalización con tabulación

Para habilitar una finalización con tabulación más similar a ISE, agregue este parámetro:

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> Esta configuración se ha agregado directamente a VSCode (y no a la extensión). Su comportamiento viene determinado por VSCode directamente y no se puede cambiar por la extensión.

## <a name="no-focus-on-console-when-executing"></a>No centrarse en la consola al ejecutar

Para mantener el foco en el editor cuando se ejecuta con <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

El valor predeterminado es `true` por motivos de accesibilidad.

## <a name="dont-start-integrated-console-on-startup"></a>No iniciar la consola integrada en el inicio

Para detener la consola integrada en el inicio, configure:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> El proceso de PowerShell en segundo plano seguirá iniciándose, ya que proporciona IntelliSense, análisis de scripts, navegación de símbolos, etc. Pero la consola no se mostrará.

## <a name="assume-files-are-powershell-by-default"></a>Suponer que los archivos son de PowerShell de manera predeterminada

Para tener archivos nuevos/sin título, regístrelos como de PowerShell de forma predeterminada:

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a>Combinación de colores

Hay una serie de temas de ISE disponibles para VSCode para que el editor se parezca mucho más a ISE.

En la [Paleta de comandos], escriba `theme` para obtener `Preferences: Color Theme` y presione <kbd>Entrar</kbd>.
En la lista desplegable, seleccione `PowerShell ISE`.

Puede establecer en este tema en la configuración con:

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a>Explorador de comandos de PowerShell

Gracias al trabajo de [@corbob](https://github.com/corbob), la extensión de PowerShell tiene un incipiente explorador de comandos propio.

En la [Paleta de comandos], escriba `PowerShell Command Explorer` y presione <kbd>Entrar</kbd>.

## <a name="open-in-the-ise"></a>Abrir en el ISE

Si finalmente desea abrir un archivo en el ISE de todos modos, puede usar <kbd>Mayús</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Otros recursos

- 4sysops tiene [un excelente artículo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sobre la configuración de VSCode para que sea más parecido al ISE.
- Mike F Robbins tiene [una excelente publicación](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sobre la configuración de VSCode.
- Learn PowerShell tiene un [excelente documento](https://www.learnpwsh.com/setup-vs-code-for-powershell/) sobre la configuración de VSCode para PowerShell.

## <a name="more-settings"></a>Más opciones de configuración

Si conoce más formas de hacer que VSCode resulte más familiar para los usuarios de ISE, haga su aportación a este documento. Si busca una configuración de compatibilidad pero no encuentra la manera de habilitarla, [abra una incidencia](https://github.com/PowerShell/vscode-powershell/issues/new/choose) y pregunte.

Siempre estamos encantados de aceptar solicitudes de incorporación de cambios y aportaciones.

## <a name="vscode-tips"></a>Sugerencias de VSCode

### <a name="command-palette"></a>Paleta de comandos

<kbd>F1</kbd> O <kbd>Ctrl</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd> en macOS)

Una forma práctica de ejecutar comandos en VSCode.
Para obtener más información, vea [la documentación de VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Paleta de comandos]: #command-palette
