---
title: "Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: 803470be4a680d47ccec8b5b19bc873626aec15e
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola
La finalización con tabulación proporciona ayuda automática al escribir en el panel de scripts o el panel de comandos. Para aprovechar esta característica, siga estos pasos:

## <a name="to-automatically-complete-a-command-entry"></a>Para completar automáticamente una entrada de comando
En el panel de comandos o el panel de scripts, escriba algunos caracteres de un comando y, después, presione la tecla TAB para seleccionar el texto de finalización deseado. Si varios elementos empiezan por el texto que ha escrito inicialmente, siga presionando la tecla Tab hasta que aparezca el elemento deseado. La finalización con tabulación puede ayudarle a escribir un nombre de cmdlet, de parámetro, de variable o de propiedad de objeto, o bien una ruta de acceso de archivo.

> [!NOTE]
> En el panel de scripts, al presionar TAB, se completa automáticamente un comando solo cuando se editan archivos .ps1, .psd1 o .psm1. La finalización con tabulación funciona siempre al escribir en el panel de comandos.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Para completar automáticamente la entrada de un parámetro de cmdlet
En el panel de comandos o el panel de scripts, escriba un cmdlet seguido por un guion y, después, presione la tecla TAB.

Por ejemplo, escriba `Get-Process -` y, a continuación, presione TAB varias veces para mostrar cada uno de los parámetros del cmdlet de uno en uno.

## <a name="see-also"></a>Véase también
- [Utilizar Windows PowerShell ISE](using-the-windows-powershell-ise.md)
- [Cómo crear una pestaña de PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)

