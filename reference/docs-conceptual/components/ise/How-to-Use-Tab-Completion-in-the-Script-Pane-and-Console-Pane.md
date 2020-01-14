---
ms.date: 01/02/2020
keywords: powershell, cmdlet
title: Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola
ms.openlocfilehash: 07cf9ff75db8d33ed018542153bfcd7503035e40
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737090"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola

La finalización con tabulación proporciona ayuda automática al escribir en el panel de scripts o el panel de comandos. Para aprovechar esta característica, siga estos pasos:

## <a name="to-automatically-complete-a-command-entry"></a>Para completar automáticamente una entrada de comando

En el panel de comandos o el panel de scripts, escriba algunos caracteres de un comando y, después, presione la tecla <kbd>TAB</kbd> para seleccionar el texto de finalización deseado. Si varios elementos empiezan por el texto que ha escrito inicialmente, siga presionando la tecla <kbd>TAB</kbd> hasta que aparezca el elemento deseado. La finalización con tabulación puede ayudarle a escribir un nombre de cmdlet, de parámetro, de variable o de propiedad de objeto, o bien una ruta de acceso de archivo.

> [!NOTE]
> En el panel de scripts, al presionar <kbd>TAB</kbd>, se completa automáticamente un comando solo cuando se editan archivos `.ps1`, `.psd1` o `.psm1`. La finalización con tabulación funciona siempre al escribir en el panel de comandos.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Para completar automáticamente la entrada de un parámetro de cmdlet

En el panel de comandos o el panel de scripts, escriba un cmdlet seguido por un guion y, después, presione la tecla <kbd>TAB</kbd>.

Por ejemplo, escriba `Get-Process -` y, a continuación, presione <kbd>TAB</kbd> varias veces para mostrar cada uno de los parámetros del cmdlet de uno en uno.

## <a name="see-also"></a>Consulte también

- [Presentación de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Cómo crear una pestaña de PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
