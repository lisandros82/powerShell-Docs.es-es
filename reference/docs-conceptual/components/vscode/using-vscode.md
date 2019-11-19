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
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="9cf5c-103">Uso de Visual Studio Code para el desarrollo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9cf5c-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="9cf5c-104">Además de [PowerShell ISE][ise], PowerShell también se admite en Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="9cf5c-105">El ISE no es compatible con PowerShell Core, pero VSCode es compatible con PowerShell Core en todas las plataformas: Windows, macOS y Linux.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-105">The ISE isn't supported with PowerShell Core, but VSCode is supported for PowerShell Core on all platforms: Windows, macOS, and Linux.</span></span>

<span data-ttu-id="9cf5c-106">Puede usar VSCode en Windows con la versión 5 de PowerShell mediante Windows 10 o la instalación de Windows Management Framework 5.1 para sistemas operativos Windows de nivel inferior, como Windows 8.1.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing Windows Management Framework 5.1 for down-level Windows OSs such as Windows 8.1.</span></span> <span data-ttu-id="9cf5c-107">Para más información, consulte [Instalación y configuración de WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-107">For more information, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>

<span data-ttu-id="9cf5c-108">Antes de empezar, asegúrese de que PowerShell existe en el sistema.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-108">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="9cf5c-109">Para cargas de trabajo modernas de Windows, macOS y Linux, consulte los siguientes vínculos:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-109">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="9cf5c-110">[Instalación de PowerShell Core en Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-110">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="9cf5c-111">[Instalación de PowerShell Core en macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-111">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="9cf5c-112">[Instalación de PowerShell Core en Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-112">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="9cf5c-113">Para las cargas de trabajo de Windows PowerShell tradicionales, vea [Instalación de Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="9cf5c-113">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="9cf5c-114">Edición con VSCode</span><span class="sxs-lookup"><span data-stu-id="9cf5c-114">Editing with VSCode</span></span>

1. <span data-ttu-id="9cf5c-115">Instale VSCode.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-115">Install VSCode.</span></span> <span data-ttu-id="9cf5c-116">Para más información, consulte la información general que se describe en [Configuración de Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-116">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

   <span data-ttu-id="9cf5c-117">Hay instrucciones de instalación para cada plataforma:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-117">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="9cf5c-118">**Linux**: siga las instrucciones de instalación de la página [Ejecución de VSCode en Linux](https://code.visualstudio.com/docs/setup/linux).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-118">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>
   - <span data-ttu-id="9cf5c-119">**macOS**: siga las instrucciones de instalación de la página [Ejecución de VSCode en macOS](https://code.visualstudio.com/docs/setup/mac).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-119">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="9cf5c-120">En macOS, debe instalar OpenSSL para que la extensión de PowerShell funcione correctamente.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-120">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="9cf5c-121">La manera más fácil de hacerlo consiste en instalar [Homebrew](https://brew.sh/) y ejecutar `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-121">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="9cf5c-122">Ahora VSCode puede cargar la extensión de PowerShell correctamente.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-122">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="9cf5c-123">**Windows**: siga las instrucciones de instalación de la página [Ejecución de VSCode en Windows](https://code.visualstudio.com/docs/setup/windows).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-123">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>

1. <span data-ttu-id="9cf5c-124">Instale la extensión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-124">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="9cf5c-125">Inicie la aplicación VSCode de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-125">Launch the VSCode app by:</span></span>
      - <span data-ttu-id="9cf5c-126">**Windows**: escriba `code` en la sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-126">**Windows**: typing `code` in your PowerShell session</span></span>
      - <span data-ttu-id="9cf5c-127">**Linux**: escriba `code` en el terminal.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-127">**Linux**: typing `code` in your terminal</span></span>
      - <span data-ttu-id="9cf5c-128">**macOS**: escriba `code` en el terminal.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-128">**macOS**: typing `code` in your terminal</span></span>
   1. <span data-ttu-id="9cf5c-129">Inicie **Quick Open** en Windows o Linux; para ello, presione <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-129">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="9cf5c-130">En macOS, presione <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-130">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="9cf5c-131">En Quick Open, escriba `ext install powershell` y presione **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-131">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="9cf5c-132">Se abre la vista **Extensiones** en la barra lateral.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-132">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="9cf5c-133">Seleccione la extensión de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-133">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="9cf5c-134">Verá una pantalla de VSCode similar a la siguiente imagen:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-134">You should see a VSCode screen similar to the following image:</span></span>

      ![VSCode](../../images/using-vscode/vscode.png)

   1. <span data-ttu-id="9cf5c-136">Haga clic en el botón **Instalar** en la extensión de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-136">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="9cf5c-137">Después de la instalación, se ve que el botón **Instalar** cambia a **Recargar**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-137">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="9cf5c-138">Haga clic en **Recargar**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-138">Click on **Reload**.</span></span>
   1. <span data-ttu-id="9cf5c-139">Una vez que se haya vuelto a cargar VSCode, estará listo para la edición.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-139">After VSCode has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="9cf5c-140">Por ejemplo, para crear un archivo, haga clic en **Archivo -> Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="9cf5c-141">Para guardarlo, haga clic en **Archivo -> Guardar** y proporcione un nombre de archivo, por ejemplo, `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="9cf5c-142">Para cerrar el archivo, haga clic en la `X` junto al nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="9cf5c-143">Para salir de VSCode, **Archivo->Salir**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-143">To exit VSCode, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="9cf5c-144">Instalación de la extensión de PowerShell en sistemas restringidos</span><span class="sxs-lookup"><span data-stu-id="9cf5c-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="9cf5c-145">Algunos sistemas están configurados de tal manera que se requiere la comprobación de todas las firmas de código y la aprobación manual de los servicios del editor de PowerShell para ejecutarse en el sistema.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="9cf5c-146">Una de las causas probables de que haya instalado la extensión de PowerShell pero reciba un error como el siguiente es la actualización de una directiva de grupo que cambia la directiva de ejecución:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="9cf5c-147">Para aprobar manualmente los servicios del editor de PowerShell y la extensión de PowerShell para VSCode, abra un símbolo del sistema y ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-147">To manually approve PowerShell Editor Services and the PowerShell extension for VSCode, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="9cf5c-148">Se le preguntará si desea ejecutar software de este editor que no es de confianza.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="9cf5c-149">Escriba `A` para ejecutar el archivo.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-149">Type `A` to run the file.</span></span> <span data-ttu-id="9cf5c-150">A continuación, abra VSCode y compruebe que la extensión de PowerShell funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-150">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="9cf5c-151">Si sigue teniendo problemas para comenzar, háganoslo saber en [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="9cf5c-152">Elección de una versión de PowerShell para usarla con la extensión</span><span class="sxs-lookup"><span data-stu-id="9cf5c-152">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="9cf5c-153">Con la instalación de PowerShell Core en paralelo con Windows PowerShell, ahora es posible usar una versión determinada de PowerShell con la extensión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-153">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="9cf5c-154">Use estos pasos para elegir la versión:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-154">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="9cf5c-155">Abra la **paleta de comandos** en Windows o Linux con <kbd>Ctrl</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-155">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="9cf5c-156">En macOS, use <kbd>Cmd</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-156">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="9cf5c-157">Busque **Sesión**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-157">Search for **Session**.</span></span>
1. <span data-ttu-id="9cf5c-158">Haga clic en **PowerShell: Show Session Menu** (PowerShell: Mostrar menú de sesión).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-158">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="9cf5c-159">En la lista, elija la versión de PowerShell que quiere usar, por ejemplo: **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-159">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9cf5c-160">Esta característica examina algunas rutas de acceso conocidas en distintos sistemas operativos para detectar las ubicaciones de instalación de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-160">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="9cf5c-161">O PowerShell pode não ser inicialmente mostrado no menu de sessão caso você o tenha instalado em um local atípico.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-161">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="9cf5c-162">Para extender el menú de la sesión, [agregue sus propias rutas de acceso personalizadas](#adding-your-own-powershell-paths-to-the-session-menu) tal como se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-162">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="9cf5c-163">Hay otra forma de acceder al menú de la sesión.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-163">There's another way to get to the session menu.</span></span> <span data-ttu-id="9cf5c-164">Cuando se abre un archivo de PowerShell en el editor, verá un número de versión verde en la esquina inferior derecha.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-164">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="9cf5c-165">Haga clic en este número de versión para acceder al menú de la sesión.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-165">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="9cf5c-166">Adición de rutas de acceso propias de PowerShell al menú de sesión</span><span class="sxs-lookup"><span data-stu-id="9cf5c-166">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="9cf5c-167">Puede agregar otras rutas de acceso ejecutables de PowerShell al menú de sesión mediante una configuración de VSCode.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-167">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="9cf5c-168">Agregue un elemento a la lista `powershell.powerShellAdditionalExePaths` o cree la lista si no existe en su `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-168">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="9cf5c-169">Cada elemento debe tener:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-169">Each item must have:</span></span>

* <span data-ttu-id="9cf5c-170">`exePath`: la ruta de acceso al ejecutable `pwsh` o `powershell`.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-170">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="9cf5c-171">`versionName`: el texto que se mostrará en el menú de la sesión.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-171">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="9cf5c-172">Puede establecer la versión de PowerShell predeterminada para usar el valor `powershell.powerShellDefaultVersion`; para ello, configúrela con el texto que se muestra en el menú de sesión (también conocido como `versionName` en el último valor).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-172">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="9cf5c-173">Después de configurar este valor, reinicie VSCode o vuelva a cargar la ventana actual de VSCode desde la **paleta de comandos** y escriba **Desarrollador: Recargar ventana**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-173">After you've configured this setting, restart VSCode or to reload the current VSCode window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="9cf5c-174">Si abre el menú de la sesión, ahora verá las versiones adicionales de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-174">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="9cf5c-175">Si compila PowerShell a partir del código fuente, se trata de una excelente forma de probar la compilación local de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-175">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="9cf5c-176">Valores de configuración de VSCode</span><span class="sxs-lookup"><span data-stu-id="9cf5c-176">Configuration settings for VSCode</span></span>

<span data-ttu-id="9cf5c-177">Mediante los pasos del párrafo anterior, puede agregar valores de configuración en `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-177">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="9cf5c-178">Recomendamos los valores de configuración siguientes para VSCode:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-178">We recommend the following configuration settings for VSCode:</span></span>

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

<span data-ttu-id="9cf5c-179">Si no desea que estos ajustes afecten a todos los tipos de archivos, VSCode también permite configuraciones por idioma.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-179">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="9cf5c-180">Cree un ajuste específico del lenguaje colocando los ajustes en un campo `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-180">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="9cf5c-181">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-181">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="9cf5c-182">Para obtener más información sobre la codificación de archivo en VSCode, vea [Descripción de la codificación de archivo](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="9cf5c-182">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="9cf5c-183">Depuración con VSCode</span><span class="sxs-lookup"><span data-stu-id="9cf5c-183">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="9cf5c-184">Depuración fuera del área de trabajo</span><span class="sxs-lookup"><span data-stu-id="9cf5c-184">No-workspace debugging</span></span>

<span data-ttu-id="9cf5c-185">A partir de VSCode versión 1.9 puede depurar scripts de PowerShell sin tener que abrir la carpeta que los contiene.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-185">As of VSCode version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="9cf5c-186">Abra el archivo de script de PowerShell con **Archivo -> Abrir archivo…** , establezca un punto de interrupción en una línea, presione <kbd>F9</kbd> y, después, presione <kbd>F5</kbd> para iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-186">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="9cf5c-187">Verá que aparece el panel de acciones de depuración, que le permite iniciar el depurador, realizar la depuración paso a paso, reanudarla y detenerla.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-187">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="9cf5c-188">Depuración del área de trabajo</span><span class="sxs-lookup"><span data-stu-id="9cf5c-188">Workspace debugging</span></span>

<span data-ttu-id="9cf5c-189">La depuración del área de trabajo hace referencia a la depuración en el contexto de una carpeta que se ha abierto en Visual Studio Code desde el menú **Archivo** mediante **Abrir carpeta...** . Suele tratarse de la carpeta del proyecto de PowerShell o la raíz del repositorio de Git.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-189">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="9cf5c-190">Incluso en este modo, para empezar a depurar el script de PowerShell seleccionado, presione <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-190">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="9cf5c-191">La depuración del área de trabajo no se limita a depurar el archivo abierto actualmente, sino que permite definir diversas configuraciones de depuración.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-191">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="9cf5c-192">Por ejemplo, puede agregar configuraciones para:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-192">For instance, you can add a configuration to:</span></span>

- <span data-ttu-id="9cf5c-193">Iniciar pruebas de Pester en el depurador</span><span class="sxs-lookup"><span data-stu-id="9cf5c-193">Launch Pester tests in the debugger.</span></span>
- <span data-ttu-id="9cf5c-194">Iniciar un archivo específico con argumentos en el depurador</span><span class="sxs-lookup"><span data-stu-id="9cf5c-194">Launch a specific file with arguments in the debugger.</span></span>
- <span data-ttu-id="9cf5c-195">Iniciar una sesión interactiva en el depurador</span><span class="sxs-lookup"><span data-stu-id="9cf5c-195">Launch an interactive session in the debugger.</span></span>
- <span data-ttu-id="9cf5c-196">Asociar el depurador a un proceso de host de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-196">Attach the debugger to a PowerShell host process.</span></span>

<span data-ttu-id="9cf5c-197">Siga los pasos siguientes para crear el archivo de configuración de depuración:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-197">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="9cf5c-198">Abra la vista **Depurar** en Windows o Linux con <kbd>Ctrl</kbd>+<kbd>Mayús</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-198">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="9cf5c-199">En macOS, presione <kbd>Cmd</kbd>+<kbd>Mayús</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-199">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="9cf5c-200">Haga clic en el icono de engranaje **Configurar** en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-200">Click the **Configure** gear icon in the toolbar.</span></span>
  1. <span data-ttu-id="9cf5c-201">VSCode le solicita que **seleccione un entorno**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-201">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="9cf5c-202">Elija **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-202">Choose **PowerShell**.</span></span>

<span data-ttu-id="9cf5c-203">El resultado es que VSCode crea un directorio y un archivo `.vscode\launch.json` en la raíz de la carpeta del área de trabajo.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-203">The result is that VSCode creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="9cf5c-204">En esta ubicación es donde se almacena la configuración de depuración.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-204">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="9cf5c-205">Si los archivos están en un repositorio de Git, lo normal es que le interese confirmar el archivo `launch.json`.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-205">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="9cf5c-206">El contenido del archivo `launch.json` es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-206">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="9cf5c-207">Este archivo representa los escenarios de depuración comunes.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-207">This file represents the common debug scenarios.</span></span> <span data-ttu-id="9cf5c-208">Cuando abra este archivo en el editor, verá un botón **Agregar configuración…** .</span><span class="sxs-lookup"><span data-stu-id="9cf5c-208">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="9cf5c-209">Puede hacer clic en este botón para agregar más configuraciones de depuración de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-209">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="9cf5c-210">Una configuración muy útil que conviene agregar es **PowerShell: Iniciar Script**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-210">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="9cf5c-211">Con esta configuración, puede especificar un archivo con argumentos opcionales que se iniciará cada vez que se presione <kbd>F5</kbd>, con independencia del archivo que esté activo en el momento en el editor.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-211">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="9cf5c-212">Una vez establecida la configuración de depuración, puede seleccionar qué configuración quiere usar durante una sesión de depuración.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-212">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="9cf5c-213">Seleccione una configuración de la lista desplegable de configuraciones de depuración en la barra de herramientas de la vista **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-213">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="9cf5c-214">Algunos blogs pueden servirle de ayuda para empezar a usar la extensión de PowerShell para Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="9cf5c-214">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="9cf5c-215">[Extensión de PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-215">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="9cf5c-216">[Escritura y depuración de scripts de PowerShell en Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-216">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="9cf5c-217">[Instrucciones de depuración de Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-217">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="9cf5c-218">[Depuración de PowerShell en Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-218">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="9cf5c-219">[Introducción al desarrollo de PowerShell en Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-219">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="9cf5c-220">[Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-220">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="9cf5c-221">[Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-221">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="9cf5c-222">[Depuración de scripts de PowerShell en Visual Studio Code, parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-222">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="9cf5c-223">[Depuración de scripts de PowerShell en Visual Studio Code, parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="9cf5c-223">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="9cf5c-224">Extensión de PowerShell para VSCode</span><span class="sxs-lookup"><span data-stu-id="9cf5c-224">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="9cf5c-225">Encontrará en [GitHub](https://github.com/PowerShell/vscode-powershell) el código fuente de la extensión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9cf5c-225">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
