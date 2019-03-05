---
title: Uso de Visual Studio Code para el desarrollo de PowerShell
description: Uso de Visual Studio Code para el desarrollo de PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 1e9b9d811a39656327af2810bd6dc8aaf3fde3a4
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251394"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="50590-103">Uso de Visual Studio Code para el desarrollo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="50590-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="50590-104">Además de [PowerShell ISE][ise], PowerShell también se admite en Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="50590-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="50590-105">Por otra parte, el ISE no es compatible con PowerShell Core, mientras que Visual Studio Code es compatible con PowerShell Core en todas las plataformas (Windows, macOS y Linux).</span><span class="sxs-lookup"><span data-stu-id="50590-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="50590-106">Puede usar Visual Studio Code en Windows con PowerShell versión 5 a través de Windows 10 o mediante la instalación de [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para sistemas operativos Windows inferiores (por ejemplo, Windows 8.1, etc).</span><span class="sxs-lookup"><span data-stu-id="50590-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="50590-107">Antes de iniciarlo, asegúrese de que tiene PowerShell en el sistema.</span><span class="sxs-lookup"><span data-stu-id="50590-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="50590-108">Para cargas de trabajo modernas de Windows, macOS y Linux, vea:</span><span class="sxs-lookup"><span data-stu-id="50590-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="50590-109">[Instalación de PowerShell Core en Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="50590-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="50590-110">[Instalación de PowerShell Core en macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="50590-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="50590-111">[Instalación de PowerShell Core en Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="50590-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="50590-112">Para cargas de trabajo de Windows PowerShell tradicionales, vea [Instalación de Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="50590-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="50590-113">Edición con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="50590-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="50590-114">1. Instalación de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="50590-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="50590-115">**Linux**: siga las instrucciones de instalación de la página [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) (Ejecución de VS Code en Linux).</span><span class="sxs-lookup"><span data-stu-id="50590-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="50590-116">**macOS**: siga las instrucciones de instalación de la página [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) (Ejecución de VS Code en macOS).</span><span class="sxs-lookup"><span data-stu-id="50590-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="50590-117">En macOS, debe instalar OpenSSL para que la extensión de PowerShell funcione correctamente.</span><span class="sxs-lookup"><span data-stu-id="50590-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="50590-118">La manera más fácil de hacerlo consiste en instalar [Homebrew](https://brew.sh/) y ejecutar `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="50590-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="50590-119">Ahora VS Code puede cargar la extensión de PowerShell correctamente.</span><span class="sxs-lookup"><span data-stu-id="50590-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="50590-120">**Windows**: siga las instrucciones de instalación de la página [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) (Ejecución de VS Code en Windows).</span><span class="sxs-lookup"><span data-stu-id="50590-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="50590-121">2. Instalación de la extensión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="50590-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="50590-122">Inicie la aplicación de Visual Studio Code. Para ello, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="50590-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="50590-123">**Windows**: escriba `code` en la sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50590-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="50590-124">**Linux**: escriba `code` en el terminal.</span><span class="sxs-lookup"><span data-stu-id="50590-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="50590-125">**macOS**: escriba `code` en el terminal.</span><span class="sxs-lookup"><span data-stu-id="50590-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="50590-126">Inicie **Quick Open**. Para ello, presione **CTRL+P** (**Cmd+P** en Mac).</span><span class="sxs-lookup"><span data-stu-id="50590-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="50590-127">En Quick Open, escriba `ext install powershell` y presione **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="50590-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="50590-128">Se abre la vista **Extensiones** en la barra lateral.</span><span class="sxs-lookup"><span data-stu-id="50590-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="50590-129">Seleccione la extensión de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="50590-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="50590-130">Debería ver algo parecido a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="50590-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="50590-132">Haga clic en el botón **Instalar** en la extensión de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="50590-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="50590-133">Después de la instalación, se ve que el botón **Instalar** cambia a **Recargar**.</span><span class="sxs-lookup"><span data-stu-id="50590-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="50590-134">Haga clic en **Recargar**.</span><span class="sxs-lookup"><span data-stu-id="50590-134">Click on **Reload**.</span></span>
- <span data-ttu-id="50590-135">Una vez que se haya vuelto a cargar Visual Studio Code, estará listo para la edición.</span><span class="sxs-lookup"><span data-stu-id="50590-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="50590-136">Por ejemplo, para crear un archivo, haga clic en **Archivo -> Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="50590-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="50590-137">Para guardarlo, haga clic en **Archivo -> Guardar** y proporcione un nombre de archivo; por ejemplo, `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="50590-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="50590-138">Para cerrar el archivo, haga clic en "x" junto al nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="50590-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="50590-139">Para salir de Visual Studio Code, haga clic en **Archivo -> Salir**.</span><span class="sxs-lookup"><span data-stu-id="50590-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="50590-140">Instalando la extensión de PowerShell en sistemas restringidos</span><span class="sxs-lookup"><span data-stu-id="50590-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="50590-141">Algunos sistemas se configuran de forma que requiere que todas las firmas de código se va a comprobar y, por tanto, requiere que los servicios de Editor de PowerShell que se apruebe manualmente para ejecutarse en el sistema.</span><span class="sxs-lookup"><span data-stu-id="50590-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="50590-142">Una actualización de directiva de grupo que cambia la directiva de ejecución es una causa probable si ha instalado la extensión de PowerShell, pero están llegando a un error como:</span><span class="sxs-lookup"><span data-stu-id="50590-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="50590-143">Para aprobar manualmente los servicios del Editor de PowerShell y, por tanto, la extensión de PowerShell para VSCode abren un símbolo del sistema y ejecución de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="50590-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="50590-144">Se le solicite "¿desea ejecutar software de este publicador que no se confía?"</span><span class="sxs-lookup"><span data-stu-id="50590-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="50590-145">Tipo `R` para ejecutar el archivo.</span><span class="sxs-lookup"><span data-stu-id="50590-145">Type `R` to run the file.</span></span> <span data-ttu-id="50590-146">A continuación, abra Visual Studio Code y compruebe que la extensión de PowerShell funcione correctamente.</span><span class="sxs-lookup"><span data-stu-id="50590-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="50590-147">Si sigue teniendo problemas de introducción, háganoslo saber en [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="50590-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="50590-148">Uso de una versión instalada específica de PowerShell</span><span class="sxs-lookup"><span data-stu-id="50590-148">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="50590-149">Si quiere usar una instalación específica de PowerShell con Visual Studio Code, debe agregar una nueva variable al archivo de configuración de usuario.</span><span class="sxs-lookup"><span data-stu-id="50590-149">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="50590-150">Haga clic en **Archivo -> Preferencias -> Configuración**.</span><span class="sxs-lookup"><span data-stu-id="50590-150">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="50590-151">Aparecen dos paneles del editor.</span><span class="sxs-lookup"><span data-stu-id="50590-151">Two editor panes appear.</span></span>
   <span data-ttu-id="50590-152">En el panel de la derecha (`settings.json`), inserte uno de los valores de configuración siguientes, en función de su sistema operativo, en alguna parte entre las dos llaves (`{` y `}`) y reemplace **\<versión\>** por la versión de PowerShell instalada:</span><span class="sxs-lookup"><span data-stu-id="50590-152">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="50590-153">Reemplace la configuración por la ruta de acceso al ejecutable de PowerShell deseado.</span><span class="sxs-lookup"><span data-stu-id="50590-153">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="50590-154">Guarde el archivo de configuración y reinicie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="50590-154">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="50590-155">Valores de configuración para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="50590-155">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="50590-156">Mediante los pasos del párrafo anterior, puede agregar valores de configuración en `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="50590-156">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="50590-157">Recomendamos los valores de configuración siguientes para Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="50590-157">We recommend the following configuration settings for Visual Studio Code:</span></span>

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

<span data-ttu-id="50590-158">Si no desea que esta configuración afecta a todos los tipos de archivos, VSCode también permite que las configuraciones por idioma.</span><span class="sxs-lookup"><span data-stu-id="50590-158">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="50590-159">Crear una configuración específica del lenguaje colocando la configuración un `[<language-name>]` campo.</span><span class="sxs-lookup"><span data-stu-id="50590-159">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="50590-160">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="50590-160">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="50590-161">Para obtener más información sobre el archivo de codificación en VS Code, consulte [descripción de codificación del archivo](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="50590-161">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="50590-162">Depuración con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="50590-162">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="50590-163">Depuración fuera del área de trabajo</span><span class="sxs-lookup"><span data-stu-id="50590-163">No-workspace debugging</span></span>

<span data-ttu-id="50590-164">A partir de Visual Studio Code versión 1.9 puede depurar scripts de PowerShell sin tener que abrir la carpeta que contiene el script de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50590-164">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="50590-165">Abra el archivo de script de PowerShell con **archivo -> Abrir archivo...** , establezca un punto de interrupción en una línea (presione F9) y, a continuación, presione F5 para iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="50590-165">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="50590-166">Aparece el panel de acciones de depuración, que le permite obtener acceso al depurador, realizar la depuración paso a paso, reanudarla y detenerla.</span><span class="sxs-lookup"><span data-stu-id="50590-166">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="50590-167">Depuración del área de trabajo</span><span class="sxs-lookup"><span data-stu-id="50590-167">Workspace debugging</span></span>

<span data-ttu-id="50590-168">La depuración del área de trabajo hace referencia a la depuración en el contexto de una carpeta que se ha abierto en Visual Studio Code mediante **Abrir carpeta…** desde el menú **Archivo**.</span><span class="sxs-lookup"><span data-stu-id="50590-168">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="50590-169">Suele tratarse de la carpeta del proyecto de PowerShell o la raíz del repositorio de Git.</span><span class="sxs-lookup"><span data-stu-id="50590-169">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="50590-170">Incluso en este modo, para empezar a depurar el script de PowerShell seleccionado, basta con presionar F5.</span><span class="sxs-lookup"><span data-stu-id="50590-170">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="50590-171">La depuración del área de trabajo no se limita a depurar el archivo abierto actualmente, sino que permite definir diversas configuraciones de depuración.</span><span class="sxs-lookup"><span data-stu-id="50590-171">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="50590-172">Por ejemplo, puede agregar configuraciones para:</span><span class="sxs-lookup"><span data-stu-id="50590-172">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="50590-173">Iniciar pruebas de Pester en el depurador</span><span class="sxs-lookup"><span data-stu-id="50590-173">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="50590-174">Iniciar un archivo específico con argumentos en el depurador</span><span class="sxs-lookup"><span data-stu-id="50590-174">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="50590-175">Iniciar una sesión interactiva en el depurador</span><span class="sxs-lookup"><span data-stu-id="50590-175">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="50590-176">Asociar el depurador a un proceso de host de PowerShell</span><span class="sxs-lookup"><span data-stu-id="50590-176">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="50590-177">Siga los pasos siguientes para crear el archivo de configuración de depuración:</span><span class="sxs-lookup"><span data-stu-id="50590-177">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="50590-178">Abra la vista **Depurar**. Para ello, presione **Ctrl+Mayús+D** (**Cmd+Mayús+ D** en Mac).</span><span class="sxs-lookup"><span data-stu-id="50590-178">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="50590-179">Presione el icono de engranaje **Configurar** en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="50590-179">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="50590-180">Visual Studio Code le solicita que **seleccione un entorno**.</span><span class="sxs-lookup"><span data-stu-id="50590-180">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="50590-181">Elija **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="50590-181">Choose **PowerShell**.</span></span>

  <span data-ttu-id="50590-182">Cuando lo haga, Visual Studio Code creará un directorio y un archivo ".vscode\launch.json" en la raíz de la carpeta del área de trabajo.</span><span class="sxs-lookup"><span data-stu-id="50590-182">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="50590-183">Aquí es donde se almacenará la configuración de depuración.</span><span class="sxs-lookup"><span data-stu-id="50590-183">This is where your debug configuration is stored.</span></span> <span data-ttu-id="50590-184">Si los archivos están en un repositorio de Git, normalmente le interesa confirmar el archivo launch.json.</span><span class="sxs-lookup"><span data-stu-id="50590-184">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="50590-185">El contenido del archivo launch.json es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="50590-185">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="50590-186">Esto representa los escenarios de depuración comunes.</span><span class="sxs-lookup"><span data-stu-id="50590-186">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="50590-187">Aun así, cuando se abre este archivo en el editor, se ve el botón **Agregar configuración…**.</span><span class="sxs-lookup"><span data-stu-id="50590-187">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="50590-188">Puede presionar este botón para agregar más configuraciones de depuración de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50590-188">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="50590-189">Una configuración muy útil que conviene agregar es **PowerShell: Iniciar script**.</span><span class="sxs-lookup"><span data-stu-id="50590-189">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="50590-190">Con esta configuración, puede especificar un archivo concreto con argumentos opcionales que se debe iniciar cada vez que se presione F5, independientemente del archivo que esté activo en el momento en el editor.</span><span class="sxs-lookup"><span data-stu-id="50590-190">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="50590-191">Una vez establecida la configuración de depuración, puede seleccionar la configuración que quiere usar durante una sesión de depuración. Para ello, selecciónela en el menú desplegable de la barra de herramientas de la vista **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="50590-191">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="50590-192">Algunos blogs pueden servirle de ayuda para empezar a usar la extensión de PowerShell para Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="50590-192">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="50590-193">[Extensión de PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="50590-193">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="50590-194">[Escritura y depuración de scripts de PowerShell en Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="50590-194">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="50590-195">[Instrucciones de depuración de Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="50590-195">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="50590-196">[Depuración de PowerShell en Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="50590-196">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="50590-197">[Introducción al desarrollo de PowerShell en Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="50590-197">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="50590-198">[Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="50590-198">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="50590-199">[Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="50590-199">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="50590-200">[Depuración de scripts de PowerShell en Visual Studio Code, parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="50590-200">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="50590-201">[Depuración de scripts de PowerShell en Visual Studio Code, parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="50590-201">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="50590-202">Extensión de PowerShell para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="50590-202">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="50590-203">Encontrará en [GitHub](https://github.com/PowerShell/vscode-powershell) el código fuente de la extensión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50590-203">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
