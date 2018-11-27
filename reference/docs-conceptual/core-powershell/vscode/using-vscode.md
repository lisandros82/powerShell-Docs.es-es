---
title: Uso de Visual Studio Code para el desarrollo de PowerShell
description: Uso de Visual Studio Code para el desarrollo de PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 6433a875c233283f94d70c7acd7d394c73029b6d
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320455"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Uso de Visual Studio Code para el desarrollo de PowerShell

Además de [PowerShell ISE][ise], PowerShell también se admite en Visual Studio Code.
Por otra parte, el ISE no es compatible con PowerShell Core, mientras que Visual Studio Code es compatible con PowerShell Core en todas las plataformas (Windows, macOS y Linux).

Puede usar Visual Studio Code en Windows con PowerShell versión 5 a través de Windows 10 o mediante la instalación de [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para sistemas operativos Windows inferiores (por ejemplo, Windows 8.1, etc).

Antes de iniciarlo, asegúrese de que tiene PowerShell en el sistema.
Para cargas de trabajo modernas de Windows, macOS y Linux, vea:

- [Instalación de PowerShell Core en Linux][install-pscore-linux]
- [Instalación de PowerShell Core en macOS][install-pscore-macos]
- [Instalación de PowerShell Core en Windows][install-pscore-windows]

Para cargas de trabajo de Windows PowerShell tradicionales, vea [Instalación de Windows PowerShell][install-winps].

## <a name="editing-with-visual-studio-code"></a>Edición con Visual Studio Code

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Instalación de Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: siga las instrucciones de instalación de la página [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) (Ejecución de VS Code en Linux).

- **macOS**: siga las instrucciones de instalación de la página [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) (Ejecución de VS Code en macOS).

  > [!IMPORTANT]
  > En macOS, debe instalar OpenSSL para que la extensión de PowerShell funcione correctamente.
  > La manera más fácil de hacerlo consiste en instalar [Homebrew](https://brew.sh/) y ejecutar `brew install openssl`.
  > Ahora VS Code puede cargar la extensión de PowerShell correctamente.

- **Windows**: siga las instrucciones de instalación de la página [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) (Ejecución de VS Code en Windows).

### <a name="2-installing-powershell-extension"></a>2. Instalación de la extensión de PowerShell

- Inicie la aplicación de Visual Studio Code. Para ello, haga lo siguiente:
  - **Windows**: escriba `code` en la sesión de PowerShell.
  - **Linux**: escriba `code` en el terminal.
  - **macOS**: escriba `code` en el terminal.

- Inicie **Quick Open**. Para ello, presione **CTRL+P** (**Cmd+P** en Mac).
- En Quick Open, escriba `ext install powershell` y presione **ENTRAR**.
- Se abre la vista **Extensiones** en la barra lateral. Seleccione la extensión de PowerShell de Microsoft.
  Debería ver algo parecido a lo siguiente:

  ![VSCode](../../images/vscode.png)

- Haga clic en el botón **Instalar** en la extensión de PowerShell de Microsoft.
- Después de la instalación, se ve que el botón **Instalar** cambia a **Recargar**.
  Haga clic en **Recargar**.
- Una vez que se haya vuelto a cargar Visual Studio Code, estará listo para la edición.

Por ejemplo, para crear un archivo, haga clic en **Archivo -> Nuevo**.
Para guardarlo, haga clic en **Archivo -> Guardar** y proporcione un nombre de archivo; por ejemplo, `HelloWorld.ps1`.
Para cerrar el archivo, haga clic en "x" junto al nombre de archivo.
Para salir de Visual Studio Code, haga clic en **Archivo -> Salir**.

#### <a name="using-a-specific-installed-version-of-powershell"></a>Uso de una versión instalada específica de PowerShell

Si quiere usar una instalación específica de PowerShell con Visual Studio Code, debe agregar una nueva variable al archivo de configuración de usuario.

1. Haga clic en **Archivo -> Preferencias -> Configuración**.
1. Aparecen dos paneles del editor.
   En el panel de la derecha (`settings.json`), inserte uno de los valores de configuración siguientes, en función de su sistema operativo, en alguna parte entre las dos llaves (`{` y `}`) y reemplace **\<versión\>** por la versión de PowerShell instalada:

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. Reemplace la configuración por la ruta de acceso al ejecutable de PowerShell deseado.
1. Guarde el archivo de configuración y reinicie Visual Studio Code.

#### <a name="configuration-settings-for-visual-studio-code"></a>Valores de configuración para Visual Studio Code

Mediante los pasos del párrafo anterior, puede agregar valores de configuración en `settings.json`.

Recomendamos los valores de configuración siguientes para Visual Studio Code:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>Depuración con Visual Studio Code

### <a name="no-workspace-debugging"></a>Depuración fuera del área de trabajo

A partir de Visual Studio Code versión 1.9 puede depurar scripts de PowerShell sin tener que abrir la carpeta que contiene el script de PowerShell.
Solo tiene que abrir el archivo de script de PowerShell con **Archivo -> Abrir archivo…**, establecer un punto de interrupción en una línea (presione F9) y, después, presionar F5 para iniciar la depuración.
Aparece el panel de acciones de depuración, que le permite obtener acceso al depurador, realizar la depuración paso a paso, reanudarla y detenerla.

### <a name="workspace-debugging"></a>Depuración del área de trabajo

La depuración del área de trabajo hace referencia a la depuración en el contexto de una carpeta que se ha abierto en Visual Studio Code mediante **Abrir carpeta…** desde el menú **Archivo**.
Suele tratarse de la carpeta del proyecto de PowerShell o la raíz del repositorio de Git.

Incluso en este modo, para empezar a depurar el script de PowerShell seleccionado, basta con presionar F5.
La depuración del área de trabajo no se limita a depurar el archivo abierto actualmente, sino que permite definir diversas configuraciones de depuración.
Por ejemplo, puede agregar configuraciones para:

- Iniciar pruebas de Pester en el depurador
- Iniciar un archivo específico con argumentos en el depurador
- Iniciar una sesión interactiva en el depurador
- Asociar el depurador a un proceso de host de PowerShell

Siga los pasos siguientes para crear el archivo de configuración de depuración:

  1. Abra la vista **Depurar**. Para ello, presione **Ctrl+Mayús+D** (**Cmd+Mayús+ D** en Mac).
  2. Presione el icono de engranaje **Configurar** en la barra de herramientas.
  3. Visual Studio Code le solicita que **seleccione un entorno**. Elija **PowerShell**.

  Cuando lo haga, Visual Studio Code creará un directorio y un archivo ".vscode\launch.json" en la raíz de la carpeta del área de trabajo.
  Aquí es donde se almacenará la configuración de depuración. Si los archivos están en un repositorio de Git, normalmente le interesa confirmar el archivo launch.json.
  El contenido del archivo launch.json es el siguiente:

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

  Esto representa los escenarios de depuración comunes.
  Aun así, cuando se abre este archivo en el editor, se ve el botón **Agregar configuración…**.
  Puede presionar este botón para agregar más configuraciones de depuración de PowerShell. Una configuración muy útil que conviene agregar es **PowerShell: Iniciar script**.
  Con esta configuración, puede especificar un archivo concreto con argumentos opcionales que se debe iniciar cada vez que se presione F5, independientemente del archivo que esté activo en el momento en el editor.

  Una vez establecida la configuración de depuración, puede seleccionar la configuración que quiere usar durante una sesión de depuración. Para ello, selecciónela en el menú desplegable de la barra de herramientas de la vista **Depurar**.

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

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>Extensión de PowerShell para Visual Studio Code

Encontrará en [GitHub](https://github.com/PowerShell/vscode-powershell) el código fuente de la extensión de PowerShell.
