---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Accesibilidad en ISE de Windows PowerShell
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
ms.openlocfilehash: 78a001dbe43a0b005d10a817e05e4cc7a72f5bd0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058461"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Accesibilidad en ISE de Windows PowerShell

En este tema se describen las características de accesibilidad del Entorno de scripting integrado (ISE) de Windows PowerShell que pueden resultar útiles.

* [Cómo cambiar el tamaño y la ubicación de los paneles de consola y de scripts](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Métodos abreviados de teclado para editar texto](#keyboard-shortcuts-for-editing-text)
* [Métodos abreviados de teclado para ejecutar scripts](#keyboard-shortcuts-for-running-scripts)
* [Métodos abreviados de teclado para personalizar la vista](#keyboard-shortcuts-for-customizing-the-view)
* [Métodos abreviados de teclado para depurar scripts](#keyboard-shortcuts-for-debugging-scripts)
* [Métodos abreviados de teclado para las pestañas de Windows PowerShell](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Métodos abreviados de teclado para iniciar y salir](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft tiene el compromiso de que todas las personas puedan utilizar fácilmente sus productos y servicios. En los siguientes temas se proporciona información sobre las características, los productos y los servicios que permiten que Windows PowerShell ISE sea más accesible para las personas con discapacidades.

Windows PowerShell ISE admite el modo de contraste alto. Para las personas con discapacidad visual, existe información de punto de interrupción disponible a través de los cmdlets de administración de puntos de interrupción, como [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) y [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Para obtener más información, consulte "Cómo administrar los puntos de interrupción" en [Cómo depurar scripts en ISE de Windows PowerShell](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Además de las características de accesibilidad y las utilidades de Microsoft Windows, las siguientes características hacen que Windows PowerShell ISE sea más accesible para las personas con discapacidades:

- Métodos abreviados de teclado.

- La tabla de colores de sintaxis y la capacidad de modificar otras opciones de color mediante el objeto de scripting [$psISE.Options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb).

- Cambio de tamaño del texto.

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Cómo cambiar el tamaño y la ubicación de los paneles de consola y de scripts

Puede usar los siguientes pasos para cambiar el tamaño y la ubicación del panel de consola y el panel de scripts. Al abrir de nuevo Windows PowerShell ISE, se conservarán los cambios realizados en el tamaño y la ubicación.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Para cambiar el tamaño del panel de scripts y el panel de consola

1. Detenga el puntero en la línea de división entre el panel de scripts y el panel de consola.

2. Cuando el puntero del ratón cambie a una flecha con dos puntas, arrastre el borde para cambiar el tamaño del panel.

### <a name="to-move-the-script-pane-and-console-pane"></a>Para mover el panel de scripts y el panel de consola

Realice una de las siguientes acciones:

- Para mover el panel de scripts encima del panel de consola, presione **CTRL+1** o, en la barra de herramientas, haga clic en el icono **Mostrar panel de scripts arriba** o, en el menú **Ver**, haga clic en **Mostrar panel de scripts arriba**.

- Para mover el panel de scripts a la derecha del panel de consola, presione **CTRL+2** o, en la barra de herramientas, haga clic en el icono **Mostrar panel de scripts a la derecha** o, en el menú **Ver**, haga clic en **Mostrar panel de scripts a la derecha**.

- Para maximizar el panel de scripts, presione **CTRL+3** o, en la barra de herramientas, haga clic en el icono **Mostrar panel de scripts maximizado** o, en el menú **Ver**, haga clic en **Mostrar panel de scripts maximizado**.

- Para maximizar el panel de consola y ocultar el panel de scripts, en el extremo derecho de la fila de pestañas, haga clic en el icono **Ocultar panel de scripts** y, en el menú **Ver**, haga clic para anular la selección de la opción de menú **Mostrar panel de scripts**.

- Para mostrar el panel de scripts cuando el panel de consola esté maximizado, en el extremo derecho de la fila de pestañas, haga clic en el icono **Mostrar panel de scripts** o, en el menú **Ver**, haga clic para seleccionar la opción de menú **Mostrar panel de scripts**.

## <a name="keyboard-shortcuts-for-editing-text"></a>Métodos abreviados de teclado para editar texto

Puede usar los siguientes métodos abreviados de teclado cuando edite texto.

|Acción|Métodos abreviados de teclado.|Usar en|
|----------|----------------------|----------|
|**Copiar**|Ctrl+C|Panel de scripts, panel de consola|
|**Cortar**|CTRL+X|Panel de scripts, panel de consola|
|**Buscar en el script**|CTRL+F|Panel de scripts|
|**Buscar siguiente en el script**|F3|Panel de scripts|
|**Buscar anterior en el script**|MAYÚS+F3|Panel de scripts|
|**Pegar**|CTRL+V|Panel de scripts, panel de consola|
|**Rehacer**|CTRL+Y|Panel de scripts, panel de consola|
|**Reemplazar en el script**|CTRL+H|Panel de scripts|
|**Guardar**|CTRL+S|Panel de scripts|
|**Seleccionar todo**|CTRL+A|Panel de scripts, panel de consola|
|**Deshacer**|CTRL+Z|Panel de scripts, panel de consola|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Métodos abreviados de teclado para ejecutar scripts

Puede usar los siguientes métodos abreviados de teclado cuando ejecute scripts en el panel de scripts.

|Acción|Método abreviado de teclado|
|----------|---------------------|
|**Nuevo**|CTRL+N|
|**Abrir**|CTRL+O|
|**Ejecutar**|F5|
|**Ejecutar selección**|F8|
|**Detener la ejecución**|CTRL+INTER. CTRL+C se puede usar cuando el contexto no es ambiguo (cuando no hay ningún texto seleccionado).|
|**Tabulación** (para el siguiente script)|CTRL+TAB **Nota:** El desplazamiento con la tecla TAB al siguiente script solo funciona si hay una sola pestaña de PowerShell abierta, o bien si hay más de una abierta, pero el foco está en el panel de scripts.|
|**Tabulación** (para el script anterior)|CTRL+SHIFT+TAB **Nota:** El desplazamiento con la tecla TAB al script anterior solo funciona si hay una sola pestaña de PowerShell abierta, o si hay más de una abierta, pero el foco está en el panel de scripts.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Métodos abreviados de teclado para personalizar la vista

Puede usar los siguientes métodos abreviados de teclado cuando personalice la vista en Windows PowerShell ISE. Son accesibles desde todos los paneles de la aplicación.

|Acción|Método abreviado de teclado|
|----------|---------------------|
|**Ir a panel de consola**|CTRL+D|
|**Ir al panel de scripts**|CTRL+I|
|**Mostrar el panel de scripts**|CTRL+R|
|**Ocultar el panel de scripts**|CTRL+R|
||
|**Subir el panel de scripts**|CTRL+1|
|**Mover el panel de scripts a la derecha**|CTRL+2|
|**Maximizar el panel de scripts**|CTRL+3|
|**Acercar**|CTRL+SIGNO MÁS|
|**Alejar**|CTRL+SIGNO MENOS|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Métodos abreviados de teclado para depurar scripts

Puede usar los siguientes métodos abreviados de teclado cuando depure scripts.

|Acción|Método abreviado de teclado|Usar en|
|----------|---------------------|----------|
|**Ejecutar o continuar**|F5|Panel de scripts, al depurar un script|
|**Depurar paso a paso por instrucciones**|F11|Panel de scripts, al depurar un script|
|**Depurar paso a paso por procedimientos**|F10|Panel de scripts, al depurar un script|
|**Depurar paso a paso para salir**|MAYÚS+F11|Panel de scripts, al depurar un script|
|**Mostrar pila de llamadas**|CTRL+MAYÚS+D|Panel de scripts, al depurar un script|
|**Mostrar puntos de interrupción**|CTRL+MAYÚS+L|Panel de scripts, al depurar un script|
|**Alternar punto de interrupción**|F9|Panel de scripts, al depurar un script|
|**Quitar todos los puntos de interrupción**|CTRL+MAYÚS+F9|Panel de scripts, al depurar un script|
|**Detener el depurador**|MAYÚS+F5|Panel de scripts, al depurar un script|

> [!NOTE]
>
> También puede usar los métodos abreviados de teclado diseñados para la consola de Windows PowerShell cuando depure scripts en Windows PowerShell ISE. Para usar estos métodos abreviados, debe escribir el método abreviado en el panel de consola y presionar ENTRAR.

|Acción|Método abreviado de teclado|Usar en|
|----------|---------------------|----------|
|**Continuar**|C|Panel de consola, al depurar un script|
|**Depurar paso a paso por instrucciones**|S|Panel de consola, al depurar un script|
|**Depurar paso a paso por procedimientos**|V|Panel de consola, al depurar un script|
|**Depurar paso a paso para salir**|O|Panel de consola, al depurar un script|
|**Repetir el último comando** (para depurar paso a paso por instrucciones o por procedimientos)|ENTRAR|Panel de consola, al depurar un script|
|**Mostrar pila de llamadas**|K|Panel de consola, al depurar un script|
|**Detener la depuración**|Q|Panel de consola, al depurar un script|
|**Enumerar el script**|L|Panel de consola, al depurar un script|
|**Mostrar los comandos de depuración de la consola**|H o ?|Panel de consola, al depurar un script|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Métodos abreviados de teclado para las pestañas de Windows PowerShell

Puede usar los siguientes métodos abreviados de teclado cuando use las pestañas de Windows PowerShell.

|Acción|Método abreviado de teclado|
|----------|---------------------|
|**Cerrar la pestaña de PowerShell**|CTRL+W|
|**Nueva pestaña de PowerShell**|CTRL+T|
|**Pestaña de PowerShell anterior**|CTRL+MAYÚS+TAB Este método abreviado solo funciona si no hay archivos abiertos en ninguna pestaña de PowerShell.|
|**Pestaña de Windows PowerShell siguiente**|CTRL+TAB Este método abreviado solo funciona si no hay archivos abiertos en ninguna pestaña de PowerShell.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Métodos abreviados de teclado para iniciar y salir

Puede usar los siguientes métodos abreviados de teclado para iniciar la consola de Windows PowerShell (PowerShell.exe) o para salir de Windows PowerShell ISE.

|Acción|Método abreviado de teclado|
|----------|---------------------|
|**Salir**|ALT+F4|
|**Iniciar PowerShell.exe** (consola de Windows PowerShell)|CTRL+MAYÚS+P|

## <a name="see-also"></a>Véase también

[Presentación de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)