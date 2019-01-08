---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Introducción a Windows PowerShell ISE
ms.openlocfilehash: 09a28b295855fd2a3c62bba8a681399dae3454f8
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411589"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) es una aplicación host de Windows PowerShell. En el ISE, puede ejecutar comandos y escribir, comprobar y depurar scripts en una interfaz gráfica de usuario único basado en Windows. El ISE proporciona edición de varias líneas, finalización con tabulación, colores de sintaxis, ejecución selectiva, ayuda contextual y compatibilidad para idiomas de derecha a izquierda. Los elementos de menú y métodos abreviados de teclado se asignan a muchas de las mismas tareas que realizaría en la consola de Windows PowerShell. Por ejemplo, cuando se depura un script en el ISE, haga en una línea de código en el panel de edición para establecer un punto de interrupción.

## <a name="support"></a>Soporte técnico

El ISE se introdujo por primera vez con Windows PowerShell V2 y rediseñado con PowerShell V3. El ISE se admite en todas las versiones compatibles de Windows PowerShell hasta y V5.1 incluido Windows PowerShell. El ISE, sin embargo, está en modo de maintennce y ninguna característica nueva es probable que va a agregar.
Además, no hay ninguna compatibilidad con el ISE con motor v6 de PowerShell y más allá. Deben tener en cuenta los usuarios que desean una herramienta gráfica que permite administrar los scrips de PowerShell, etcetera, [Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Principales características

Las características clave en Windows PowerShell ISE se incluyen:

- Edición de varias líneas: para insertar una línea en blanco debajo de la línea actual en el panel de comandos, presione MAYÚS+ENTRAR.
- Ejecución selectiva: para ejecutar parte de un script, seleccione el texto que quiera ejecutar y, a continuación, haga clic en el botón **Ejecutar script**. También puede presionar F5.
- Ayuda contextual: escriba **Invoke-Item** y presione F1. El archivo de ayuda se abre en el artículo correspondiente al cmdlet **Invoke-Item**.

Windows PowerShell ISE permite personalizar algunos aspectos de su apariencia. También tiene su propio script de perfil de Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Para iniciar Windows PowerShell ISE

Haga clic en **Inicio**, seleccione **Windows PowerShell** y, después, haga clic en **Windows PowerShell ISE**.
Como alternativa, puede escribir `powershell_ise.exe` en cualquier shell de comandos o en el cuadro Ejecutar.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Para obtener ayuda de Windows PowerShell ISE

En el menú **Ayuda**, haga clic en **Ayuda de Windows PowerShell**. También puede presionar F1. El archivo que se abre contiene información detallada sobre Windows PowerShell ISE y Windows PowerShell, además de toda la ayuda disponible en el cmdlet Get-Help.
