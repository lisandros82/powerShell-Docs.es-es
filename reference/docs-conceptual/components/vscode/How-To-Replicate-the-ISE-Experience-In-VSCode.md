---
title: Cómo replicar la experiencia de ISE en Visual Studio Code
description: Cómo replicar la experiencia de ISE en Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012490"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Cómo replicar la experiencia de ISE en Visual Studio Code

Mientras que la extensión de PowerShell para VSCode no busca paridad completa con el ISE de PowerShell, hay características que hacen que la experiencia de VSCode más natural para los usuarios del ISE.

Este documento trata de lista, puede configurar en VSCode para que el usuario experimente un poco más conocidos en comparación con el ISE.

## <a name="key-bindings"></a>Enlaces de teclado

| Función                              | Enlace de ISE                  | Enlace de VSCode                              |
| ----------------                      | -----------                  | --------------                              |
| Interrupción y salto de depurador          | <kbd>CTRL</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Ejecutar texto/resaltado de línea actual | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Lista de fragmentos de código disponibles               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>CTRL</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Enlaces de teclado personalizados

También puede [configurar sus propios enlaces claves](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) en VSCode también.

## <a name="tab-completion"></a>Finalización con tabulación

Para habilitar más ISE similar a la finalización con tabulación, agregue esta configuración:

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> Esta configuración se ha agregado directamente en VSCode (en lugar de en la extensión). Su comportamiento viene determinado por VSCode directamente y no se puede cambiar la extensión.

## <a name="no-focus-on-console-when-executing"></a>No se centran en la consola al ejecutar

Para mantener el foco en el editor cuando se ejecuta con <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

El valor predeterminado es `true` por motivos de accesibilidad.

## <a name="dont-start-integrated-console-on-startup"></a>No se inician consola integrada en el inicio

Para detener la consola integrada en el inicio, establezca:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> Todavía se iniciará el proceso de PowerShell de fondo, ya proporciona IntelliSense, análisis de secuencia de comandos, navegación de símbolos, etcetera. Pero no se muestra la consola.

## <a name="assume-files-are-powershell-by-default"></a>Se supone que los archivos están PowerShell de forma predeterminada

Para hacer que los archivos nuevos/sin título, registrar como PowerShell de forma predeterminada:

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>Combinación de colores

Hay un número de temas ISE para VSCode hacer que el editor parezca mucho el ISE.

En el [paleta de comandos] tipo `theme` obtener `Preferences: Color Theme` y presione <kbd>ENTRAR</kbd>.
En la lista desplegable, seleccione `PowerShell ISE`.

Puede establecer en este tema en la configuración con:

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>Explorador de comando de PowerShell

Gracias a los trabajos de [ @corbob ](https://github.com/corbob), la extensión de PowerShell tiene los comienzos de su propio explorador de comando.

En el [paleta de comandos], escriba `PowerShell Command Explorer` y presione <kbd>ENTRAR</kbd>.

## <a name="open-in-the-ise"></a>Abrir en el ISE

Si finalmente desean abrir un archivo en el ISE de todos modos, puede usar <kbd>MAYÚS</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Otros recursos

- tiene 4sysops [un excelente artículo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sobre la configuración de VSCode para que sea más parecido del ISE.
- Tiene Mike F Robbins [una excelente publicación](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sobre la configuración de VSCode.
- Obtenga información sobre PowerShell tiene [una escritura excelente seguridad](https://www.learnpwsh.com/setup-vs-code-for-powershell/) en Introducción VSCode programa de instalación de PowerShell.

## <a name="more-settings"></a>Más opciones de configuración

Si necesita más maneras de hacer que VSCode le resulte más familiar para los usuarios ISE, contribuyen a este documento. Si hay una configuración de compatibilidad que busca, pero no se puede encontrar alguna forma de habilitarlo, [abra una incidencia](https://github.com/PowerShell/vscode-powershell/issues/new/choose) y pregunte!

¡Siempre estamos encantados de Aceptar pr y contribuciones también!

## <a name="vscode-tips"></a>Sugerencias de VSCode

### <a name="command-palette"></a>Paleta de comandos

<kbd>F1</kbd> o <kbd>Ctrl</kbd>+<kbd>MAYÚS</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Desplazar</kbd>+<kbd>P</kbd> en macOS)

Una forma práctica de ejecutar comandos en VSCode.
Para obtener más información, consulte [los documentos de VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Paleta de comandos]: #command-palette
