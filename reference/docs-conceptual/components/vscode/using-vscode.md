---
title: Uso de Visual Studio Code para el desarrollo de PowerShell
description: Uso de Visual Studio Code para el desarrollo de PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 6a0da6e060693dc7cfc08d40fd658414dc23d660
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733879"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="71aa7-103">Uso de Visual Studio Code para el desarrollo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="71aa7-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="71aa7-104">Además de [PowerShell ISE][ise], PowerShell también se admite en Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="71aa7-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="71aa7-105">Por otra parte, el ISE no es compatible con PowerShell Core, mientras que Visual Studio Code es compatible con PowerShell Core en todas las plataformas (Windows, macOS y Linux).</span><span class="sxs-lookup"><span data-stu-id="71aa7-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="71aa7-106">Puede usar Visual Studio Code en Windows con PowerShell versión 5 a través de Windows 10 o mediante la instalación de [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) para sistemas operativos Windows inferiores (por ejemplo, Windows 8.1, etc).</span><span class="sxs-lookup"><span data-stu-id="71aa7-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="71aa7-107">Antes de iniciarlo, asegúrese de que tiene PowerShell en el sistema.</span><span class="sxs-lookup"><span data-stu-id="71aa7-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="71aa7-108">Para cargas de trabajo modernas de Windows, macOS y Linux, vea:</span><span class="sxs-lookup"><span data-stu-id="71aa7-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="71aa7-109">[Instalación de PowerShell Core en Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="71aa7-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="71aa7-110">[Instalación de PowerShell Core en macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="71aa7-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="71aa7-111">[Instalación de PowerShell Core en Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="71aa7-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="71aa7-112">Para las cargas de trabajo de Windows PowerShell tradicionales, vea [Instalación de Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="71aa7-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="71aa7-113">Edición con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="71aa7-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="71aa7-114">1. Instalación de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="71aa7-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="71aa7-115">**Linux**: siga las instrucciones de instalación de la página [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) (Ejecución de VS Code en Linux).</span><span class="sxs-lookup"><span data-stu-id="71aa7-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="71aa7-116">**macOS**: siga las instrucciones de instalación de la página [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) (Ejecución de VS Code en macOS).</span><span class="sxs-lookup"><span data-stu-id="71aa7-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="71aa7-117">En macOS, debe instalar OpenSSL para que la extensión de PowerShell funcione correctamente.</span><span class="sxs-lookup"><span data-stu-id="71aa7-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="71aa7-118">La manera más fácil de hacerlo consiste en instalar [Homebrew](https://brew.sh/) y ejecutar `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="71aa7-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="71aa7-119">Ahora VS Code puede cargar la extensión de PowerShell correctamente.</span><span class="sxs-lookup"><span data-stu-id="71aa7-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="71aa7-120">**Windows**: siga las instrucciones de instalación de la página [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) (Ejecución de VS Code en Windows).</span><span class="sxs-lookup"><span data-stu-id="71aa7-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="71aa7-121">2. Instalación de la extensión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="71aa7-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="71aa7-122">Inicie la aplicación de Visual Studio Code. Para ello, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="71aa7-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="71aa7-123">**Windows**: escriba `code` en la sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71aa7-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="71aa7-124">**Linux**: escriba `code` en el terminal.</span><span class="sxs-lookup"><span data-stu-id="71aa7-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="71aa7-125">**macOS**: escriba `code` en el terminal.</span><span class="sxs-lookup"><span data-stu-id="71aa7-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="71aa7-126">Inicie **Quick Open**. Para ello, presione **CTRL+P** (**Cmd+P** en Mac).</span><span class="sxs-lookup"><span data-stu-id="71aa7-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="71aa7-127">En Quick Open, escriba `ext install powershell` y presione **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="71aa7-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="71aa7-128">Se abre la vista **Extensiones** en la barra lateral.</span><span class="sxs-lookup"><span data-stu-id="71aa7-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="71aa7-129">Seleccione la extensión de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="71aa7-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="71aa7-130">Debería ver algo parecido a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="71aa7-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="71aa7-132">Haga clic en el botón **Instalar** en la extensión de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="71aa7-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="71aa7-133">Después de la instalación, se ve que el botón **Instalar** cambia a **Recargar**.</span><span class="sxs-lookup"><span data-stu-id="71aa7-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="71aa7-134">Haga clic en **Recargar**.</span><span class="sxs-lookup"><span data-stu-id="71aa7-134">Click on **Reload**.</span></span>
- <span data-ttu-id="71aa7-135">Una vez que se haya vuelto a cargar Visual Studio Code, estará listo para la edición.</span><span class="sxs-lookup"><span data-stu-id="71aa7-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="71aa7-136">Por ejemplo, para crear un archivo, haga clic en **Archivo -> Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="71aa7-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="71aa7-137">Para guardarlo, haga clic en **Archivo -> Guardar** y proporcione un nombre de archivo; por ejemplo, `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="71aa7-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="71aa7-138">Para cerrar el archivo, haga clic en "x" junto al nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="71aa7-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="71aa7-139">Para salir de Visual Studio Code, haga clic en **Archivo -> Salir**.</span><span class="sxs-lookup"><span data-stu-id="71aa7-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="71aa7-140">Instalación de la extensión de PowerShell en sistemas restringidos</span><span class="sxs-lookup"><span data-stu-id="71aa7-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="71aa7-141">Algunos sistemas se configuran de una manera que requiere que todas las firmas de código se verifiquen y, por lo tanto, requiere que los servicios del editor de PowerShell se aprueben manualmente para ejecutarse en el sistema.</span><span class="sxs-lookup"><span data-stu-id="71aa7-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="71aa7-142">Una actualización de la directiva de grupo que cambie la directiva de ejecución es una causa probable de recibir un error como este si ha instalado la extensión de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="71aa7-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="71aa7-143">Para aprobar manualmente los servicios del Editor de PowerShell y, por tanto, la extensión de PowerShell para VSCode, abra un símbolo del sistema y ejecute:</span><span class="sxs-lookup"><span data-stu-id="71aa7-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="71aa7-144">Se le preguntará si desea ejecutar software de este publicador que no es de confianza.</span><span class="sxs-lookup"><span data-stu-id="71aa7-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="71aa7-145">Escriba `R` para ejecutar el archivo.</span><span class="sxs-lookup"><span data-stu-id="71aa7-145">Type `R` to run the file.</span></span> <span data-ttu-id="71aa7-146">A continuación, abra Visual Studio Code y compruebe que la extensión de PowerShell funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="71aa7-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="71aa7-147">Si sigue teniendo problemas para comenzar, háganoslo saber en [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="71aa7-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="71aa7-148">Elección de una versión de PowerShell para usarla con la extensión</span><span class="sxs-lookup"><span data-stu-id="71aa7-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="71aa7-149">Con la instalación de PowerShell Core en paralelo con Windows PowerShell, ahora es posible usar una versión determinada de PowerShell con la extensión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71aa7-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="71aa7-150">Siga estas etapas para escolher a versão:</span><span class="sxs-lookup"><span data-stu-id="71aa7-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="71aa7-151">Abra la paleta de comandos (<kbd>Ctrl</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd> en Windows y Linux, <kbd>Cmd</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd> en macOS).</span><span class="sxs-lookup"><span data-stu-id="71aa7-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="71aa7-152">Busque "Sesión".</span><span class="sxs-lookup"><span data-stu-id="71aa7-152">Search for "Session".</span></span>
1. <span data-ttu-id="71aa7-153">Haga clic en "PowerShell: Show Session Menu" (PowerShell: Mostrar menú de sesión).</span><span class="sxs-lookup"><span data-stu-id="71aa7-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="71aa7-154">Elija en la lista la versión de PowerShell que quiere usar, por ejemplo, "PowerShell Core".</span><span class="sxs-lookup"><span data-stu-id="71aa7-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

>[!IMPORTANT]
> <span data-ttu-id="71aa7-155">Esta característica examina algunas rutas de acceso conocidas en distintos sistemas operativos para detectar las ubicaciones de instalación de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71aa7-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="71aa7-156">O PowerShell pode não ser inicialmente mostrado no menu de sessão caso você o tenha instalado em um local atípico.</span><span class="sxs-lookup"><span data-stu-id="71aa7-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="71aa7-157">Para extender el menú de la sesión, [agregue sus propias rutas de acceso personalizadas](#adding-your-own-powershell-paths-to-the-session-menu) tal como se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="71aa7-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="71aa7-158">Esta es otra forma de acceder al menú de la sesión.</span><span class="sxs-lookup"><span data-stu-id="71aa7-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="71aa7-159">Cuando se abre un archivo de PowerShell en el editor, verá un número de versión verde en la esquina inferior derecha.</span><span class="sxs-lookup"><span data-stu-id="71aa7-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="71aa7-160">Haga clic en este número de versión para acceder al menú de la sesión.</span><span class="sxs-lookup"><span data-stu-id="71aa7-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="71aa7-161">Adição dos seus caminhos do PowerSheel ao menu de sessão</span><span class="sxs-lookup"><span data-stu-id="71aa7-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="71aa7-162">É possível adicionar outros caminhos executáveis do PowerShell ao menu de sessão por meio de uma configuração do VS Code.</span><span class="sxs-lookup"><span data-stu-id="71aa7-162">You can add other PowerShell executable paths to the session menu through a VS Code setting.</span></span>

<span data-ttu-id="71aa7-163">Agregue un elemento a la lista `powershell.powerShellAdditionalExePaths` o cree la lista si no existe en su `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="71aa7-163">Add an item to the list  `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="71aa7-164">Cada item precisa ter:</span><span class="sxs-lookup"><span data-stu-id="71aa7-164">Each item must have:</span></span>

* <span data-ttu-id="71aa7-165">`exePath`: la ruta de acceso al ejecutable `pwsh` o `powershell`.</span><span class="sxs-lookup"><span data-stu-id="71aa7-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="71aa7-166">`versionName`: el texto que se mostrará en el menú de la sesión.</span><span class="sxs-lookup"><span data-stu-id="71aa7-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="71aa7-167">É possível definir a versão padrão do PowerShell a ser usada. Para isso, utilize a configuração `powershell.powerShellDefaultVersion` definindo-a como o texto exibido no menu de sessão (também conhecido como `versionName` na última configuração):</span><span class="sxs-lookup"><span data-stu-id="71aa7-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="71aa7-168">Depois de definir essa configuração, reinicie o Visual Studio Code ou use a ação "Desenvolvedor: recarregar janela" da paleta de comando para atualizar a janela atual do vscode.</span><span class="sxs-lookup"><span data-stu-id="71aa7-168">Once you've set this setting, restart Visual Studio Code or use the the "Developer: Reload Window" command pallet action to reload the current vscode window.</span></span>

<span data-ttu-id="71aa7-169">Si abre el menú de la sesión, ahora verá las versiones adicionales de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71aa7-169">If you open the session menu, you will now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="71aa7-170">Si compila PowerShell a partir del código fuente, se trata de una excelente forma de probar la compilación local de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71aa7-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="71aa7-171">Valores de configuración para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="71aa7-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="71aa7-172">Mediante los pasos del párrafo anterior, puede agregar valores de configuración en `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="71aa7-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="71aa7-173">Recomendamos los valores de configuración siguientes para Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="71aa7-173">We recommend the following configuration settings for Visual Studio Code:</span></span>

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

<span data-ttu-id="71aa7-174">Si no desea que estos ajustes afecten a todos los tipos de archivos, VSCode también permite configuraciones por idioma.</span><span class="sxs-lookup"><span data-stu-id="71aa7-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="71aa7-175">Cree un ajuste específico del lenguaje colocando los ajustes en un campo `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="71aa7-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="71aa7-176">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="71aa7-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="71aa7-177">Para obtener más información sobre la codificación de archivo en VS Code, consulte [Descripción de la codificación de archivo](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="71aa7-177">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="71aa7-178">Depuración con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="71aa7-178">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="71aa7-179">Depuración fuera del área de trabajo</span><span class="sxs-lookup"><span data-stu-id="71aa7-179">No-workspace debugging</span></span>

<span data-ttu-id="71aa7-180">A partir de Visual Studio Code versión 1.9 puede depurar scripts de PowerShell sin tener que abrir la carpeta que contiene el script de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71aa7-180">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="71aa7-181">Abra el archivo de script de PowerShell con **Archivo -> Abrir archivo…** , establezca un punto de interrupción en una línea (presione F9) y, después, presione F5 para iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="71aa7-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="71aa7-182">Aparece el panel de acciones de depuración, que le permite obtener acceso al depurador, realizar la depuración paso a paso, reanudarla y detenerla.</span><span class="sxs-lookup"><span data-stu-id="71aa7-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="71aa7-183">Depuración del área de trabajo</span><span class="sxs-lookup"><span data-stu-id="71aa7-183">Workspace debugging</span></span>

<span data-ttu-id="71aa7-184">La depuración del área de trabajo hace referencia a la depuración en el contexto de una carpeta que se ha abierto en Visual Studio Code mediante **Abrir carpeta…** desde el menú **Archivo**.</span><span class="sxs-lookup"><span data-stu-id="71aa7-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="71aa7-185">Suele tratarse de la carpeta del proyecto de PowerShell o la raíz del repositorio de Git.</span><span class="sxs-lookup"><span data-stu-id="71aa7-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="71aa7-186">Incluso en este modo, para empezar a depurar el script de PowerShell seleccionado, basta con presionar F5.</span><span class="sxs-lookup"><span data-stu-id="71aa7-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="71aa7-187">La depuración del área de trabajo no se limita a depurar el archivo abierto actualmente, sino que permite definir diversas configuraciones de depuración.</span><span class="sxs-lookup"><span data-stu-id="71aa7-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="71aa7-188">Por ejemplo, puede agregar configuraciones para:</span><span class="sxs-lookup"><span data-stu-id="71aa7-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="71aa7-189">Iniciar pruebas de Pester en el depurador</span><span class="sxs-lookup"><span data-stu-id="71aa7-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="71aa7-190">Iniciar un archivo específico con argumentos en el depurador</span><span class="sxs-lookup"><span data-stu-id="71aa7-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="71aa7-191">Iniciar una sesión interactiva en el depurador</span><span class="sxs-lookup"><span data-stu-id="71aa7-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="71aa7-192">Asociar el depurador a un proceso de host de PowerShell</span><span class="sxs-lookup"><span data-stu-id="71aa7-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="71aa7-193">Siga los pasos siguientes para crear el archivo de configuración de depuración:</span><span class="sxs-lookup"><span data-stu-id="71aa7-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="71aa7-194">Abra la vista **Depurar**. Para ello, presione **Ctrl+Mayús+D** (**Cmd+Mayús+ D** en Mac).</span><span class="sxs-lookup"><span data-stu-id="71aa7-194">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="71aa7-195">Presione el icono de engranaje **Configurar** en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="71aa7-195">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="71aa7-196">Visual Studio Code le solicita que **seleccione un entorno**.</span><span class="sxs-lookup"><span data-stu-id="71aa7-196">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="71aa7-197">Elija **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="71aa7-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="71aa7-198">Cuando lo haga, Visual Studio Code creará un directorio y un archivo ".vscode\launch.json" en la raíz de la carpeta del área de trabajo.</span><span class="sxs-lookup"><span data-stu-id="71aa7-198">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="71aa7-199">Aquí es donde se almacenará la configuración de depuración.</span><span class="sxs-lookup"><span data-stu-id="71aa7-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="71aa7-200">Si los archivos están en un repositorio de Git, normalmente le interesa confirmar el archivo launch.json.</span><span class="sxs-lookup"><span data-stu-id="71aa7-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="71aa7-201">El contenido del archivo launch.json es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="71aa7-201">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="71aa7-202">Esto representa los escenarios de depuración comunes.</span><span class="sxs-lookup"><span data-stu-id="71aa7-202">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="71aa7-203">Aun así, cuando se abre este archivo en el editor, se ve el botón **Agregar configuración…** .</span><span class="sxs-lookup"><span data-stu-id="71aa7-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="71aa7-204">Puede presionar este botón para agregar más configuraciones de depuración de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71aa7-204">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="71aa7-205">Una configuración muy útil que conviene agregar es **PowerShell: Iniciar Script**.</span><span class="sxs-lookup"><span data-stu-id="71aa7-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="71aa7-206">Con esta configuración, puede especificar un archivo concreto con argumentos opcionales que se debe iniciar cada vez que se presione F5, independientemente del archivo que esté activo en el momento en el editor.</span><span class="sxs-lookup"><span data-stu-id="71aa7-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="71aa7-207">Una vez establecida la configuración de depuración, puede seleccionar la configuración que quiere usar durante una sesión de depuración. Para ello, selecciónela en el menú desplegable de la barra de herramientas de la vista **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="71aa7-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="71aa7-208">Algunos blogs pueden servirle de ayuda para empezar a usar la extensión de PowerShell para Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="71aa7-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="71aa7-209">[Extensión de PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="71aa7-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="71aa7-210">[Escritura y depuración de scripts de PowerShell en Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="71aa7-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="71aa7-211">[Instrucciones de depuración de Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="71aa7-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="71aa7-212">[Depuración de PowerShell en Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="71aa7-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="71aa7-213">[Introducción al desarrollo de PowerShell en Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="71aa7-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="71aa7-214">[Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="71aa7-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="71aa7-215">[Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="71aa7-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="71aa7-216">[Depuración de scripts de PowerShell en Visual Studio Code, parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="71aa7-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="71aa7-217">[Depuración de scripts de PowerShell en Visual Studio Code, parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="71aa7-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="71aa7-218">Extensión de PowerShell para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="71aa7-218">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="71aa7-219">Encontrará en [GitHub](https://github.com/PowerShell/vscode-powershell) el código fuente de la extensión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71aa7-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
