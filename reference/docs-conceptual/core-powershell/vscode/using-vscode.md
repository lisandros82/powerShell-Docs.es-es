# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="df487-101">Uso de Visual Studio Code para el desarrollo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="df487-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="df487-102">Además de [PowerShell ISE][ise], PowerShell también se admite en Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="df487-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="df487-103">Por otra parte, el ISE no es compatible con PowerShell Core, mientras que Visual Studio Code es compatible con PowerShell Core en todas las plataformas (Windows, macOS y Linux).</span><span class="sxs-lookup"><span data-stu-id="df487-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="df487-104">Puede usar Visual Studio Code en Windows con PowerShell versión 5 a través de Windows 10 o mediante la instalación de [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para sistemas operativos Windows inferiores (por ejemplo, Windows 8.1, etc).</span><span class="sxs-lookup"><span data-stu-id="df487-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="df487-105">Antes de iniciarlo, asegúrese de que tiene PowerShell en el sistema.</span><span class="sxs-lookup"><span data-stu-id="df487-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="df487-106">Para cargas de trabajo modernas de Windows, macOS y Linux, vea:</span><span class="sxs-lookup"><span data-stu-id="df487-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="df487-107">[Instalación de PowerShell Core en macOS y Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="df487-107">[Installing PowerShell Core on macOS and Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="df487-108">[Instalación de PowerShell Core en Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="df487-108">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="df487-109">Para cargas de trabajo de Windows PowerShell tradicionales, vea [Instalación de Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="df487-109">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="df487-110">Edición con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="df487-110">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="df487-111">1. Instalación de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="df487-111">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="df487-112">**Linux**: siga las instrucciones de instalación de la página [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) (Ejecución de VS Code en Linux).</span><span class="sxs-lookup"><span data-stu-id="df487-112">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="df487-113">**macOS**: siga las instrucciones de instalación de la página [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) (Ejecución de VS Code en macOS).</span><span class="sxs-lookup"><span data-stu-id="df487-113">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df487-114">En macOS, debe instalar OpenSSL para que la extensión de PowerShell funcione correctamente.</span><span class="sxs-lookup"><span data-stu-id="df487-114">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
> <span data-ttu-id="df487-115">La manera más fácil de hacerlo consiste en instalar [Homebrew](http://brew.sh/) y ejecutar `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="df487-115">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
> <span data-ttu-id="df487-116">La extensión de PowerShell ahora se cargará correctamente.</span><span class="sxs-lookup"><span data-stu-id="df487-116">The PowerShell extension will now be able to load successfully.</span></span>

- <span data-ttu-id="df487-117">**Windows**: siga las instrucciones de instalación de la página [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) (Ejecución de VS Code en Windows).</span><span class="sxs-lookup"><span data-stu-id="df487-117">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="df487-118">2. Instalación de la extensión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="df487-118">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="df487-119">Inicie la aplicación de Visual Studio Code. Para ello, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="df487-119">Launch the Visual Studio Code app by:</span></span>
    - <span data-ttu-id="df487-120">**Windows**: escriba `code` en la sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df487-120">**Windows**: typing `code` in your PowerShell session</span></span>
    - <span data-ttu-id="df487-121">**Linux**: escriba `code` en el terminal.</span><span class="sxs-lookup"><span data-stu-id="df487-121">**Linux**: typing `code` in your terminal</span></span>
    - <span data-ttu-id="df487-122">**macOS**: escriba `code` en el terminal.</span><span class="sxs-lookup"><span data-stu-id="df487-122">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="df487-123">Inicie **Quick Open**. Para ello, presione **CTRL+P** (**Cmd+P** en Mac).</span><span class="sxs-lookup"><span data-stu-id="df487-123">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="df487-124">En Quick Open, escriba `ext install powershell` y presione **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="df487-124">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="df487-125">Se abrirá la vista **Extensiones** en la barra lateral.</span><span class="sxs-lookup"><span data-stu-id="df487-125">The **Extensions** view will open on the Side Bar.</span></span> <span data-ttu-id="df487-126">Seleccione la extensión de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="df487-126">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="df487-127">Verá algo parecido a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="df487-127">You will see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="df487-129">Haga clic en el botón **Instalar** en la extensión de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="df487-129">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="df487-130">Después de la instalación, verá que el botón **Instalar** cambia a **Recargar**.</span><span class="sxs-lookup"><span data-stu-id="df487-130">After the install, you will see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="df487-131">Haga clic en **Recargar**.</span><span class="sxs-lookup"><span data-stu-id="df487-131">Click on **Reload**.</span></span>
- <span data-ttu-id="df487-132">Una vez que se haya vuelto a cargar Visual Studio Code, estará listo para la edición.</span><span class="sxs-lookup"><span data-stu-id="df487-132">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="df487-133">Por ejemplo, para crear un archivo, haga clic en **Archivo -> Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="df487-133">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="df487-134">Para guardarlo, haga clic en **Archivo -> Guardar** y proporcione un nombre de archivo; por ejemplo, `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="df487-134">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="df487-135">Para cerrar el archivo, haga clic en "x" junto al nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="df487-135">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="df487-136">Para salir de Visual Studio Code, haga clic en **Archivo -> Salir**.</span><span class="sxs-lookup"><span data-stu-id="df487-136">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="df487-137">Uso de una versión instalada específica de PowerShell</span><span class="sxs-lookup"><span data-stu-id="df487-137">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="df487-138">Si quiere usar una instalación específica de PowerShell con Visual Studio Code, debe agregar una nueva variable al archivo de configuración de usuario.</span><span class="sxs-lookup"><span data-stu-id="df487-138">If you wish to use a specific installation of PowerShell with Visual Studio Code, you will need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="df487-139">Haga clic en **Archivo -> Preferencias -> Configuración**.</span><span class="sxs-lookup"><span data-stu-id="df487-139">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="df487-140">Aparecerán dos paneles del editor.</span><span class="sxs-lookup"><span data-stu-id="df487-140">Two editor panes will appear.</span></span>
   <span data-ttu-id="df487-141">En el panel de la derecha (`settings.json`), inserte uno de los valores de configuración siguientes, en función de su sistema operativo, en alguna parte entre las dos llaves (`{` y `}`) y reemplace *<version>* por la versión de PowerShell instalada:</span><span class="sxs-lookup"><span data-stu-id="df487-141">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. <span data-ttu-id="df487-142">Reemplace la configuración por la ruta de acceso al ejecutable de PowerShell deseado.</span><span class="sxs-lookup"><span data-stu-id="df487-142">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="df487-143">Guarde el archivo de configuración y reinicie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="df487-143">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="df487-144">Valores de configuración para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="df487-144">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="df487-145">Mediante los pasos del párrafo anterior, puede agregar valores de configuración en `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="df487-145">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="df487-146">Recomendamos los valores de configuración siguientes para Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="df487-146">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="df487-147">Depuración con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="df487-147">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="df487-148">Depuración fuera del área de trabajo</span><span class="sxs-lookup"><span data-stu-id="df487-148">No-workspace debugging</span></span>

<span data-ttu-id="df487-149">A partir de Visual Studio Code versión 1.9 puede depurar scripts de PowerShell sin tener que abrir la carpeta que contiene el script de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df487-149">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="df487-150">Solo tiene que abrir el archivo de script de PowerShell con **Archivo -> Abrir archivo…**, establecer un punto de interrupción en una línea (presione F9) y, después, presionar F5 para iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="df487-150">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="df487-151">Aparecerá el panel de acciones de depuración, que le permite obtener acceso al depurador, realizar la depuración paso a paso, reanudarla y detenerla.</span><span class="sxs-lookup"><span data-stu-id="df487-151">You will see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="df487-152">Depuración del área de trabajo</span><span class="sxs-lookup"><span data-stu-id="df487-152">Workspace debugging</span></span>

<span data-ttu-id="df487-153">La depuración del área de trabajo hace referencia a la depuración en el contexto de una carpeta que se ha abierto en Visual Studio Code mediante **Abrir carpeta…** desde el menú **Archivo**.</span><span class="sxs-lookup"><span data-stu-id="df487-153">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="df487-154">Suele tratarse de la carpeta del proyecto de PowerShell o la raíz del repositorio de Git.</span><span class="sxs-lookup"><span data-stu-id="df487-154">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="df487-155">Incluso en este modo, para empezar a depurar el script de PowerShell seleccionado, basta con presionar F5.</span><span class="sxs-lookup"><span data-stu-id="df487-155">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="df487-156">La depuración del área de trabajo no se limita a depurar el archivo abierto actualmente, sino que permite definir diversas configuraciones de depuración.</span><span class="sxs-lookup"><span data-stu-id="df487-156">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="df487-157">Por ejemplo, puede agregar configuraciones para:</span><span class="sxs-lookup"><span data-stu-id="df487-157">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="df487-158">Iniciar pruebas de Pester en el depurador</span><span class="sxs-lookup"><span data-stu-id="df487-158">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="df487-159">Iniciar un archivo específico con argumentos en el depurador</span><span class="sxs-lookup"><span data-stu-id="df487-159">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="df487-160">Iniciar una sesión interactiva en el depurador</span><span class="sxs-lookup"><span data-stu-id="df487-160">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="df487-161">Asociar el depurador a un proceso de host de PowerShell</span><span class="sxs-lookup"><span data-stu-id="df487-161">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="df487-162">Siga los pasos siguientes para crear el archivo de configuración de depuración:</span><span class="sxs-lookup"><span data-stu-id="df487-162">Follow these steps to create your debug configuration file:</span></span>

1. <span data-ttu-id="df487-163">Abra la vista **Depurar**. Para ello, presione **Ctrl+Mayús+D** (**Cmd+Mayús+ D** en Mac).</span><span class="sxs-lookup"><span data-stu-id="df487-163">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
1. <span data-ttu-id="df487-164">Presione el icono de engranaje **Configurar** en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="df487-164">Press the **Configure** gear icon in the toolbar.</span></span>
1. <span data-ttu-id="df487-165">Visual Studio Code le solicitará que **seleccione un entorno**.</span><span class="sxs-lookup"><span data-stu-id="df487-165">Visual Studio Code will prompt you to **Select Environment**.</span></span>
   <span data-ttu-id="df487-166">Elija **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="df487-166">Choose **PowerShell**.</span></span>

   <span data-ttu-id="df487-167">Cuando lo haga, Visual Studio Code creará un directorio y un archivo ".vscode\launch.json" en la raíz de la carpeta del área de trabajo.</span><span class="sxs-lookup"><span data-stu-id="df487-167">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
   <span data-ttu-id="df487-168">Aquí es donde se almacenará la configuración de depuración.</span><span class="sxs-lookup"><span data-stu-id="df487-168">This is where your debug configuration is stored.</span></span> <span data-ttu-id="df487-169">Si los archivos están en un repositorio de Git, normalmente le interesará confirmar el archivo launch.json.</span><span class="sxs-lookup"><span data-stu-id="df487-169">If your files are in a Git repository, you will typically want to commit the launch.json file.</span></span>
   <span data-ttu-id="df487-170">El contenido del archivo launch.json es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="df487-170">The contents of the launch.json file are:</span></span>

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

<span data-ttu-id="df487-171">Esto representa los escenarios de depuración comunes.</span><span class="sxs-lookup"><span data-stu-id="df487-171">This represents the common debug scenarios.</span></span>
<span data-ttu-id="df487-172">Aun así, cuando abra este archivo en el editor, verá el botón **Agregar configuración…**.</span><span class="sxs-lookup"><span data-stu-id="df487-172">However, when you open this file in the editor, you will see an **Add Configuration...** button.</span></span>
<span data-ttu-id="df487-173">Puede presionar este botón para agregar más configuraciones de depuración de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df487-173">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="df487-174">Una configuración muy útil que conviene agregar es **PowerShell: Iniciar script**.</span><span class="sxs-lookup"><span data-stu-id="df487-174">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
<span data-ttu-id="df487-175">Con esta configuración, puede especificar un archivo concreto con argumentos opcionales que se debe iniciar cada vez que se presione F5, independientemente del archivo que esté activo en el momento en el editor.</span><span class="sxs-lookup"><span data-stu-id="df487-175">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="df487-176">Una vez establecida la configuración de depuración, puede seleccionar la configuración que quiere usar durante una sesión de depuración. Para ello, selecciónela en el menú desplegable de la barra de herramientas de la vista **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="df487-176">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="df487-177">Algunos blogs pueden serle de ayuda para empezar a usar la extensión de PowerShell para Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="df487-177">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

- <span data-ttu-id="df487-178">Visual Studio Code: [extensión de PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="df487-178">Visual Studio Code: [PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="df487-179">[Escritura y depuración de scripts de PowerShell en Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="df487-179">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="df487-180">[Instrucciones de depuración de Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="df487-180">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="df487-181">[Depuración de PowerShell en Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="df487-181">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="df487-182">[Introducción al desarrollo de PowerShell en Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="df487-182">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="df487-183">[Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="df487-183">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="df487-184">[Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="df487-184">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="df487-185">[Depuración de scripts de PowerShell en Visual Studio Code, parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="df487-185">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="df487-186">[Depuración de scripts de PowerShell en Visual Studio Code, parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="df487-186">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-macOS-and-Linux.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="df487-187">Extensión de PowerShell para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="df487-187">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="df487-188">Encontrará en [GitHub](https://github.com/PowerShell/vscode-powershell) el código fuente de la extensión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df487-188">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
