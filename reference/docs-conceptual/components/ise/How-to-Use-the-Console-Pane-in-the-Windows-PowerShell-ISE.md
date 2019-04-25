---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Cómo usar el panel de consola en Windows PowerShell ISE
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 5bbbdd3b1f0324ff1a4f2298459f58640c4dc9a6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057415"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Cómo usar el panel de consola en Windows PowerShell ISE

El panel de consola del Entorno de scripting integrado (ISE) de Windows PowerShell funciona exactamente igual que la ventana de consola independiente de Windows PowerShell ISE.

Para ejecutar un comando en el panel de consola, escriba un comando y, a continuación, presione ENTRAR. Para escribir varios comandos que quiera ejecutar en secuencia, escriba MAYÚS+ENTRAR entre comandos. Consulte [Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obtener ayuda sobre la escritura de los comandos.

Para detener un comando, en la barra de herramientas, haga clic en **Detener la operación**, o presione CTRL+Interrumpir. También puede usar CTRL+C para detener un comando si el contexto no es ambiguo. Por ejemplo, si se ha seleccionado texto en el panel actual, CTRL+C se asigna a la operación de copia.

A partir de Windows PowerShell v3, el panel de salida se combinó con el panel de consola. La ventaja de esta combinación es que se comporta como la consola independiente de Windows PowerShell y se eliminan las diferencias en los procedimientos que eran necesarios cuando eran independientes. Se puede hacer lo siguiente:

- Seleccionar y copiar texto del panel de consola en el Portapapeles para pegarlo en cualquier otra ventana. Para seleccionar texto, mantenga presionado el botón del ratón en el panel de salida mientras arrastra el mouse sobre el texto que quiere capturar. También puede usar las teclas de dirección mientras mantiene presionada la tecla **MAYÚS** para seleccionar texto. A continuación, presione CTRL+C o haga clic en el icono **Copiar** en la barra de herramientas.

- Pegar el texto seleccionado en la posición actual del cursor. Haga clic en el icono **Pegar** de la barra de herramientas.

- Borrar todo el texto del panel de consola. Para borrar el panel de consola, puede hacer clic en el icono **Borrar panel de consola** de la barra de herramientas, o ejecutar el comando **Clear-Host** o su alias, **cls**.

## <a name="see-also"></a>Véase también

- [Presentación de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)