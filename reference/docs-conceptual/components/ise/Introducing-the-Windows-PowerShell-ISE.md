---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Introducción a Windows PowerShell ISE
ms.openlocfilehash: 3e4471d0982ba4d7ef1a9d59906a9ff297f6f7cb
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736205"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) es una aplicación host de Windows PowerShell. En el ISE, puede ejecutar comandos y escribir, probar y depurar scripts en una única interfaz gráfica de usuario basada en Windows. El ISE proporciona edición de varias líneas, finalización con tabulación, color de sintaxis, ejecución selectiva, ayuda contextual y compatibilidad con idiomas de derecha a izquierda. Los elementos de menú y métodos abreviados de teclado se asignan a muchas de las mismas tareas que realizaría en la consola de Windows PowerShell. Por ejemplo, al depurar un script en el ISE, puede hacer clic con el botón derecho en una línea de código del panel de edición para establecer un punto de interrupción.

## <a name="support"></a>Soporte técnico

El ISE se introdujo por primera vez con Windows PowerShell V2 y se rediseñó con PowerShell V3. El ISE se admite en todas las versiones compatibles de Windows PowerShell hasta Windows PowerShell V5.1 (inclusive).

> [!NOTE]
> PowerShell ISE ya no se incluye en el desarrollo activo de características. Como componente que se envía con Windows, sigue siendo compatible oficialmente con las correcciones de servicios de seguridad y alta prioridad.
> Aunque actualmente no está previsto quitar el ISE de Windows,
>
> no existe ninguna compatibilidad con él a partir de PowerShell v6. Los usuarios que quieran reemplazar el ISE deben usar [Visual Studio Code](https://code.visualstudio.com/) con la [extensión de PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).

## <a name="key-features"></a>Principales características

Entre las principales características de Windows PowerShell ISE están las siguientes:

- Edición de varias líneas: para insertar una línea en blanco debajo de la línea actual en el panel de comandos, presione <kbd>MAYÚS</kbd>+<kbd>ENTRAR</kbd>.
- Ejecución selectiva: para ejecutar parte de un script, seleccione el texto que quiera ejecutar y, a continuación, haga clic en el botón **Ejecutar script**. También puede presionar <kbd>F5</kbd>.
- Ayuda contextual: escriba `Invoke-Item` y, luego, presione <kbd>F1</kbd>. El archivo de ayuda se abre en el artículo correspondiente al cmdlet `Invoke-Item`.

Windows PowerShell ISE permite personalizar algunos aspectos de su apariencia. También tiene su propio script de perfil de Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Para iniciar Windows PowerShell ISE

Haga clic en **Inicio**, seleccione **Windows PowerShell** y, después, haga clic en **Windows PowerShell ISE**.
Como alternativa, puede escribir `powershell_ise.exe` en cualquier shell de comandos o en el cuadro Ejecutar.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Para obtener ayuda de Windows PowerShell ISE

En el menú **Ayuda**, haga clic en **Ayuda de Windows PowerShell**. También puede presionar <kbd>F1</kbd>. El archivo que se abre contiene información detallada sobre Windows PowerShell ISE y Windows PowerShell, además de toda la ayuda disponible con el cmdlet `Get-Help`.
