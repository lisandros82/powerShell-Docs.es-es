---
title: Uso de Visual Studio Code para el desarrollo de PowerShell
description: Uso de Visual Studio Code para el desarrollo de PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: f8e1e9af257037fc7bd74549e4197c9a1695e952
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587438"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="eda0c-103">Uso de Visual Studio Code para el desarrollo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="eda0c-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="eda0c-104">Además de [PowerShell ISE][ise], PowerShell también se admite en Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="eda0c-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="eda0c-105">Por otra parte, el ISE no es compatible con PowerShell Core, mientras que Visual Studio Code es compatible con PowerShell Core en todas las plataformas (Windows, macOS y Linux).</span><span class="sxs-lookup"><span data-stu-id="eda0c-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="eda0c-106">Puede usar Visual Studio Code en Windows con PowerShell versión 5 a través de Windows 10 o mediante la instalación de [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para sistemas operativos Windows inferiores (por ejemplo, Windows 8.1, etc).</span><span class="sxs-lookup"><span data-stu-id="eda0c-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="eda0c-107">Antes de iniciarlo, asegúrese de que tiene PowerShell en el sistema.</span><span class="sxs-lookup"><span data-stu-id="eda0c-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="eda0c-108">Para cargas de trabajo modernas de Windows, macOS y Linux, vea:</span><span class="sxs-lookup"><span data-stu-id="eda0c-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="eda0c-109">[Instalación de PowerShell Core en Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="eda0c-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="eda0c-110">[Instalación de PowerShell Core en macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="eda0c-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="eda0c-111">[Instalación de PowerShell Core en Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="eda0c-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="eda0c-112">Para cargas de trabajo de Windows PowerShell tradicionales, vea [Instalación de Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="eda0c-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="eda0c-113">Edición con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eda0c-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="eda0c-114">1. Instalación de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eda0c-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="eda0c-115">**Linux**: siga las instrucciones de instalación de la página [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) (Ejecución de VS Code en Linux).</span><span class="sxs-lookup"><span data-stu-id="eda0c-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="eda0c-116">**macOS**: siga las instrucciones de instalación de la página [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) (Ejecución de VS Code en macOS).</span><span class="sxs-lookup"><span data-stu-id="eda0c-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="eda0c-117">En macOS, debe instalar OpenSSL para que la extensión de PowerShell funcione correctamente.</span><span class="sxs-lookup"><span data-stu-id="eda0c-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="eda0c-118">La manera más fácil de hacerlo consiste en instalar [Homebrew](http://brew.sh/) y ejecutar `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="eda0c-118">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="eda0c-119">Ahora el código de VS puede cargar la extensión de PowerShell correctamente.</span><span class="sxs-lookup"><span data-stu-id="eda0c-119">VS Code can now load the the PowerShell extension successfully.</span></span>

- <span data-ttu-id="eda0c-120">**Windows**: siga las instrucciones de instalación de la página [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) (Ejecución de VS Code en Windows).</span><span class="sxs-lookup"><span data-stu-id="eda0c-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="eda0c-121">2. Instalación de la extensión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="eda0c-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="eda0c-122">Inicie la aplicación de Visual Studio Code. Para ello, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="eda0c-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="eda0c-123">**Windows**: escriba `code` en la sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eda0c-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="eda0c-124">**Linux**: escriba `code` en el terminal.</span><span class="sxs-lookup"><span data-stu-id="eda0c-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="eda0c-125">**macOS**: escriba `code` en el terminal.</span><span class="sxs-lookup"><span data-stu-id="eda0c-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="eda0c-126">Inicie **Quick Open**. Para ello, presione **CTRL+P** (**Cmd+P** en Mac).</span><span class="sxs-lookup"><span data-stu-id="eda0c-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="eda0c-127">En Quick Open, escriba `ext install powershell` y presione **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="eda0c-128">Se abre la vista **Extensiones** en la barra lateral.</span><span class="sxs-lookup"><span data-stu-id="eda0c-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="eda0c-129">Seleccione la extensión de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eda0c-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="eda0c-130">Debería ver algo parecido a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="eda0c-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="eda0c-132">Haga clic en el botón **Instalar** en la extensión de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eda0c-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="eda0c-133">Después de la instalación, se ve que el botón **Instalar** cambia a **Recargar**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="eda0c-134">Haga clic en **Recargar**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-134">Click on **Reload**.</span></span>
- <span data-ttu-id="eda0c-135">Una vez que se haya vuelto a cargar Visual Studio Code, estará listo para la edición.</span><span class="sxs-lookup"><span data-stu-id="eda0c-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="eda0c-136">Por ejemplo, para crear un archivo, haga clic en **Archivo -> Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="eda0c-137">Para guardarlo, haga clic en **Archivo -> Guardar** y proporcione un nombre de archivo; por ejemplo, `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="eda0c-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="eda0c-138">Para cerrar el archivo, haga clic en "x" junto al nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="eda0c-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="eda0c-139">Para salir de Visual Studio Code, haga clic en **Archivo -> Salir**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-139">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="eda0c-140">Uso de una versión instalada específica de PowerShell</span><span class="sxs-lookup"><span data-stu-id="eda0c-140">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="eda0c-141">Si quiere usar una instalación específica de PowerShell con Visual Studio Code, debe agregar una nueva variable al archivo de configuración de usuario.</span><span class="sxs-lookup"><span data-stu-id="eda0c-141">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="eda0c-142">Haga clic en **Archivo -> Preferencias -> Configuración**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-142">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="eda0c-143">Aparecen dos paneles del editor.</span><span class="sxs-lookup"><span data-stu-id="eda0c-143">Two editor panes appear.</span></span>
   <span data-ttu-id="eda0c-144">En el panel de la derecha (`settings.json`), inserte uno de los valores de configuración siguientes, en función de su sistema operativo, en alguna parte entre las dos llaves (`{` y `}`) y reemplace **\<versión\>** por la versión de PowerShell instalada:</span><span class="sxs-lookup"><span data-stu-id="eda0c-144">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="eda0c-145">Reemplace la configuración por la ruta de acceso al ejecutable de PowerShell deseado.</span><span class="sxs-lookup"><span data-stu-id="eda0c-145">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="eda0c-146">Guarde el archivo de configuración y reinicie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="eda0c-146">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="eda0c-147">Valores de configuración para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eda0c-147">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="eda0c-148">Mediante los pasos del párrafo anterior, puede agregar valores de configuración en `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="eda0c-148">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="eda0c-149">Recomendamos los valores de configuración siguientes para Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="eda0c-149">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="eda0c-150">Depuración con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eda0c-150">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="eda0c-151">Depuración fuera del área de trabajo</span><span class="sxs-lookup"><span data-stu-id="eda0c-151">No-workspace debugging</span></span>

<span data-ttu-id="eda0c-152">A partir de Visual Studio Code versión 1.9 puede depurar scripts de PowerShell sin tener que abrir la carpeta que contiene el script de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eda0c-152">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="eda0c-153">Solo tiene que abrir el archivo de script de PowerShell con **Archivo -> Abrir archivo…**, establecer un punto de interrupción en una línea (presione F9) y, después, presionar F5 para iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="eda0c-153">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="eda0c-154">Aparece el panel de acciones de depuración, que le permite obtener acceso al depurador, realizar la depuración paso a paso, reanudarla y detenerla.</span><span class="sxs-lookup"><span data-stu-id="eda0c-154">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="eda0c-155">Depuración del área de trabajo</span><span class="sxs-lookup"><span data-stu-id="eda0c-155">Workspace debugging</span></span>

<span data-ttu-id="eda0c-156">La depuración del área de trabajo hace referencia a la depuración en el contexto de una carpeta que se ha abierto en Visual Studio Code mediante **Abrir carpeta…** desde el menú **Archivo**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-156">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="eda0c-157">Suele tratarse de la carpeta del proyecto de PowerShell o la raíz del repositorio de Git.</span><span class="sxs-lookup"><span data-stu-id="eda0c-157">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="eda0c-158">Incluso en este modo, para empezar a depurar el script de PowerShell seleccionado, basta con presionar F5.</span><span class="sxs-lookup"><span data-stu-id="eda0c-158">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="eda0c-159">La depuración del área de trabajo no se limita a depurar el archivo abierto actualmente, sino que permite definir diversas configuraciones de depuración.</span><span class="sxs-lookup"><span data-stu-id="eda0c-159">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="eda0c-160">Por ejemplo, puede agregar configuraciones para:</span><span class="sxs-lookup"><span data-stu-id="eda0c-160">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="eda0c-161">Iniciar pruebas de Pester en el depurador</span><span class="sxs-lookup"><span data-stu-id="eda0c-161">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="eda0c-162">Iniciar un archivo específico con argumentos en el depurador</span><span class="sxs-lookup"><span data-stu-id="eda0c-162">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="eda0c-163">Iniciar una sesión interactiva en el depurador</span><span class="sxs-lookup"><span data-stu-id="eda0c-163">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="eda0c-164">Asociar el depurador a un proceso de host de PowerShell</span><span class="sxs-lookup"><span data-stu-id="eda0c-164">Attach the debugger to a PowerShell host process</span></span>

  <span data-ttu-id="eda0c-165">Siga los pasos siguientes para crear el archivo de configuración de depuración:</span><span class="sxs-lookup"><span data-stu-id="eda0c-165">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="eda0c-166">Abra la vista **Depurar**. Para ello, presione **Ctrl+Mayús+D** (**Cmd+Mayús+ D** en Mac).</span><span class="sxs-lookup"><span data-stu-id="eda0c-166">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="eda0c-167">Presione el icono de engranaje **Configurar** en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="eda0c-167">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="eda0c-168">Visual Studio Code le solicita que **seleccione un entorno**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-168">Visual Studio Code prompts you to **Select Environment**.</span></span>
  <span data-ttu-id="eda0c-169">Elija **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-169">Choose **PowerShell**.</span></span>

  <span data-ttu-id="eda0c-170">Cuando lo haga, Visual Studio Code creará un directorio y un archivo ".vscode\launch.json" en la raíz de la carpeta del área de trabajo.</span><span class="sxs-lookup"><span data-stu-id="eda0c-170">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="eda0c-171">Aquí es donde se almacenará la configuración de depuración.</span><span class="sxs-lookup"><span data-stu-id="eda0c-171">This is where your debug configuration is stored.</span></span> <span data-ttu-id="eda0c-172">Si los archivos están en un repositorio de Git, normalmente le interesa confirmar el archivo launch.json.</span><span class="sxs-lookup"><span data-stu-id="eda0c-172">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="eda0c-173">El contenido del archivo launch.json es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="eda0c-173">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="eda0c-174">Esto representa los escenarios de depuración comunes.</span><span class="sxs-lookup"><span data-stu-id="eda0c-174">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="eda0c-175">Aun así, cuando se abre este archivo en el editor, se ve el botón **Agregar configuración…**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-175">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="eda0c-176">Puede presionar este botón para agregar más configuraciones de depuración de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eda0c-176">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="eda0c-177">Una configuración muy útil que conviene agregar es **PowerShell: Iniciar script**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-177">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="eda0c-178">Con esta configuración, puede especificar un archivo concreto con argumentos opcionales que se debe iniciar cada vez que se presione F5, independientemente del archivo que esté activo en el momento en el editor.</span><span class="sxs-lookup"><span data-stu-id="eda0c-178">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="eda0c-179">Una vez establecida la configuración de depuración, puede seleccionar la configuración que quiere usar durante una sesión de depuración. Para ello, selecciónela en el menú desplegable de la barra de herramientas de la vista **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="eda0c-179">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

  <span data-ttu-id="eda0c-180">Algunos blogs pueden serle de ayuda para empezar a usar la extensión de PowerShell para Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="eda0c-180">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="eda0c-181">Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="eda0c-181">Visual Studio Code:</span></span>

- <span data-ttu-id="eda0c-182">[Extensión de PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="eda0c-182">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="eda0c-183">[Escritura y depuración de scripts de PowerShell en Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="eda0c-183">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="eda0c-184">[Instrucciones de depuración de Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="eda0c-184">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="eda0c-185">[Depuración de PowerShell en Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="eda0c-185">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="eda0c-186">[Introducción al desarrollo de PowerShell en Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="eda0c-186">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="eda0c-187">[Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="eda0c-187">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="eda0c-188">[Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="eda0c-188">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="eda0c-189">[Depuración de scripts de PowerShell en Visual Studio Code, parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="eda0c-189">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="eda0c-190">[Depuración de scripts de PowerShell en Visual Studio Code, parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="eda0c-190">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="eda0c-191">Extensión de PowerShell para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eda0c-191">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="eda0c-192">Encontrará en [GitHub](https://github.com/PowerShell/vscode-powershell) el código fuente de la extensión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eda0c-192">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>