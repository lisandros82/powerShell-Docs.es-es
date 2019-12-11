---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Métodos abreviados de teclado para Windows PowerShell ISE
ms.openlocfilehash: f71aea16f7a98ff7b6427237dc90104e4ea0db71
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030929"
---
# <a name="keyboard-shortcuts-for-the-windows-powershell-ise"></a>Métodos abreviados de teclado para Windows PowerShell ISE

Use los siguientes métodos abreviados de teclado para realizar acciones en el Entorno de scripting integrado (ISE) de Windows PowerShell®. Windows PowerShell ISE está disponible como parte de los sistemas operativos Windows Server y cliente de Windows, pero también se puede instalar en algunos sistemas operativos anteriores de Windows como parte del [paquete de descarga de Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881).

## <a name="keyboard-shortcuts-for-editing-text"></a>Métodos abreviados de teclado para editar texto

Puede usar los siguientes métodos abreviados de teclado cuando edite texto.

|Acción|Métodos abreviados de teclado.|Usar en|
|----------|----------------------|----------|
|**Ayuda**|F1|Panel de scripts **Importante:** Puede especificar que la ayuda de F1 proceda de la biblioteca de TechNet en la ayuda descargada o web (Update-Help). Para realizar la selección, haga clic en **Herramientas**, **Opciones** y, a continuación, en la pestaña **Configuración General**, active o desactive **Usar Ayuda local en lugar de contenido en línea.**|
|**Copiar**|Ctrl+C|Panel de scripts, Panel de comandos y Panel de salida|
|**Cortar**|CTRL+X|Panel de scripts, Panel de comandos|
|**Expandir o contraer la esquematización**|CTRL+M|Panel de scripts|
|**Buscar en el script**|CTRL+F|Panel de scripts|
|**Buscar siguiente en el script**|F3|Panel de scripts|
|**Buscar anterior en el script**|MAYÚS+F3|Panel de scripts|
|**Buscar llave que coincida**|CTRL +]|Panel de scripts|
|**Pegar**|CTRL+V|Panel de scripts, Panel de comandos|
|**Rehacer**|CTRL+Y|Panel de scripts, Panel de comandos|
|**Reemplazar en el script**|CTRL+H|Panel de scripts|
|**Guardar**|CTRL+S|Panel de scripts|
|**Seleccionar todo**|CTRL+A|Panel de scripts, Panel de comandos y Panel de salida|
|**Mostrar fragmentos de código**|CTRL+J|Panel de scripts, Panel de comandos|
|**Deshacer**|CTRL+Z|Panel de scripts, Panel de comandos|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Métodos abreviados de teclado para ejecutar scripts

Puede usar los siguientes métodos abreviados de teclado cuando ejecute scripts en el panel de scripts.

|Acción|Método abreviado de teclado|
|----------|---------------------|
|**Nuevo**|CTRL+N|
|**Abrir**|CTRL+O|
|**Ejecutar**|F5|
|**Ejecutar selección**|F8|
|**Detener la ejecución**|CTRL+INTER. CTRL+C se puede usar cuando el contexto no es ambiguo (cuando no hay ningún texto seleccionado).|
|**Tabulación** (para el siguiente script)|CTRL+TAB **Nota:** La pestaña para el siguiente script solo funciona si tiene una sola pestaña de Windows PowerShell abierta, o bien si tiene más de una abierta pero el foco está en el panel de scripts.|
|**Tabulación** (para el script anterior)|CTRL+SHIFT+TAB **Nota:** La pestaña para el script anterior solo funciona si tiene una sola pestaña de Windows PowerShell abierta, o bien si tiene más de una abierta pero el foco está en el panel de scripts.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Métodos abreviados de teclado para personalizar la vista

Puede usar los siguientes métodos abreviados de teclado cuando personalice la vista en Windows PowerShell ISE. Son accesibles desde todos los paneles de la aplicación.

|Acción|Método abreviado de teclado|
|----------|---------------------|
|**Ir al panel de comandos (v2) o el panel de consola (v3 y versiones posteriores)**|CTRL+D|
|**Ir al panel de salida (solo v2)**|CTRL+MAYÚS+O|
|**Ir al panel de scripts**|CTRL+I|
|**Mostrar el panel de scripts**|CTRL+R|
|**Ocultar el panel de scripts**|CTRL+R|
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
> También puede usar los métodos abreviados de teclado diseñados para la consola de Windows PowerShell cuando depure scripts en Windows PowerShell ISE. Para usar estos métodos abreviados, debe escribir el método abreviado en el panel de comandos y presionar ENTRAR.

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
|**Pestaña de PowerShell anterior**|CTRL+MAYÚS+TAB Este método abreviado solo funciona si no hay archivos abiertos en ninguna pestaña de Windows PowerShell.|
|**Pestaña de Windows PowerShell siguiente**|CTRL+TAB Este método abreviado solo funciona si no hay archivos abiertos en ninguna pestaña de Windows PowerShell.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Métodos abreviados de teclado para iniciar y salir

Puede usar los siguientes métodos abreviados de teclado para iniciar la consola de Windows PowerShell (PowerShell.exe) o para salir de Windows PowerShell ISE.

|Acción|Método abreviado de teclado|
|----------|---------------------|
|**Salir**|ALT+F4|
|**Iniciar PowerShell.exe** (consola de Windows PowerShell)|CTRL+MAYÚS+P|

## <a name="see-also"></a>Véase también

- [PowerShell Magazine: The Complete List of Windows PowerShell ISE Keyboard Shortcuts](https://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/) (Lista completa de métodos abreviados de teclado de Windows PowerShell ISE)
