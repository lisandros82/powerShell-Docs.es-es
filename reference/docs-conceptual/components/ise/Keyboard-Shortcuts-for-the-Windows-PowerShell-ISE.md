---
ms.date: 01/02/2020
keywords: powershell, cmdlet
title: Métodos abreviados de teclado para Windows PowerShell ISE
ms.openlocfilehash: ee1b5961f8528d44330345bc49368e61970861ca
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737056"
---
# <a name="keyboard-shortcuts-for-the-windows-powershell-ise"></a>Métodos abreviados de teclado para Windows PowerShell ISE

Use los siguientes métodos abreviados de teclado para realizar acciones en el Entorno de scripting integrado (ISE) de Windows PowerShell®. Windows PowerShell ISE está disponible como parte de los sistemas operativos Windows Server y cliente de Windows, pero también se puede instalar en algunos sistemas operativos anteriores de Windows como parte del [paquete de descarga de Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881).

## <a name="keyboard-shortcuts-for-editing-text"></a>Métodos abreviados de teclado para editar texto

Puede usar los siguientes métodos abreviados de teclado cuando edite texto.

|              Acción              |       Métodos abreviados de teclado.       |                                                                                                                                                 Usar en                                                                                                                                                 |
| -------------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Ayuda**                         | <kbd>F1</kbd>                  | Panel de scripts **Importante:** Puede especificar que la ayuda de <kbd>F1</kbd> proceda de la biblioteca de TechNet en la ayuda descargada o web (consulte `Update-Help`). Para realizar la selección, haga clic en **Herramientas**, **Opciones** y, a continuación, en la pestaña **Configuración General**, active o desactive **Usar Ayuda local en lugar de contenido en línea.** |
| **Copy**                         | <kbd>CTRL</kbd>+<kbd>C</kbd>   | Panel de scripts, Panel de comandos y Panel de salida                                                                                                                                                                                                                                                                 |
| **Cortar**                          | <kbd>CTRL</kbd>+<kbd>X</kbd>   | Panel de scripts, Panel de comandos                                                                                                                                                                                                                                                                              |
| **Expandir o contraer la esquematización** | <kbd>CTRL</kbd>+<kbd>M</kbd>   | Panel de scripts                                                                                                                                                                                                                                                                                            |
| **Buscar en el script**               | <kbd>CTRL</kbd>+<kbd>F</kbd>   | Panel de scripts                                                                                                                                                                                                                                                                                            |
| **Buscar siguiente en el script**          | <kbd>F3</kbd>                  | Panel de scripts                                                                                                                                                                                                                                                                                            |
| **Buscar anterior en el script**      | <kbd>MAYÚS</kbd>+<kbd>F3</kbd> | Panel de scripts                                                                                                                                                                                                                                                                                            |
| **Buscar llave que coincida**          | <kbd>CTRL</kbd>+<kbd>]</kbd>   | Panel de scripts                                                                                                                                                                                                                                                                                            |
| **Pegar**                        | <kbd>CTRL</kbd>+<kbd>V</kbd>   | Panel de scripts, Panel de comandos                                                                                                                                                                                                                                                                              |
| **Rehacer**                         | <kbd>CTRL</kbd>+<kbd>Y</kbd>   | Panel de scripts, Panel de comandos                                                                                                                                                                                                                                                                              |
| **Reemplazar en el script**            | <kbd>CTRL</kbd>+<kbd>H</kbd>   | Panel de scripts                                                                                                                                                                                                                                                                                            |
| **Guardar**                         | <kbd>CTRL</kbd>+<kbd>S</kbd>   | Panel de scripts                                                                                                                                                                                                                                                                                            |
| **Seleccionar todo**                   | <kbd>CTRL</kbd>+<kbd>A</kbd>   | Panel de scripts, Panel de comandos y Panel de salida                                                                                                                                                                                                                                                                 |
| **Mostrar fragmentos de código**                | <kbd>CTRL</kbd>+<kbd>J</kbd>   | Panel de scripts, Panel de comandos                                                                                                                                                                                                                                                                              |
| **Deshacer**                         | <kbd>CTRL</kbd>+<kbd>Z</kbd>   | Panel de scripts, Panel de comandos                                                                                                                                                                                                                                                                              |

## <a name="keyboard-shortcuts-for-running-scripts"></a>Métodos abreviados de teclado para ejecutar scripts

Puede usar los siguientes métodos abreviados de teclado cuando ejecute scripts en el panel de scripts.

|            Acción            |                                                                                                             Método abreviado de teclado                                                                                                             |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nuevo**                      | <kbd>CTRL</kbd>+<kbd>N</kbd>                                                                                                                                                                                                              |
| **Abrir**                     | <kbd>CTRL</kbd>+<kbd>O</kbd>                                                                                                                                                                                                              |
| **Ejecutar**                      | <kbd>F5</kbd>                                                                                                                                                                                                                             |
| **Ejecutar selección**            | <kbd>F8</kbd>                                                                                                                                                                                                                             |
| **Detener la ejecución**           | <kbd>CTRL</kbd>+<kbd>INTERRUMPIR</kbd>. <kbd>CTRL</kbd>+<kbd>C</kbd> se puede usar cuando el contexto no es ambiguo (cuando no hay texto seleccionado).                                                                                              |
| **Tabulación** (para el siguiente script)     | <kbd>CTRL</kbd>+<kbd>TAB</kbd> **Nota:** La pestaña para el siguiente script solo funciona si tiene una sola pestaña de Windows PowerShell abierta, o bien si tiene más de una abierta pero el foco está en el panel de scripts.               |
| **Tabulación** (para el script anterior) | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>TAB</kbd> **Nota:** La pestaña para el script anterior solo funciona si tiene una sola pestaña de Windows PowerShell abierta, o bien si tiene más de una abierta pero el foco está en el panel de scripts. |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Métodos abreviados de teclado para personalizar la vista

Puede usar los siguientes métodos abreviados de teclado cuando personalice la vista en Windows PowerShell ISE. Son accesibles desde todos los paneles de la aplicación.

|                        Acción                         |               Método abreviado de teclado               |
| ----------------------------------------------------- | --------------------------------------------- |
| **Ir al panel de comandos (v2) o el panel de consola (v3 y versiones posteriores)** | <kbd>CTRL</kbd>+<kbd>D</kbd>                  |
| **Ir al panel de salida (solo v2)**                       | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>O</kbd> |
| **Ir al panel de scripts**                                 | <kbd>CTRL</kbd>+<kbd>I</kbd>                  |
| **Mostrar el panel de scripts**                                  | <kbd>CTRL</kbd>+<kbd>R</kbd>                  |
| **Ocultar el panel de scripts**                                  | <kbd>CTRL</kbd>+<kbd>R</kbd>                  |
| **Subir el panel de scripts**                               | <kbd>CTRL</kbd>+<kbd>1</kbd>                  |
| **Mover el panel de scripts a la derecha**                            | <kbd>CTRL</kbd>+<kbd>2</kbd>                  |
| **Maximizar el panel de scripts**                              | <kbd>CTRL</kbd>+<kbd>3</kbd>                  |
| **Acercar**                                           | <kbd>CTRL</kbd>+<kbd>+</kbd>                  |
| **Alejar**                                          | <kbd>CTRL</kbd>+<kbd>-</kbd>                  |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Métodos abreviados de teclado para depurar scripts

Puede usar los siguientes métodos abreviados de teclado cuando depure scripts.

|           Acción           |               Método abreviado de teclado                |                Usar en                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **Ejecutar o continuar**           | <kbd>F5</kbd>                                  | Panel de scripts, al depurar un script |
| **Depurar paso a paso por instrucciones**              | <kbd>F11</kbd>                                 | Panel de scripts, al depurar un script |
| **Depurar paso a paso por procedimientos**              | <kbd>F10</kbd>                                 | Panel de scripts, al depurar un script |
| **Depurar paso a paso para salir**               | <kbd>MAYÚS</kbd>+<kbd><kbd>F11</kbd></kbd>     | Panel de scripts, al depurar un script |
| **Mostrar pila de llamadas**     | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>D</kbd>  | Panel de scripts, al depurar un script |
| **Mostrar puntos de interrupción**       | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>L</kbd>  | Panel de scripts, al depurar un script |
| **Alternar punto de interrupción**      | <kbd>F9</kbd>                                  | Panel de scripts, al depurar un script |
| **Quitar todos los puntos de interrupción** | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>F9</kbd> | Panel de scripts, al depurar un script |
| **Detener el depurador**          | <kbd>MAYÚS</kbd>+<kbd>F5</kbd>                 | Panel de scripts, al depurar un script |

> [!NOTE]
> También puede usar los métodos abreviados de teclado diseñados para la consola de Windows PowerShell cuando depure scripts en Windows PowerShell ISE. Para usar estos métodos abreviados, debe escribir el método abreviado en el panel de comandos y presionar <kbd>ENTRAR</kbd>.

|                        Acción                        | Método abreviado de teclado |                Usar en                 |
| ---------------------------------------------------- | ----------------- | ------------------------------------- |
| **Continuar**                                         | `C`               | Panel de consola, al depurar un script |
| **Depurar paso a paso por instrucciones**                                        | `S`               | Panel de consola, al depurar un script |
| **Depurar paso a paso por procedimientos**                                        | `V`               | Panel de consola, al depurar un script |
| **Depurar paso a paso para salir**                                         | `O`               | Panel de consola, al depurar un script |
| **Repetir el último comando** (para depurar paso a paso por instrucciones o por procedimientos) | <kbd>ENTRAR</kbd>  | Panel de consola, al depurar un script |
| **Mostrar pila de llamadas**                               | `K`               | Panel de consola, al depurar un script |
| **Detener la depuración**                                   | `Q`               | Panel de consola, al depurar un script |
| **Enumerar el script**                                  | `L`               | Panel de consola, al depurar un script |
| **Mostrar los comandos de depuración de la consola**               | `H` o `?`        | Panel de consola, al depurar un script |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Métodos abreviados de teclado para las pestañas de Windows PowerShell

Puede usar los siguientes métodos abreviados de teclado cuando use las pestañas de Windows PowerShell.

|             Acción              |                                                        Método abreviado de teclado                                                        |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Cerrar la pestaña de PowerShell**        | <kbd>CTRL</kbd>+<kbd>W</kbd>                                                                                                    |
| **Nueva pestaña de PowerShell**          | <kbd>CTRL</kbd>+<kbd>T</kbd>                                                                                                    |
| **Pestaña de PowerShell anterior**     | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>TAB</kbd>. Este método abreviado solo funciona si no hay archivos abiertos en ninguna pestaña de Windows PowerShell. |
| **Pestaña de Windows PowerShell siguiente** | <kbd>CTRL</kbd>+<kbd>TAB</kbd>. Este método abreviado solo funciona si no hay archivos abiertos en ninguna pestaña de Windows PowerShell.                  |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Métodos abreviados de teclado para iniciar y salir

Puede usar los siguientes métodos abreviados de teclado para iniciar la consola de Windows PowerShell (PowerShell.exe) o para salir de Windows PowerShell ISE.

|                        Acción                        |               Método abreviado de teclado               |
| ---------------------------------------------------- | --------------------------------------------- |
| **Salir**                                             | <kbd>ALT</kbd>+<kbd>F4</kbd>                  |
| **Iniciar PowerShell.exe** (consola de Windows PowerShell) | <kbd>CTRL</kbd>+<kbd>MAYÚS</kbd>+<kbd>P</kbd> |

## <a name="see-also"></a>Consulte también

- [PowerShell Magazine: The Complete List of Windows PowerShell ISE Keyboard Shortcuts](https://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/) (Lista completa de métodos abreviados de teclado de Windows PowerShell ISE)
