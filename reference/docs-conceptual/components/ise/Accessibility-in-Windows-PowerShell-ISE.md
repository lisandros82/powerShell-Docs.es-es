---
ms.date: 12/19/2019
keywords: powershell, cmdlet
title: Accesibilidad en ISE de Windows PowerShell
ms.openlocfilehash: e618daca98d76f767a8b60a3425760bfc0bd0f64
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736290"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Accesibilidad en ISE de Windows PowerShell

En este tema se describen las características de accesibilidad del Entorno de scripting integrado (ISE) de Windows PowerShell que pueden resultar útiles.

- [Cómo cambiar el tamaño y la ubicación de los paneles de consola y de scripts](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
- [Métodos abreviados de teclado para editar texto](#keyboard-shortcuts-for-editing-text)
- [Métodos abreviados de teclado para ejecutar scripts](#keyboard-shortcuts-for-running-scripts)
- [Métodos abreviados de teclado para personalizar la vista](#keyboard-shortcuts-for-customizing-the-view)
- [Métodos abreviados de teclado para depurar scripts](#keyboard-shortcuts-for-debugging-scripts)
- [Métodos abreviados de teclado para las pestañas de Windows PowerShell](#keyboard-shortcuts-for-windows-powershell-tabs)
- [Métodos abreviados de teclado para iniciar y salir](#keyboard-shortcuts-for-starting-and-exiting)
- [Administración de puntos de interrupción con cmdlets](#breakpoint-management)

Microsoft tiene el compromiso de que todas las personas puedan utilizar fácilmente sus productos y servicios. En los siguientes temas se proporciona información sobre las características, los productos y los servicios que permiten que Windows PowerShell ISE sea más accesible para las personas con discapacidades.

Además de las características de accesibilidad y las utilidades de Microsoft Windows, las siguientes características hacen que Windows PowerShell ISE sea más accesible para las personas con discapacidades:

- Métodos abreviados de teclado.

- La tabla de colores de sintaxis y la capacidad de modificar otras opciones de color mediante el objeto de scripting [$psISE.Options](object-model/The-ISEOptions-Object.md).

- Cambio de tamaño del texto.

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Cómo cambiar el tamaño y la ubicación de los paneles de consola y de scripts

Puede usar los siguientes pasos para cambiar el tamaño y la ubicación del panel de consola y el panel de scripts. Al abrir de nuevo Windows PowerShell ISE, se conservarán los cambios realizados en el tamaño y la ubicación.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Para cambiar el tamaño del panel de scripts y el panel de consola

1. Detenga el puntero en la línea de división entre el panel de scripts y el panel de consola.

2. Cuando el puntero del ratón cambie a una flecha con dos puntas, arrastre el borde para cambiar el tamaño del panel.

### <a name="to-move-the-script-pane-and-console-pane"></a>Para mover el panel de scripts y el panel de consola

Realice una de las siguientes acciones:

- Para mover el panel de scripts encima del panel de consola, presione <kbd>CTRL</kbd>+<kbd>1</kbd> o, en la barra de herramientas, haga clic en el icono **Mostrar panel de scripts arriba** o, en el menú **Ver**, haga clic en **Mostrar panel de scripts arriba**.

- Para mover el panel de scripts a la derecha del panel de consola, presione <kbd>CTRL</kbd>+<kbd>2</kbd> o, en la barra de herramientas, haga clic en el icono **Mostrar panel de scripts** a la derecha o, en el menú **Ver**, haga clic en **Mostrar panel de scripts a la derecha**.

- Para maximizar el panel de scripts, presione <kbd>CTRL</kbd>+<kbd>3</kbd> o, en la barra de herramientas, haga clic en el icono **Mostrar panel de scripts maximizado** o, en el menú **Ver**, haga clic en **Mostrar panel de scripts maximizado**.

- Para maximizar el panel de consola y ocultar el panel de scripts, en el extremo derecho de la fila de pestañas, haga clic en el icono **Ocultar panel de scripts** y, en el menú **Ver**, haga clic para anular la selección de la opción de menú **Mostrar panel de scripts**.

- Para mostrar el panel de scripts cuando el panel de consola esté maximizado, en el extremo derecho de la fila de pestañas, haga clic en el icono **Mostrar panel de scripts** o, en el menú **Ver**, haga clic para seleccionar la opción de menú **Mostrar panel de scripts**.

## <a name="keyboard-shortcuts-for-editing-text"></a>Métodos abreviados de teclado para editar texto

Puede usar los siguientes métodos abreviados de teclado cuando edite texto.

|           Acción            |       Métodos abreviados de teclado.       |          Usar en           |
| --------------------------- | ------------------------------ | ------------------------- |
| **Copy**                    | <kbd>CTRL</kbd>+<kbd>C</kbd>   | Panel de scripts, panel de consola |
| **Cortar**                     | <kbd>CTRL</kbd>+<kbd>X</kbd>   | Panel de scripts, panel de consola |
| **Buscar en el script**          | <kbd>CTRL</kbd>+<kbd>F</kbd>   | Panel de scripts               |
| **Buscar siguiente en el script**     | <kbd>F3</kbd>                  | Panel de scripts               |
| **Buscar anterior en el script** | <kbd>MAYÚS</kbd>+<kbd>F3</kbd> | Panel de scripts               |
| **Pegar**                   | <kbd>CTRL</kbd>+<kbd>V</kbd>   | Panel de scripts, panel de consola |
| **Rehacer**                    | <kbd>CTRL</kbd>+<kbd>Y</kbd>   | Panel de scripts, panel de consola |
| **Reemplazar en el script**       | <kbd>CTRL</kbd>+<kbd>H</kbd>   | Panel de scripts               |
| **Guardar**                    | <kbd>CTRL</kbd>+<kbd>S</kbd>   | Panel de scripts               |
| **Seleccionar todo**              | <kbd>CTRL</kbd>+<kbd>A</kbd>   | Panel de scripts, panel de consola |
| **Deshacer**                    | <kbd>CTRL</kbd>+<kbd>Z</kbd>   | Panel de scripts, panel de consola |

## <a name="keyboard-shortcuts-for-running-scripts"></a>Métodos abreviados de teclado para ejecutar scripts

Puede usar los siguientes métodos abreviados de teclado cuando ejecute scripts en el panel de scripts.

|            Acción            |                                                                                                     Método abreviado de teclado                                                                                                      |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nuevo**                      | <kbd>CTRL</kbd>+<kbd>N</kbd>                                                                                                                                                                                               |
| **Abrir**                     | <kbd>CTRL</kbd>+<kbd>O</kbd>                                                                                                                                                                                               |
| **Ejecutar**                      | <kbd>F5</kbd>                                                                                                                                                                                                              |
| **Ejecutar selección**            | <kbd>F8</kbd>                                                                                                                                                                                                              |
| **Detener la ejecución**           | <kbd>CTRL</kbd>+<kbd>INTERRUMPIR</kbd>. <kbd>CTRL</kbd>+<kbd>C</kbd> se puede usar cuando el contexto no es ambiguo (cuando no hay texto seleccionado).                                                                               |
| **Tabulación** (para el siguiente script)     | <kbd>CTRL</kbd>+<kbd>TAB</kbd> **Nota:** El desplazamiento con la tecla TAB al siguiente script solo funciona si hay una sola pestaña de PowerShell abierta, o bien si hay más de una abierta, pero el foco está en el panel de scripts.                |
| **Tabulación** (para el script anterior) | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>TAB</kbd> **Nota:** El desplazamiento con la tecla TAB al script anterior solo funciona si hay una sola pestaña de PowerShell abierta, o si hay más de una abierta, pero el foco está en el panel de scripts. |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Métodos abreviados de teclado para personalizar la vista

Puede usar los siguientes métodos abreviados de teclado cuando personalice la vista en Windows PowerShell ISE. Son accesibles desde todos los paneles de la aplicación.

|           Acción           |         Método abreviado de teclado        |
| -------------------------- | -------------------------------- |
| **Ir a panel de consola**     | <kbd>CTRL</kbd>+<kbd>D</kbd>     |
| **Ir al panel de scripts**      | <kbd>CTRL</kbd>+<kbd>I</kbd>     |
| **Mostrar el panel de scripts**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **Ocultar el panel de scripts**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **Subir el panel de scripts**    | <kbd>CTRL</kbd>+<kbd>1</kbd>     |
| **Mover el panel de scripts a la derecha** | <kbd>CTRL</kbd>+<kbd>2</kbd>     |
| **Maximizar el panel de scripts**   | <kbd>CTRL</kbd>+<kbd>3</kbd>     |
| **Acercar**                | <kbd>CTRL</kbd>+<kbd>MÁS</kbd>  |
| **Alejar**               | <kbd>CTRL</kbd>+<kbd>MENOS</kbd> |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Métodos abreviados de teclado para depurar scripts

Puede usar los siguientes métodos abreviados de teclado cuando depure scripts.

|           Acción           |               Método abreviado de teclado                |                Usar en                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **Ejecutar o continuar**           | <kbd>F5</kbd>                                  | Panel de scripts, al depurar un script |
| **Depurar paso a paso por instrucciones**              | <kbd>F11</kbd>                                 | Panel de scripts, al depurar un script |
| **Depurar paso a paso por procedimientos**              | <kbd>F10</kbd>                                 | Panel de scripts, al depurar un script |
| **Depurar paso a paso para salir**               | <kbd>MAYÚS</kbd>+<kbd>F11</kbd>                | Panel de scripts, al depurar un script |
| **Mostrar pila de llamadas**     | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>D</kbd>  | Panel de scripts, al depurar un script |
| **Mostrar puntos de interrupción**       | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>L</kbd>  | Panel de scripts, al depurar un script |
| **Alternar punto de interrupción**      | <kbd>F9</kbd>                                  | Panel de scripts, al depurar un script |
| **Quitar todos los puntos de interrupción** | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>F9</kbd> | Panel de scripts, al depurar un script |
| **Detener el depurador**          | <kbd>MAYÚS</kbd>+<kbd>F5</kbd>                 | Panel de scripts, al depurar un script |

> [!NOTE]
> También puede usar los métodos abreviados de teclado diseñados para la consola de Windows PowerShell cuando depure scripts en Windows PowerShell ISE. Para usar estos métodos abreviados, debe escribir el método abreviado en el panel de consola y presionar ENTRAR.

|                 Acción                  |      Método abreviado de teclado       |                Usar en                 |
| --------------------------------------- | ---------------------------- | ------------------------------------- |
| **Continuar**                            | <kbd>C</kbd>                 | Panel de consola, al depurar un script |
| **Depurar paso a paso por instrucciones**                           | <kbd>S</kbd>                 | Panel de consola, al depurar un script |
| **Depurar paso a paso por procedimientos**                           | <kbd>V</kbd>                 | Panel de consola, al depurar un script |
| **Depurar paso a paso para salir**                            | <kbd>O</kbd>                 | Panel de consola, al depurar un script |
| **Repetir el último comando**(Depurar paso a paso por instrucciones/por procedimientos) | <kbd>ENTRAR</kbd>             | Panel de consola, al depurar un script |
| **Mostrar pila de llamadas**                  | <kbd>K</kbd>                 | Panel de consola, al depurar un script |
| **Detener la depuración**                      | <kbd>Q</kbd>                 | Panel de consola, al depurar un script |
| **Enumerar el script**                     | <kbd>L</kbd>                 | Panel de consola, al depurar un script |
| **Mostrar los comandos de depuración de la consola**  | <kbd>H</kbd> o <kbd>?</kbd> | Panel de consola, al depurar un script |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Métodos abreviados de teclado para las pestañas de Windows PowerShell

Puede usar los siguientes métodos abreviados de teclado cuando use las pestañas de Windows PowerShell.

|             Acción              |                                 Método abreviado de teclado                                  |
| ------------------------------- | ---------------------------------------------------------------------------------- |
| **Cerrar la pestaña de PowerShell**        | <kbd>CTRL</kbd>+<kbd>W</kbd>                                                       |
| **Nueva pestaña de PowerShell**          | <kbd>CTRL</kbd>+<kbd>T</kbd>                                                       |
| **Pestaña de PowerShell anterior**     | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>TAB</kbd> (solo si no hay archivos abiertos en ninguna pestaña de PowerShell)                 |
| **Pestaña de Windows PowerShell siguiente** | <kbd>CTRL</kbd>+<kbd>TAB</kbd> (solo si no hay archivos abiertos en ninguna pestaña de PowerShell) |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Métodos abreviados de teclado para iniciar y salir

Puede usar los siguientes métodos abreviados de teclado para iniciar la consola de Windows PowerShell (**PowerShell.exe**) o para salir de Windows PowerShell ISE.

|                        Acción                         |               Método abreviado de teclado               |
| ----------------------------------------------------- | --------------------------------------------- |
| **Salir**                                              | <kbd>ALT</kbd>+<kbd>F4</kbd>                  |
| **Iniciar PowerShell.exe** (consola de Windows PowerShell) | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>P</kbd> |

## <a name="breakpoint-management"></a>Administración de puntos de interrupción

Para las personas con discapacidad visual, existe información de punto de interrupción disponible a través de los cmdlets de administración de puntos de interrupción, como [Get-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Get-PSBreakpoint.md) y [Set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md).
Para obtener más información, consulte "Cómo administrar los puntos de interrupción" en [Cómo depurar scripts en ISE de Windows PowerShell](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md).

## <a name="see-also"></a>Consulte también

[Presentación de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
