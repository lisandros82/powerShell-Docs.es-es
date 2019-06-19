---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Explorar Windows PowerShell ISE
ms.openlocfilehash: 8c47e236e2e345a887fc3af281e429f440e176ff
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031033"
---
# <a name="exploring-the-windows-powershell-ise"></a>Explorar Windows PowerShell ISE

Puede usar el Entorno de scripting integrado (ISE) de Windows PowerShell® para crear, ejecutar y depurar scripts y comandos. Windows PowerShell ISE consta de la barra de menús, las pestañas de Windows PowerShell, la barra de herramientas, las pestañas de script, un panel de scripts, un panel de consola, una barra de estado, un control deslizante de tamaño de texto y la ayuda contextual.

> [!NOTE]
> A partir de Windows PowerShell ISE 3.0, los paneles de comandos y de salida se combinan en un único panel de consola.

## <a name="menu-bar"></a>Barra de menús

La barra de menús contiene los menús **Archivo**, **Edición**, **Ver**, **Herramientas**, **Depurar**, **Complementos** y **Ayuda**. Los botones de los menús permiten realizar tareas relacionadas con la escritura y ejecución de scripts y la ejecución de comandos en Windows PowerShell ISE. Además, se puede colocar una [herramienta de complemento](../../core-powershell/ise/The-ISEAddOnTool-Object.md) en la barra de menús mediante la ejecución de scripts que usan la [jerarquía del modelo de objetos de ISE](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

> [!NOTE]
> En Windows PowerShell ISE 2.0, no existían los menús **Herramientas** y **Complementos**.

## <a name="windows-powershell-tabs"></a>Pestañas de Windows PowerShell

Una pestaña de Windows PowerShell es el entorno en el que se ejecuta un script de Windows PowerShell. Puede abrir nuevas pestañas de Windows PowerShell en Windows PowerShell ISE para crear entornos independientes en el equipo local o en equipos remotos. Puede tener un máximo de ocho pestañas de PowerShell abiertas de forma simultánea.

## <a name="toolbar"></a>Barra de herramientas

Los botones siguientes están ubicados en la barra de herramientas.

|Botón|Función|
|----------|------------|
|**Nuevo**|Abre un nuevo script.|
|**Abrir**|Abre un script o un archivo existente.|
|**Guardar**|Guarda un script o un archivo.|
|**Cortar**|Corta el texto seleccionado y lo copia en el Portapapeles.|
|**Copiar**|Copia el texto seleccionado en el portapapeles.|
|**Pegar**|Pega el contenido del Portapapeles en la ubicación del cursor.|
|**Borrar panel de salida**|Borra todo el contenido del panel de salida.|
|**Deshacer**|Invierte la acción que se acaba de realizar.|
|**Rehacer**|Realiza la acción que se acaba de deshacer.|
|**Ejecutar script**|Ejecuta un script.|
|**Ejecutar selección**|Ejecuta una parte seleccionada de un script.|
|**Detener la ejecución**|Detiene un script que se está ejecutando.|
|**Nueva pestaña de PowerShell en remoto**|Crea una nueva pestaña de PowerShell que establece una sesión en un equipo remoto. Aparece un cuadro de diálogo que le pide que escriba los detalles necesarios para establecer la conexión remota.|
|**Iniciar PowerShell.exe**|Abre una consola de PowerShell.|
|**Mostrar panel de scripts arriba**|Mueve el panel de scripts a la parte superior de la pantalla.|
|**Mover panel de scripts a la derecha**|Mueve el panel de scripts a la derecha de la pantalla.|
|**Mostrar panel de scripts maximizado**|Maximiza el panel de scripts.|

## <a name="script-tab"></a>Pestaña Script

Muestra el nombre del script que se está editando. Puede hacer clic en una pestaña de script para seleccionar el script que desea editar.

Cuando apunte a la pestaña de script, la ruta de acceso completa al archivo de script se mostrará en una información sobre herramientas.

## <a name="script-pane"></a>Panel de scripts

Permite crear y ejecutar scripts. Puede abrir, editar y ejecutar scripts existentes en el panel de scripts.

## <a name="output-pane"></a>Panel de salida

Muestra los resultados de los comandos y scripts que ha ejecutado. También puede copiar y borrar el contenido en el panel de salida.

## <a name="command-pane"></a>Panel de comandos

Permite escribir comandos. Puede ejecutar un comando de una línea o un comando de varias líneas en el panel de comandos. Presione MAYÚS+ENTRAR para introducir cada línea de un comando de varias líneas y presione ENTRAR después de la última línea para ejecutarlo. El mensaje que aparece en la parte superior del panel de comandos muestra la ruta de acceso al directorio de trabajo actual.

## <a name="status-bar"></a>Barra de estado

Permite ver si los comandos y scripts que ejecuta se han completado. La barra de estado se encuentra en la parte inferior de la pantalla. Las partes seleccionadas de los mensajes de error se muestran en la barra de estado.

## <a name="text-size-slider"></a>Control deslizante Tamaño del texto

Aumenta o disminuye el tamaño del texto en la pantalla.

## <a name="help"></a>Ayuda

La ayuda de Windows PowerShell ISE está disponible en la biblioteca de TechNet en Internet. Para abrir la Ayuda, haga clic en **Ayuda de Windows PowerShell ISE** en el menú **Ayuda** o presione la tecla F1 en cualquier lugar excepto cuando el cursor esté en el nombre de un cmdlet en el panel de scripts o en panel de consola. Desde el menú **Ayuda** también puede ejecutar el cmdlet Update-Help y mostrar la ventana Comandos, que le muestra todos los parámetros de un cmdlet para ayudarle a construir comandos, lo que permite rellenar los parámetros en un formulario fácil de usar.

## <a name="see-also"></a>Véase también

- [Presentación de Windows PowerShell ISE](../../core-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md)
