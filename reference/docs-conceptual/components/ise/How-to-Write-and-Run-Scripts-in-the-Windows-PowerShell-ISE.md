---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Cómo escribir y ejecutar scripts en Windows PowerShell ISE
ms.openlocfilehash: 4a08d7d206d103dcb398964d7ce75bea1e76559a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028976"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Cómo escribir y ejecutar scripts en Windows PowerShell ISE

En este artículo se describe cómo crear, editar, ejecutar y guardar scripts en el panel de scripts.

## <a name="how-to-create-and-run-scripts"></a>Cómo crear y ejecutar scripts

Puede abrir y editar archivos de Windows PowerShell en el panel de scripts. Los tipos de archivo de interés específicos de Windows PowerShell son los archivos de script (.ps1), los archivos de datos de script (.psd1) y los archivos de módulo de script (.psm1). Estos tipos de archivo presentan color de sintaxis en el editor de panel de scripts. Otros tipos de archivo comunes que puede abrir en el panel de scripts son los archivos de configuración (.ps1xml), los archivos XML y los archivos de texto.

> [!NOTE]
> La directiva de ejecución de Windows PowerShell determina si puede ejecutar scripts y cargar archivos de configuración y perfiles de Windows PowerShell. La directiva de ejecución predeterminada, Restricted, impide que se ejecuten todos los scripts y que se carguen perfiles. Para cambiar la directiva de ejecución a fin de permitir cargar y usar perfiles, consulte [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) y [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).

### <a name="to-create-a-new-script-file"></a>Para crear un nuevo archivo de script

En la barra de herramientas, haga clic en **Nuevo**, o bien, en el menú **Archivo**, haga clic en **Nuevo**. El archivo creado aparece en una nueva pestaña de archivo en la ficha actual de PowerShell. Recuerde que las pestañas de PowerShell solo están visibles cuando hay más de una. De forma predeterminada, se crea un archivo de tipo script (.ps1), pero se puede guardar con un nombre y una extensión diferentes. Se pueden crear varios archivos de script en la misma pestaña de PowerShell.

### <a name="to-open-an-existing-script"></a>Para abrir un script existente

En la barra de herramientas, haga clic en **Abrir**, o bien, en el menú **Archivo**, haga clic en **Abrir**. En el cuadro de diálogo **Abrir**, seleccione el archivo que quiera abrir. El archivo abierto aparece en una nueva pestaña.

### <a name="to-close-a-script-tab"></a>Para cerrar una pestaña de script

Haga clic en el icono **Cerrar** (X) de la pestaña del archivo que desea cerrar o bien seleccione el menú **Archivo** y haga clic en **Cerrar**.

Si el archivo se ha modificado desde que se guardó por última vez, se le preguntará si desea guardar o descartar los cambios.

### <a name="to-display-the-file-path"></a>Para mostrar la ruta de acceso del archivo

En la pestaña del archivo, señale el nombre de archivo. La ruta de acceso completa al archivo de script se muestra en una información sobre herramientas.

### <a name="to-run-a-script"></a>Para ejecutar un script

En la barra de herramientas, haga clic en **Ejecutar script**, o bien, en el menú **Archivo**, haga clic en **Ejecutar**.

### <a name="to-run-a-portion-of-a-script"></a>Para ejecutar parte de un script

1. En el panel de scripts, seleccione una parte de un script.
2. En el menú **Archivo**, haga clic en **Ejecutar selección**, o bien haga clic en **Ejecutar selección** en la barra de herramientas.

### <a name="to-stop-a-running-script"></a>Para detener un script que se está ejecutando

Hay varias maneras para detener un script en ejecución.

- Haga clic en **Detener operación** en la barra de herramientas
- Presione CTRL + INTER.
- Seleccione el menú **Archivo** y haga clic en **Detener operación**.

Presionar **CTRL+C** también funciona a menos que ya haya texto seleccionado, en cuyo caso **CTRL+C** se asigna a la función de copia del texto seleccionado.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Cómo escribir y editar texto en el panel de scripts

Puede copiar, cortar, pegar, buscar y reemplazar texto en el panel de scripts. También puede deshacer y rehacer la última acción que ha realizado. Los métodos abreviados de teclado para estas acciones son los mismos que los usados para todas las aplicaciones de Windows.

### <a name="to-enter-text-in-the-script-pane"></a>Para escribir texto en el panel de scripts

1. Mueva el cursor al panel de scripts haciendo clic en cualquier lugar del panel de scripts o en **Ir al panel de scripts** en el menú **Ver**.
2. Cree un script. El color de sintaxis y la finalización con tabulación proporcionan una experiencia de edición más rica en Windows PowerShell ISE.
3. Vea [Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obtener más información sobre el uso de la característica de finalización de con tabulación para facilitar la escritura.

### <a name="to-find-text-in-the-script-pane"></a>Para buscar texto en el panel de scripts

1. Para buscar texto en cualquier lugar, presione **CTRL+F** o, en el menú **Edición**, haga clic en **Buscar en el script**.
2. Para buscar texto después del cursor, presione **F3** o, en el menú **Edición**, haga clic en **Buscar siguiente en el script**.
3. Para buscar texto antes del cursor, presione **MAYÚS+F3** o, en el menú **Edición**, haga clic en **Buscar anterior en el script**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Para buscar y reemplazar texto en el panel de scripts

Presione **CRTL+H** o, en el menú **Edición**, haga clic en **Replace in Script** (Reemplazar en script). Escriba el texto que desea encontrar y el texto de reemplazo y, después, presione **ENTRAR**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Para ir a una línea determinada de texto en el panel de scripts

1. En el panel de scripts, presione **CTRL+G** o, en el menú **Edición**, haga clic en **Ir a la línea**.

2. Escriba un número de línea.

### <a name="to-copy-text-in-the-script-pane"></a>Para copiar texto en el panel de scripts

1. En el panel de scripts, seleccione el texto que desee copiar.

2. Presione **CTRL+C** o haga clic en el icono **Copiar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Copiar**.

### <a name="to-cut-text-in-the-script-pane"></a>Para cortar texto en el panel de scripts

1. En el panel de scripts, seleccione el texto que desee cortar.
2. Presione **CTRL+X** o haga clic en el icono **Cortar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Cortar**.

### <a name="to-paste-text-into-the-script-pane"></a>Para pegar texto en el panel de scripts

Presione **CTRL+V** o haga clic en el icono **Pegar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Pegar**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Para deshacer una acción en el panel de scripts

Presione **CTRL+Z** o haga clic en el icono **Deshacer** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Deshacer**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Para rehacer una acción en el panel de scripts

Presione **CTRL+Y** o haga clic en el icono **Rehacer** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Rehacer**.

## <a name="how-to-save-a-script"></a>Cómo guardar un script

Aparece un asterisco junto al nombre del script para marcar un archivo que no se ha guardado desde que se modificó. El asterisco desaparecerá cuando se guarda el archivo.

### <a name="to-save-a-script"></a>Para guardar un script

Presione **CTRL+S** o haga clic en el icono **Guardar** de la barra de herramientas. O bien, en el menú **Archivo**, haga clic en **Guardar**.

### <a name="to-save-and-name-a-script"></a>Para guardar un script y asignarle un nombre

1. En el menú **Archivo**, haga clic en **Guardar como**. Se abre el cuadro de diálogo **Guardar como**.
2. En el cuadro **Nombre de archivo**, escriba un nombre para el archivo.
3. En el cuadro **Guardar como tipo**, seleccione un tipo de archivo. Por ejemplo, en el cuadro **Guardar como tipo**, seleccione “Scripts de PowerShell (\*.ps1)”.
4. Haga clic en **Guardar**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Para guardar un script en la codificación ASCII

De forma predeterminada, Windows PowerShell ISE guarda los nuevos archivos de script (.ps1), los archivos de datos de script (.psd1) y los archivos de módulo de script (.psm1) como Unicode (BigEndianUnicode). Para guardar un script en otra codificación, como ASCII (ANSI), use los métodos **Save** o **SaveAs** en el objeto [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md).

El siguiente comando guarda un nuevo script como MyScript.ps1 con la codificación ASCII.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

El siguiente comando reemplaza el archivo de script actual con un archivo con el mismo nombre, pero con la codificación ASCII.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

El comando siguiente obtiene la codificación del archivo actual.

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE admite las siguientes opciones de codificación: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 y Default. El valor de la opción predeterminada varía según el sistema.

Windows PowerShell ISE no cambia la codificación de los archivos de script cuando se usan los comandos Guardar o Guardar como.

## <a name="see-also"></a>Véase también

- [Explorar Windows PowerShell ISE](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
