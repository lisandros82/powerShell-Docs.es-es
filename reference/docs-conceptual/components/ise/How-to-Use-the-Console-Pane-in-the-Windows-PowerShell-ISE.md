---
ms.date: 01/02/2020
keywords: powershell, cmdlet
title: Cómo usar el panel de consola en Windows PowerShell ISE
ms.openlocfilehash: f0ef07e410ed494f5732eab360c4e050c9c09a7f
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736154"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Cómo usar el panel de consola en Windows PowerShell ISE

El panel de consola del Entorno de scripting integrado (ISE) de Windows PowerShell funciona exactamente igual que la ventana de consola independiente de Windows PowerShell ISE.

Para ejecutar un comando en el panel de consola, escriba un comando y, a continuación, presione <kbd>ENTRAR</kbd>. Para escribir varios comandos que quiera ejecutar en secuencia, escriba <kbd>MAYÚS</kbd>+<kbd>ENTRAR</kbd> entre comandos. Consulte [Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obtener ayuda sobre la escritura de los comandos.

Para detener un comando, en la barra de herramientas, haga clic en **Detener la operación** o presione <kbd>CTRL</kbd>+<kbd>Interrumpir</kbd>. También puede usar <kbd>CTRL</kbd>+<kbd>C</kbd> para detener un comando si el contexto no es ambiguo. Por ejemplo, si se ha seleccionado texto en el panel actual, <kbd>CTRL</kbd>+<kbd>C</kbd> se asigna a la operación de copia.

A partir de Windows PowerShell v3, el panel de salida se combinó con el panel de consola. La ventaja de esta combinación es que se comporta como la consola independiente de Windows PowerShell y se eliminan las diferencias en los procedimientos que eran necesarios cuando eran independientes. Puede:

- Seleccionar y copiar texto del panel de consola en el Portapapeles para pegarlo en cualquier otra ventana. Para seleccionar texto, mantenga presionado el botón del ratón en el panel de salida mientras arrastra el mouse sobre el texto que quiere capturar. También puede usar las teclas de dirección mientras mantiene presionada la tecla <kbd>MAYÚS</kbd> para seleccionar texto. Después, pulse <kbd>CTRL</kbd>+<kbd>C</kbd> o haga clic en el icono **Copiar** de la barra de herramientas.

- Pegar el texto seleccionado en la posición actual del cursor. Haga clic en el icono **Pegar** de la barra de herramientas.

- Borrar todo el texto del panel de consola. Para borrar el panel de consola, puede hacer clic en el icono **Borrar panel de consola** de la barra de herramientas, o bien ejecutar el comando `Clear-Host` o su alias, `cls`.

## <a name="see-also"></a>Consulte también

- [Presentación de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
