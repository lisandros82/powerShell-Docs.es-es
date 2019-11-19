---
title: Uso de Visual Studio Code para el desarrollo de PowerShell
description: Uso de Visual Studio Code para el desarrollo de PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: b083388174dbae4a50da73156d2fce41412613a7
ms.sourcegitcommit: 14b50e5446f69729f72231f5dc6f536cdd1084c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73933882"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Uso de Visual Studio Code para el desarrollo de PowerShell

Además de [PowerShell ISE][ise], PowerShell también se admite en Visual Studio Code (VSCode). El ISE no es compatible con PowerShell Core, pero VSCode es compatible con PowerShell Core en todas las plataformas: Windows, macOS y Linux.

Puede usar VSCode en Windows con la versión 5 de PowerShell mediante Windows 10 o la instalación de Windows Management Framework 5.1 para sistemas operativos Windows de nivel inferior, como Windows 8.1. Para más información, consulte [Instalación y configuración de WMF 5.1](/powershell/scripting/wmf/setup/install-configure).

Antes de empezar, asegúrese de que PowerShell existe en el sistema. Para cargas de trabajo modernas de Windows, macOS y Linux, consulte los siguientes vínculos:

- [Instalación de PowerShell Core en Linux][install-pscore-linux]
- [Instalación de PowerShell Core en macOS][install-pscore-macos]
- [Instalación de PowerShell Core en Windows][install-pscore-windows]

Para las cargas de trabajo de Windows PowerShell tradicionales, vea [Instalación de Windows PowerShell][install-winps].

## <a name="editing-with-vscode"></a>Edición con VSCode

1. Instale VSCode. Para más información, consulte la información general que se describe en [Configuración de Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).

   Hay instrucciones de instalación para cada plataforma:

   - **Linux**: siga las instrucciones de instalación de la página [Ejecución de VSCode en Linux](https://code.visualstudio.com/docs/setup/linux).
   - **macOS**: siga las instrucciones de instalación de la página [Ejecución de VSCode en macOS](https://code.visualstudio.com/docs/setup/mac).

     > [!IMPORTANT]
     > En macOS, debe instalar OpenSSL para que la extensión de PowerShell funcione correctamente. La manera más fácil de hacerlo consiste en instalar [Homebrew](https://brew.sh/) y ejecutar `brew install openssl`. Ahora VSCode puede cargar la extensión de PowerShell correctamente.

   - **Windows**: siga las instrucciones de instalación de la página [Ejecución de VSCode en Windows](https://code.visualstudio.com/docs/setup/windows).

1. Instale la extensión de PowerShell.

   1. Inicie la aplicación VSCode de la siguiente manera:
      - **Windows**: escriba `code` en la sesión de PowerShell.
      - **Linux**: escriba `code` en el terminal.
      - **macOS**: escriba `code` en el terminal.
   1. Inicie **Quick Open** en Windows o Linux; para ello, presione <kbd>Ctrl</kbd>+<kbd>P</kbd>. En macOS, presione <kbd>Cmd</kbd>+<kbd>P</kbd>.
   1. En Quick Open, escriba `ext install powershell` y presione **Entrar**.
   1. Se abre la vista **Extensiones** en la barra lateral. Seleccione la extensión de PowerShell de Microsoft.
      Verá una pantalla de VSCode similar a la siguiente imagen:

      ![VSCode](../../images/using-vscode/vscode.png)

   1. Haga clic en el botón **Instalar** en la extensión de PowerShell de Microsoft.
   1. Después de la instalación, se ve que el botón **Instalar** cambia a **Recargar**. Haga clic en **Recargar**.
   1. Una vez que se haya vuelto a cargar VSCode, estará listo para la edición.

Por ejemplo, para crear un archivo, haga clic en **Archivo -> Nuevo**. Para guardarlo, haga clic en **Archivo -> Guardar** y proporcione un nombre de archivo, por ejemplo, `HelloWorld.ps1`. Para cerrar el archivo, haga clic en la `X` junto al nombre de archivo. Para salir de VSCode, **Archivo->Salir**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Instalación de la extensión de PowerShell en sistemas restringidos

Algunos sistemas están configurados de tal manera que se requiere la comprobación de todas las firmas de código y la aprobación manual de los servicios del editor de PowerShell para ejecutarse en el sistema. Una de las causas probables de que haya instalado la extensión de PowerShell pero reciba un error como el siguiente es la actualización de una directiva de grupo que cambia la directiva de ejecución:

```
Language server startup failed.
```

Para aprobar manualmente los servicios del editor de PowerShell y la extensión de PowerShell para VSCode, abra un símbolo del sistema y ejecute el siguiente comando:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Se le preguntará si desea ejecutar software de este editor que no es de confianza. Escriba `A` para ejecutar el archivo. A continuación, abra VSCode y compruebe que la extensión de PowerShell funciona correctamente. Si sigue teniendo problemas para comenzar, háganoslo saber en [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Elección de una versión de PowerShell para usarla con la extensión

Con la instalación de PowerShell Core en paralelo con Windows PowerShell, ahora es posible usar una versión determinada de PowerShell con la extensión de PowerShell. Use estos pasos para elegir la versión:

1. Abra la **paleta de comandos** en Windows o Linux con <kbd>Ctrl</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd>. En macOS, use <kbd>Cmd</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd>.
1. Busque **Sesión**.
1. Haga clic en **PowerShell: Show Session Menu** (PowerShell: Mostrar menú de sesión).
1. En la lista, elija la versión de PowerShell que quiere usar, por ejemplo: **PowerShell Core**.

> [!IMPORTANT]
> Esta característica examina algunas rutas de acceso conocidas en distintos sistemas operativos para detectar las ubicaciones de instalación de PowerShell. O PowerShell pode não ser inicialmente mostrado no menu de sessão caso você o tenha instalado em um local atípico. Para extender el menú de la sesión, [agregue sus propias rutas de acceso personalizadas](#adding-your-own-powershell-paths-to-the-session-menu) tal como se describe a continuación.

>[!NOTE]
> Hay otra forma de acceder al menú de la sesión. Cuando se abre un archivo de PowerShell en el editor, verá un número de versión verde en la esquina inferior derecha. Haga clic en este número de versión para acceder al menú de la sesión.

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Adición de rutas de acceso propias de PowerShell al menú de sesión

Puede agregar otras rutas de acceso ejecutables de PowerShell al menú de sesión mediante una configuración de VSCode.

Agregue un elemento a la lista `powershell.powerShellAdditionalExePaths` o cree la lista si no existe en su `settings.json`:

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

Cada elemento debe tener:

* `exePath`: la ruta de acceso al ejecutable `pwsh` o `powershell`.
* `versionName`: el texto que se mostrará en el menú de la sesión.

Puede establecer la versión de PowerShell predeterminada para usar el valor `powershell.powerShellDefaultVersion`; para ello, configúrela con el texto que se muestra en el menú de sesión (también conocido como `versionName` en el último valor).

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

Después de configurar este valor, reinicie VSCode o vuelva a cargar la ventana actual de VSCode desde la **paleta de comandos** y escriba **Desarrollador: Recargar ventana**.

Si abre el menú de la sesión, ahora verá las versiones adicionales de PowerShell.

> [!NOTE]
> Si compila PowerShell a partir del código fuente, se trata de una excelente forma de probar la compilación local de PowerShell.

### <a name="configuration-settings-for-vscode"></a>Valores de configuración de VSCode

Mediante los pasos del párrafo anterior, puede agregar valores de configuración en `settings.json`.

Recomendamos los valores de configuración siguientes para VSCode:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Si no desea que estos ajustes afecten a todos los tipos de archivos, VSCode también permite configuraciones por idioma. Cree un ajuste específico del lenguaje colocando los ajustes en un campo `[<language-name>]`. Por ejemplo:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Para obtener más información sobre la codificación de archivo en VSCode, vea [Descripción de la codificación de archivo](understanding-file-encoding.md).

## <a name="debugging-with-vscode"></a>Depuración con VSCode

### <a name="no-workspace-debugging"></a>Depuración fuera del área de trabajo

A partir de VSCode versión 1.9 puede depurar scripts de PowerShell sin tener que abrir la carpeta que los contiene. Abra el archivo de script de PowerShell con **Archivo -> Abrir archivo…** , establezca un punto de interrupción en una línea, presione <kbd>F9</kbd> y, después, presione <kbd>F5</kbd> para iniciar la depuración. Verá que aparece el panel de acciones de depuración, que le permite iniciar el depurador, realizar la depuración paso a paso, reanudarla y detenerla.

### <a name="workspace-debugging"></a>Depuración del área de trabajo

La depuración del área de trabajo hace referencia a la depuración en el contexto de una carpeta que se ha abierto en Visual Studio Code desde el menú **Archivo** mediante **Abrir carpeta...** . Suele tratarse de la carpeta del proyecto de PowerShell o la raíz del repositorio de Git.

Incluso en este modo, para empezar a depurar el script de PowerShell seleccionado, presione <kbd>F5</kbd>. La depuración del área de trabajo no se limita a depurar el archivo abierto actualmente, sino que permite definir diversas configuraciones de depuración. Por ejemplo, puede agregar configuraciones para:

- Iniciar pruebas de Pester en el depurador
- Iniciar un archivo específico con argumentos en el depurador
- Iniciar una sesión interactiva en el depurador
- Asociar el depurador a un proceso de host de PowerShell.

Siga los pasos siguientes para crear el archivo de configuración de depuración:

  1. Abra la vista **Depurar** en Windows o Linux con <kbd>Ctrl</kbd>+<kbd>Mayús</kbd>+<kbd>D</kbd>. En macOS, presione <kbd>Cmd</kbd>+<kbd>Mayús</kbd>+<kbd>D</kbd>.
  1. Haga clic en el icono de engranaje **Configurar** en la barra de herramientas.
  1. VSCode le solicita que **seleccione un entorno**. Elija **PowerShell**.

El resultado es que VSCode crea un directorio y un archivo `.vscode\launch.json` en la raíz de la carpeta del área de trabajo. En esta ubicación es donde se almacena la configuración de depuración. Si los archivos están en un repositorio de Git, lo normal es que le interese confirmar el archivo `launch.json`. El contenido del archivo `launch.json` es el siguiente:

```json
{
  "version": "0.2.0",
  "configurations": [
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Launch (current file)",
          "script": "${file}",
          "args": [],
          "cwd": "${file}"
      },
      {
          "type": "PowerShell",
          "request": "attach",
          "name": "PowerShell Attach to Host Process",
          "processId": "${command.PickPSHostProcess}",
          "runspaceId": 1
      },
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Interactive Session",
          "cwd": "${workspaceRoot}"
      }
  ]
}
```

Este archivo representa los escenarios de depuración comunes. Cuando abra este archivo en el editor, verá un botón **Agregar configuración…** . Puede hacer clic en este botón para agregar más configuraciones de depuración de PowerShell. Una configuración muy útil que conviene agregar es **PowerShell: Iniciar Script**. Con esta configuración, puede especificar un archivo con argumentos opcionales que se iniciará cada vez que se presione <kbd>F5</kbd>, con independencia del archivo que esté activo en el momento en el editor.

Una vez establecida la configuración de depuración, puede seleccionar qué configuración quiere usar durante una sesión de depuración. Seleccione una configuración de la lista desplegable de configuraciones de depuración en la barra de herramientas de la vista **Depurar**.

Algunos blogs pueden servirle de ayuda para empezar a usar la extensión de PowerShell para Visual Studio Code:

- [Extensión de PowerShell][ps-extension]
- [Escritura y depuración de scripts de PowerShell en Visual Studio Code][debug]
- [Instrucciones de depuración de Visual Studio Code][vscode-guide]
- [Depuración de PowerShell en Visual Studio Code][ps-vscode]
- [Introducción al desarrollo de PowerShell en Visual Studio Code][getting-started]
- [Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 1][editing-part1]
- [Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 2][editing-part2]
- [Depuración de scripts de PowerShell en Visual Studio Code, parte 1][debugging-part1]
- [Depuración de scripts de PowerShell en Visual Studio Code, parte 2][debugging-part2]

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a>Extensión de PowerShell para VSCode

Encontrará en [GitHub](https://github.com/PowerShell/vscode-powershell) el código fuente de la extensión de PowerShell.
