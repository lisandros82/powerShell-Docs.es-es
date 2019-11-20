---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Cómo escribir y ejecutar scripts en Windows PowerShell ISE
ms.openlocfilehash: be54e26965a6d2f1472059820080a6a06c47dd26
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117557"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="985eb-103">Cómo escribir y ejecutar scripts en Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="985eb-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="985eb-104">En este artículo se describe cómo crear, editar, ejecutar y guardar scripts en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="985eb-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="985eb-105">Cómo crear y ejecutar scripts</span><span class="sxs-lookup"><span data-stu-id="985eb-105">How to create and run scripts</span></span>

<span data-ttu-id="985eb-106">Puede abrir y editar archivos de Windows PowerShell en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="985eb-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="985eb-107">Los tipos de archivo de interés específicos de Windows PowerShell son los archivos de script (.ps1), los archivos de datos de script (.psd1) y los archivos de módulo de script (.psm1).</span><span class="sxs-lookup"><span data-stu-id="985eb-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="985eb-108">Estos tipos de archivo presentan color de sintaxis en el editor de panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="985eb-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="985eb-109">Otros tipos de archivo comunes que puede abrir en el panel de scripts son los archivos de configuración (.ps1xml), los archivos XML y los archivos de texto.</span><span class="sxs-lookup"><span data-stu-id="985eb-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="985eb-110">La directiva de ejecución de Windows PowerShell determina si puede ejecutar scripts y cargar archivos de configuración y perfiles de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="985eb-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="985eb-111">La directiva de ejecución predeterminada, Restricted, impide que se ejecuten todos los scripts y que se carguen perfiles.</span><span class="sxs-lookup"><span data-stu-id="985eb-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="985eb-112">Para cambiar la directiva de ejecución a fin de permitir cargar y usar perfiles, consulte [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) y [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="985eb-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="985eb-113">Para crear un nuevo archivo de script</span><span class="sxs-lookup"><span data-stu-id="985eb-113">To create a new script file</span></span>

<span data-ttu-id="985eb-114">En la barra de herramientas, haga clic en **Nuevo**, o bien, en el menú **Archivo**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="985eb-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="985eb-115">El archivo creado aparece en una nueva pestaña de archivo en la ficha actual de PowerShell. Recuerde que las pestañas de PowerShell solo están visibles cuando hay más de una.</span><span class="sxs-lookup"><span data-stu-id="985eb-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="985eb-116">De forma predeterminada, se crea un archivo de tipo script (.ps1), pero se puede guardar con un nombre y una extensión diferentes.</span><span class="sxs-lookup"><span data-stu-id="985eb-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="985eb-117">Se pueden crear varios archivos de script en la misma pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="985eb-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="985eb-118">Para abrir un script existente</span><span class="sxs-lookup"><span data-stu-id="985eb-118">To open an existing script</span></span>

<span data-ttu-id="985eb-119">En la barra de herramientas, haga clic en **Abrir**, o bien, en el menú **Archivo**, haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="985eb-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="985eb-120">En el cuadro de diálogo **Abrir**, seleccione el archivo que quiera abrir.</span><span class="sxs-lookup"><span data-stu-id="985eb-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="985eb-121">El archivo abierto aparece en una nueva pestaña.</span><span class="sxs-lookup"><span data-stu-id="985eb-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="985eb-122">Para cerrar una pestaña de script</span><span class="sxs-lookup"><span data-stu-id="985eb-122">To close a script tab</span></span>

<span data-ttu-id="985eb-123">Haga clic en el icono **Cerrar** (X) de la pestaña del archivo que desea cerrar o bien seleccione el menú **Archivo** y haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="985eb-123">Click the **Close** icon (X) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="985eb-124">Si el archivo se ha modificado desde que se guardó por última vez, se le preguntará si desea guardar o descartar los cambios.</span><span class="sxs-lookup"><span data-stu-id="985eb-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="985eb-125">Para mostrar la ruta de acceso del archivo</span><span class="sxs-lookup"><span data-stu-id="985eb-125">To display the file path</span></span>

<span data-ttu-id="985eb-126">En la pestaña del archivo, señale el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="985eb-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="985eb-127">La ruta de acceso completa al archivo de script se muestra en una información sobre herramientas.</span><span class="sxs-lookup"><span data-stu-id="985eb-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="985eb-128">Para ejecutar un script</span><span class="sxs-lookup"><span data-stu-id="985eb-128">To run a script</span></span>

<span data-ttu-id="985eb-129">En la barra de herramientas, haga clic en **Ejecutar script**, o bien, en el menú **Archivo**, haga clic en **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="985eb-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="985eb-130">Para ejecutar parte de un script</span><span class="sxs-lookup"><span data-stu-id="985eb-130">To run a portion of a script</span></span>

1. <span data-ttu-id="985eb-131">En el panel de scripts, seleccione una parte de un script.</span><span class="sxs-lookup"><span data-stu-id="985eb-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="985eb-132">En el menú **Archivo**, haga clic en **Ejecutar selección**, o bien haga clic en **Ejecutar selección** en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="985eb-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="985eb-133">Para detener un script que se está ejecutando</span><span class="sxs-lookup"><span data-stu-id="985eb-133">To stop a running script</span></span>

<span data-ttu-id="985eb-134">Hay varias maneras para detener un script en ejecución.</span><span class="sxs-lookup"><span data-stu-id="985eb-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="985eb-135">Haga clic en **Detener operación** en la barra de herramientas</span><span class="sxs-lookup"><span data-stu-id="985eb-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="985eb-136">Presione CTRL + INTER.</span><span class="sxs-lookup"><span data-stu-id="985eb-136">Press CTRL+BREAK</span></span>
- <span data-ttu-id="985eb-137">Seleccione el menú **Archivo** y haga clic en **Detener operación**.</span><span class="sxs-lookup"><span data-stu-id="985eb-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="985eb-138">Presionar **CTRL+C** también funciona a menos que ya haya texto seleccionado, en cuyo caso **CTRL+C** se asigna a la función de copia del texto seleccionado.</span><span class="sxs-lookup"><span data-stu-id="985eb-138">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="985eb-139">Cómo escribir y editar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="985eb-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="985eb-140">Puede copiar, cortar, pegar, buscar y reemplazar texto en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="985eb-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="985eb-141">También puede deshacer y rehacer la última acción que ha realizado.</span><span class="sxs-lookup"><span data-stu-id="985eb-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="985eb-142">Los métodos abreviados de teclado para estas acciones son los mismos que los usados para todas las aplicaciones de Windows.</span><span class="sxs-lookup"><span data-stu-id="985eb-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="985eb-143">Para escribir texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="985eb-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="985eb-144">Mueva el cursor al panel de scripts haciendo clic en cualquier lugar del panel de scripts o en **Ir al panel de scripts** en el menú **Ver**.</span><span class="sxs-lookup"><span data-stu-id="985eb-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="985eb-145">Cree un script.</span><span class="sxs-lookup"><span data-stu-id="985eb-145">Create a script.</span></span> <span data-ttu-id="985eb-146">El color de sintaxis y la finalización con tabulación proporcionan una experiencia de edición más rica en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="985eb-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="985eb-147">Vea [Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obtener más información sobre el uso de la característica de finalización de con tabulación para facilitar la escritura.</span><span class="sxs-lookup"><span data-stu-id="985eb-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="985eb-148">Para buscar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="985eb-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="985eb-149">Para buscar texto en cualquier lugar, presione **CTRL+F** o, en el menú **Edición**, haga clic en **Buscar en el script**.</span><span class="sxs-lookup"><span data-stu-id="985eb-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="985eb-150">Para buscar texto después del cursor, presione **F3** o, en el menú **Edición**, haga clic en **Buscar siguiente en el script**.</span><span class="sxs-lookup"><span data-stu-id="985eb-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="985eb-151">Para buscar texto antes del cursor, presione **MAYÚS+F3** o, en el menú **Edición**, haga clic en **Buscar anterior en el script**.</span><span class="sxs-lookup"><span data-stu-id="985eb-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="985eb-152">Para buscar y reemplazar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="985eb-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="985eb-153">Presione **CRTL+H** o, en el menú **Edición**, haga clic en **Replace in Script** (Reemplazar en script).</span><span class="sxs-lookup"><span data-stu-id="985eb-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="985eb-154">Escriba el texto que desea encontrar y el texto de reemplazo y, después, presione **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="985eb-154">Enter the text you want to find and the replacement text, then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="985eb-155">Para ir a una línea determinada de texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="985eb-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="985eb-156">En el panel de scripts, presione **CTRL+G** o, en el menú **Edición**, haga clic en **Ir a la línea**.</span><span class="sxs-lookup"><span data-stu-id="985eb-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="985eb-157">Escriba un número de línea.</span><span class="sxs-lookup"><span data-stu-id="985eb-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="985eb-158">Para copiar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="985eb-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="985eb-159">En el panel de scripts, seleccione el texto que desee copiar.</span><span class="sxs-lookup"><span data-stu-id="985eb-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="985eb-160">Presione **CTRL+C** o haga clic en el icono **Copiar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="985eb-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="985eb-161">Para cortar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="985eb-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="985eb-162">En el panel de scripts, seleccione el texto que desee cortar.</span><span class="sxs-lookup"><span data-stu-id="985eb-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="985eb-163">Presione **CTRL+X** o haga clic en el icono **Cortar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Cortar**.</span><span class="sxs-lookup"><span data-stu-id="985eb-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="985eb-164">Para pegar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="985eb-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="985eb-165">Presione **CTRL+V** o haga clic en el icono **Pegar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Pegar**.</span><span class="sxs-lookup"><span data-stu-id="985eb-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="985eb-166">Para deshacer una acción en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="985eb-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="985eb-167">Presione **CTRL+Z** o haga clic en el icono **Deshacer** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Deshacer**.</span><span class="sxs-lookup"><span data-stu-id="985eb-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="985eb-168">Para rehacer una acción en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="985eb-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="985eb-169">Presione **CTRL+Y** o haga clic en el icono **Rehacer** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Rehacer**.</span><span class="sxs-lookup"><span data-stu-id="985eb-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="985eb-170">Cómo guardar un script</span><span class="sxs-lookup"><span data-stu-id="985eb-170">How to save a script</span></span>

<span data-ttu-id="985eb-171">Aparece un asterisco junto al nombre del script para marcar un archivo que no se ha guardado desde que se modificó.</span><span class="sxs-lookup"><span data-stu-id="985eb-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="985eb-172">El asterisco desaparecerá cuando se guarda el archivo.</span><span class="sxs-lookup"><span data-stu-id="985eb-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="985eb-173">Para guardar un script</span><span class="sxs-lookup"><span data-stu-id="985eb-173">To save a script</span></span>

<span data-ttu-id="985eb-174">Presione **CTRL+S** o haga clic en el icono **Guardar** de la barra de herramientas. O bien, en el menú **Archivo**, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="985eb-174">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="985eb-175">Para guardar un script y asignarle un nombre</span><span class="sxs-lookup"><span data-stu-id="985eb-175">To save and name a script</span></span>

1. <span data-ttu-id="985eb-176">En el menú **Archivo**, haga clic en **Guardar como**.</span><span class="sxs-lookup"><span data-stu-id="985eb-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="985eb-177">Se abre el cuadro de diálogo **Guardar como**.</span><span class="sxs-lookup"><span data-stu-id="985eb-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="985eb-178">En el cuadro **Nombre de archivo**, escriba un nombre para el archivo.</span><span class="sxs-lookup"><span data-stu-id="985eb-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="985eb-179">En el cuadro **Guardar como tipo**, seleccione un tipo de archivo.</span><span class="sxs-lookup"><span data-stu-id="985eb-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="985eb-180">Por ejemplo, en el cuadro **Guardar como tipo**, seleccione “Scripts de PowerShell (\*.ps1)”.</span><span class="sxs-lookup"><span data-stu-id="985eb-180">For example, in the **Save as type** box, select 'PowerShell Scripts (\*.ps1)'.</span></span>
4. <span data-ttu-id="985eb-181">Haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="985eb-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="985eb-182">Para guardar un script en la codificación ASCII</span><span class="sxs-lookup"><span data-stu-id="985eb-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="985eb-183">De forma predeterminada, Windows PowerShell ISE guarda los nuevos archivos de script (.ps1), los archivos de datos de script (.psd1) y los archivos de módulo de script (.psm1) como Unicode (BigEndianUnicode). Para guardar un script en otra codificación, como ASCII (ANSI), use los métodos **Save** o **SaveAs** en el objeto [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="985eb-183">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="985eb-184">El siguiente comando guarda un nuevo script como MyScript.ps1 con la codificación ASCII.</span><span class="sxs-lookup"><span data-stu-id="985eb-184">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="985eb-185">El siguiente comando reemplaza el archivo de script actual con un archivo con el mismo nombre, pero con la codificación ASCII.</span><span class="sxs-lookup"><span data-stu-id="985eb-185">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="985eb-186">El comando siguiente obtiene la codificación del archivo actual.</span><span class="sxs-lookup"><span data-stu-id="985eb-186">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="985eb-187">Windows PowerShell ISE admite las siguientes opciones de codificación: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 y Default.</span><span class="sxs-lookup"><span data-stu-id="985eb-187">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="985eb-188">El valor de la opción predeterminada varía según el sistema.</span><span class="sxs-lookup"><span data-stu-id="985eb-188">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="985eb-189">Windows PowerShell ISE no cambia la codificación de los archivos de script cuando se usan los comandos Guardar o Guardar como.</span><span class="sxs-lookup"><span data-stu-id="985eb-189">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="985eb-190">Véase también</span><span class="sxs-lookup"><span data-stu-id="985eb-190">See Also</span></span>

- [<span data-ttu-id="985eb-191">Explorar Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="985eb-191">Exploring the Windows PowerShell ISE</span></span>](exploring-the-windows-powershell-ise.md)
