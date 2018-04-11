---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Cómo escribir y ejecutar scripts en Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 4b8a9c0c3a710f3b3b9b6077c3c84e174a141db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="b053c-103">Cómo escribir y ejecutar scripts en Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b053c-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="b053c-104">En este tema se describe cómo crear, editar, ejecutar y guardar scripts en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="b053c-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="b053c-105">Cómo crear y ejecutar scripts</span><span class="sxs-lookup"><span data-stu-id="b053c-105">How to create and run scripts</span></span>

<span data-ttu-id="b053c-106">Puede abrir y editar archivos de Windows PowerShell en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="b053c-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="b053c-107">Los tipos de archivo de interés específicos de Windows PowerShell son los archivos de script (.ps1), los archivos de datos de script (.psd1) y los archivos de módulo de script (.psm1).</span><span class="sxs-lookup"><span data-stu-id="b053c-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="b053c-108">Estos tipos de archivo presentan color de sintaxis en el editor de panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="b053c-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="b053c-109">Otros tipos de archivo comunes que puede abrir en el panel de scripts son los archivos de configuración (.ps1xml), los archivos XML y los archivos de texto.</span><span class="sxs-lookup"><span data-stu-id="b053c-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="b053c-110">La directiva de ejecución de Windows PowerShell determina si puede ejecutar scripts y cargar archivos de configuración y perfiles de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b053c-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="b053c-111">La directiva de ejecución predeterminada, Restricted, impide que se ejecuten todos los scripts y que se carguen perfiles.</span><span class="sxs-lookup"><span data-stu-id="b053c-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="b053c-112">Para cambiar la directiva de ejecución a fin de permitir cargar y usar perfiles, consulte [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) y [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span><span class="sxs-lookup"><span data-stu-id="b053c-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="b053c-113">Para crear un nuevo archivo de script</span><span class="sxs-lookup"><span data-stu-id="b053c-113">To create a new script file</span></span>

<span data-ttu-id="b053c-114">En la barra de herramientas, haga clic en **Nuevo**, o bien, en el menú **Archivo**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="b053c-114">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="b053c-115">El archivo creado aparece en una nueva pestaña de archivo en la ficha actual de PowerShell. Recuerde que las pestañas de PowerShell solo están visibles cuando hay más de una.</span><span class="sxs-lookup"><span data-stu-id="b053c-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="b053c-116">De forma predeterminada, se crea un archivo de tipo script (.ps1), pero se puede guardar con un nombre y una extensión diferentes.</span><span class="sxs-lookup"><span data-stu-id="b053c-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="b053c-117">Se pueden crear varios archivos de script en la misma pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b053c-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="b053c-118">Para abrir un script existente</span><span class="sxs-lookup"><span data-stu-id="b053c-118">To open an existing script</span></span>

<span data-ttu-id="b053c-119">En la barra de herramientas, haga clic en **Abrir**, o bien, en el menú **Archivo**, haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="b053c-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="b053c-120">En el cuadro de diálogo **Abrir**, seleccione el archivo que quiera abrir.</span><span class="sxs-lookup"><span data-stu-id="b053c-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="b053c-121">El archivo abierto aparece en una nueva pestaña.</span><span class="sxs-lookup"><span data-stu-id="b053c-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="b053c-122">Para cerrar una pestaña de script</span><span class="sxs-lookup"><span data-stu-id="b053c-122">To close a script tab</span></span>

<span data-ttu-id="b053c-123">Haga clic en la pestaña de script que quiera cerrar y realice una de las siguientes acciones:</span><span class="sxs-lookup"><span data-stu-id="b053c-123">Click the script tab of the script you want to close, then do one of the following:</span></span>

1. <span data-ttu-id="b053c-124">Haga clic en el icono **Cerrar** (X) de la pestaña de script.</span><span class="sxs-lookup"><span data-stu-id="b053c-124">Click the **Close** icon (X) on the script tab.</span></span>

2. <span data-ttu-id="b053c-125">En el menú **Archivo**, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="b053c-125">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="b053c-126">Si el archivo se ha modificado desde que se guardó por última vez, se le preguntará si desea guardar o descartar los cambios.</span><span class="sxs-lookup"><span data-stu-id="b053c-126">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="b053c-127">Para mostrar la ruta de acceso del archivo</span><span class="sxs-lookup"><span data-stu-id="b053c-127">To display the file path</span></span>

<span data-ttu-id="b053c-128">En la pestaña del archivo, señale el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="b053c-128">On the file tab, point to the file name.</span></span> <span data-ttu-id="b053c-129">La ruta de acceso completa al archivo de script se muestra en una información sobre herramientas.</span><span class="sxs-lookup"><span data-stu-id="b053c-129">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="b053c-130">Para ejecutar un script</span><span class="sxs-lookup"><span data-stu-id="b053c-130">To run a script</span></span>

<span data-ttu-id="b053c-131">En la barra de herramientas, haga clic en **Ejecutar script**, o bien, en el menú **Archivo**, haga clic en **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="b053c-131">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="b053c-132">Para ejecutar parte de un script</span><span class="sxs-lookup"><span data-stu-id="b053c-132">To run a portion of a script</span></span>

1. <span data-ttu-id="b053c-133">En el panel de scripts, seleccione una parte de un script.</span><span class="sxs-lookup"><span data-stu-id="b053c-133">In the Script Pane, select a portion of a script.</span></span>

2. <span data-ttu-id="b053c-134">En el menú **Archivo**, haga clic en **Ejecutar selección**, o bien haga clic en **Ejecutar selección** en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="b053c-134">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="b053c-135">Para detener un script que se está ejecutando</span><span class="sxs-lookup"><span data-stu-id="b053c-135">To stop a running script</span></span>

<span data-ttu-id="b053c-136">En la barra de herramientas, haga clic en **Detener la operación**, presione CTRL+Interrumpir, o bien, en el menú **Archivo**, haga clic en **Detener la operación**.</span><span class="sxs-lookup"><span data-stu-id="b053c-136">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="b053c-137">Presionar **CTRL+C** también funciona a menos que ya haya texto seleccionado, en cuyo caso **CTRL+C** se asigna a la función de copia del texto seleccionado.</span><span class="sxs-lookup"><span data-stu-id="b053c-137">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="b053c-138">Cómo escribir y editar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="b053c-138">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="b053c-139">Use los siguientes pasos para editar texto en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="b053c-139">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="b053c-140">Puede copiar, cortar, pegar, buscar y reemplazar texto.</span><span class="sxs-lookup"><span data-stu-id="b053c-140">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="b053c-141">También puede deshacer y rehacer la última acción que ha realizado.</span><span class="sxs-lookup"><span data-stu-id="b053c-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="b053c-142">Los métodos abreviados de teclado para realizar estas acciones son los mismos que los usados para todas las aplicaciones de Windows.</span><span class="sxs-lookup"><span data-stu-id="b053c-142">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="b053c-143">Para escribir texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="b053c-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="b053c-144">Mueva el cursor al panel de scripts haciendo clic en cualquier lugar del panel de scripts o en **Ir al panel de scripts** en el menú **Ver**.</span><span class="sxs-lookup"><span data-stu-id="b053c-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2. <span data-ttu-id="b053c-145">Cree un script.</span><span class="sxs-lookup"><span data-stu-id="b053c-145">Create a script.</span></span> <span data-ttu-id="b053c-146">El color de la sintaxis y la finalización con tabulación hacen que la experiencia sea mejor en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b053c-146">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3. <span data-ttu-id="b053c-147">Vea [Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obtener más información sobre el uso de la característica de finalización de con tabulación para facilitar la escritura.</span><span class="sxs-lookup"><span data-stu-id="b053c-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="b053c-148">Para buscar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="b053c-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="b053c-149">Para buscar texto en cualquier lugar, presione **CTRL+F** o, en el menú **Edición**, haga clic en **Buscar en el script**.</span><span class="sxs-lookup"><span data-stu-id="b053c-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2. <span data-ttu-id="b053c-150">Para buscar texto después del cursor, presione **F3** o, en el menú **Edición**, haga clic en **Buscar siguiente en el script**.</span><span class="sxs-lookup"><span data-stu-id="b053c-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3. <span data-ttu-id="b053c-151">Para buscar texto antes del cursor, presione **MAYÚS+F3** o, en el menú **Edición**, haga clic en **Buscar anterior en el script**.</span><span class="sxs-lookup"><span data-stu-id="b053c-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="b053c-152">Para buscar y reemplazar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="b053c-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="b053c-153">Presione **CRTL+H** o, en el menú **Edición**, haga clic en **Replace in Script** (Reemplazar en script).</span><span class="sxs-lookup"><span data-stu-id="b053c-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="b053c-154">Escriba el texto que quiera buscar y el texto con el que desee reemplazarlo y, a continuación, presione **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="b053c-154">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="b053c-155">Para ir a una línea determinada de texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="b053c-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="b053c-156">En el panel de scripts, presione **CTRL+G** o, en el menú **Edición**, haga clic en **Ir a la línea**.</span><span class="sxs-lookup"><span data-stu-id="b053c-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="b053c-157">Escriba un número de línea.</span><span class="sxs-lookup"><span data-stu-id="b053c-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="b053c-158">Para copiar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="b053c-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="b053c-159">En el panel de scripts, seleccione el texto que desee copiar.</span><span class="sxs-lookup"><span data-stu-id="b053c-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="b053c-160">Presione **CTRL+C** o haga clic en el icono **Copiar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="b053c-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="b053c-161">Para cortar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="b053c-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="b053c-162">En el panel de scripts, seleccione el texto que desee cortar.</span><span class="sxs-lookup"><span data-stu-id="b053c-162">In the Script Pane, select the text that you want to cut.</span></span>

2. <span data-ttu-id="b053c-163">Presione **CTRL+X** o haga clic en el icono **Cortar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Cortar**.</span><span class="sxs-lookup"><span data-stu-id="b053c-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="b053c-164">Para pegar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="b053c-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="b053c-165">Presione **CTRL+V** o haga clic en el icono **Pegar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Pegar**.</span><span class="sxs-lookup"><span data-stu-id="b053c-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="b053c-166">Para deshacer una acción en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="b053c-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="b053c-167">Presione **CTRL+Z** o haga clic en el icono **Deshacer** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Deshacer**.</span><span class="sxs-lookup"><span data-stu-id="b053c-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="b053c-168">Para rehacer una acción en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="b053c-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="b053c-169">Presione **CTRL+Y** o haga clic en el icono **Rehacer** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Rehacer**.</span><span class="sxs-lookup"><span data-stu-id="b053c-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="b053c-170">Cómo guardar un script</span><span class="sxs-lookup"><span data-stu-id="b053c-170">How to save a script</span></span>

<span data-ttu-id="b053c-171">Use los pasos siguientes para guardar un script y asignarle un nombre.</span><span class="sxs-lookup"><span data-stu-id="b053c-171">Use the following steps to save and name a script.</span></span> <span data-ttu-id="b053c-172">Aparece un asterisco junto al nombre del script para marcar un archivo que no se ha guardado desde que se modificó.</span><span class="sxs-lookup"><span data-stu-id="b053c-172">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="b053c-173">El asterisco desaparecerá cuando se guarda el archivo.</span><span class="sxs-lookup"><span data-stu-id="b053c-173">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="b053c-174">Para guardar un script</span><span class="sxs-lookup"><span data-stu-id="b053c-174">To save a script</span></span>

<span data-ttu-id="b053c-175">Presione **CTRL+S** o haga clic en el icono **Guardar** de la barra de herramientas. O bien, en el menú **Archivo**, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="b053c-175">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="b053c-176">Para guardar un script y asignarle un nombre</span><span class="sxs-lookup"><span data-stu-id="b053c-176">To save and name a script</span></span>

1. <span data-ttu-id="b053c-177">En el menú **Archivo**, haga clic en **Guardar como**.</span><span class="sxs-lookup"><span data-stu-id="b053c-177">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="b053c-178">Se abre el cuadro de diálogo **Guardar como**.</span><span class="sxs-lookup"><span data-stu-id="b053c-178">The **Save As** dialog box will appear.</span></span>

2. <span data-ttu-id="b053c-179">En el cuadro **Nombre de archivo**, escriba un nombre para el archivo.</span><span class="sxs-lookup"><span data-stu-id="b053c-179">In the **File name** box, enter a name for the file.</span></span>

3. <span data-ttu-id="b053c-180">En el cuadro **Guardar como tipo**, seleccione un tipo de archivo.</span><span class="sxs-lookup"><span data-stu-id="b053c-180">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="b053c-181">Por ejemplo, en el cuadro **Guardar como tipo**, seleccione "Scripts de PowerShell (\* .ps1)".</span><span class="sxs-lookup"><span data-stu-id="b053c-181">For example, in the **Save as type** box, select 'œPowerShell Scripts (\* .ps1)'.</span></span>

4. <span data-ttu-id="b053c-182">Haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="b053c-182">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="b053c-183">Para guardar un script en la codificación ASCII</span><span class="sxs-lookup"><span data-stu-id="b053c-183">To save a script in ASCII encoding</span></span>

<span data-ttu-id="b053c-184">De forma predeterminada, Windows PowerShell ISE guarda los nuevos archivos de script (.ps1), los archivos de datos de script (.psd1) y los archivos de módulo de script (.psm1) como Unicode (BigEndianUnicode). Para guardar un script en otra codificación, como ASCII (ANSI), use los métodos **Save** o **SaveAs** en el objeto [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile).</span><span class="sxs-lookup"><span data-stu-id="b053c-184">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="b053c-185">El siguiente comando guarda un nuevo script como MyScript.ps1 con la codificación ASCII.</span><span class="sxs-lookup"><span data-stu-id="b053c-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="b053c-186">El siguiente comando reemplaza el archivo de script actual con un archivo con el mismo nombre, pero con la codificación ASCII.</span><span class="sxs-lookup"><span data-stu-id="b053c-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="b053c-187">El comando siguiente obtiene la codificación del archivo actual.</span><span class="sxs-lookup"><span data-stu-id="b053c-187">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="b053c-188">Windows PowerShell ISE admite las siguientes opciones de codificación: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 y predeterminada.</span><span class="sxs-lookup"><span data-stu-id="b053c-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="b053c-189">El valor de la opción predeterminada varía según el sistema.</span><span class="sxs-lookup"><span data-stu-id="b053c-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="b053c-190">Windows PowerShell ISE no cambia la codificación de los scripts creados en otros editores, aunque se usen los comandos Guardar o Guardar como en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b053c-190">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="b053c-191">Véase también</span><span class="sxs-lookup"><span data-stu-id="b053c-191">See Also</span></span>

- [<span data-ttu-id="b053c-192">Explorar Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b053c-192">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)