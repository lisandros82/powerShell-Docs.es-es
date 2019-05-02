---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Introducción a Windows PowerShell ISE
ms.openlocfilehash: 729c8535dbcfcd2c51070b8beac5d328375f36ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057431"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) es una aplicación host de Windows PowerShell. En el ISE, puede ejecutar comandos y escribir, probar y depurar scripts en una única interfaz gráfica de usuario basada en Windows. El ISE proporciona edición de varias líneas, finalización con tabulación, color de sintaxis, ejecución selectiva, ayuda contextual y compatibilidad con idiomas de derecha a izquierda. Los elementos de menú y métodos abreviados de teclado se asignan a muchas de las mismas tareas que realizaría en la consola de Windows PowerShell. Por ejemplo, al depurar un script en el ISE, puede hacer clic con el botón derecho en una línea de código del panel de edición para establecer un punto de interrupción.

## <a name="support"></a>Soporte técnico

El ISE se introdujo por primera vez con Windows PowerShell V2 y se rediseñó con PowerShell V3. El ISE se admite en todas las versiones compatibles de Windows PowerShell hasta Windows PowerShell V5.1 (inclusive). El ISE, sin embargo, está en modo de mantenimiento y no es probable que se le agreguen características nuevas.
Además, no hay ninguna compatibilidad para el ISE a partir de PowerShell v6. Los usuarios que deseen una herramienta gráfica con la que administrar los scripts de PowerShell, etc., deben considerar la opción de [Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Principales características

Entre las principales características de Windows PowerShell ISE están las siguientes:

- Edición de varias líneas: para insertar una línea en blanco debajo de la línea actual en el panel de comandos, presione MAYÚS+ENTRAR.
- Ejecución selectiva: para ejecutar parte de un script, seleccione el texto que quiera ejecutar y, a continuación, haga clic en el botón **Ejecutar script**. También puede presionar F5.
- Ayuda contextual: escriba **Invoke-Item** y presione F1. El archivo de ayuda se abre en el artículo correspondiente al cmdlet **Invoke-Item**.

Windows PowerShell ISE permite personalizar algunos aspectos de su apariencia. También tiene su propio script de perfil de Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Para iniciar Windows PowerShell ISE

Haga clic en **Inicio**, seleccione **Windows PowerShell** y, después, haga clic en **Windows PowerShell ISE**.
Como alternativa, puede escribir `powershell_ise.exe` en cualquier shell de comandos o en el cuadro Ejecutar.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Para obtener ayuda de Windows PowerShell ISE

En el menú **Ayuda**, haga clic en **Ayuda de Windows PowerShell**. También puede presionar F1. El archivo que se abre contiene información detallada sobre Windows PowerShell ISE y Windows PowerShell, además de toda la ayuda disponible en el cmdlet Get-Help.
