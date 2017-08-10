---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Cómo escribir y ejecutar scripts en Windows PowerShell ISE"
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 871a4b6f4575af4f823a6957dc971335497320a4
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="5268b-103">Cómo escribir y ejecutar scripts en Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="5268b-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>
<span data-ttu-id="5268b-104">En este tema se describe cómo crear, editar, ejecutar y guardar scripts en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="5268b-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

-   [<span data-ttu-id="5268b-105">Cómo crear y ejecutar scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-105">How to create and run scripts</span></span>](#bkmk_1)

-   [<span data-ttu-id="5268b-106">Cómo escribir y editar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-106">How to write and edit text in the Script Pane</span></span>](#bkmk_2)

-   [<span data-ttu-id="5268b-107">Cómo guardar un script</span><span class="sxs-lookup"><span data-stu-id="5268b-107">How to save a script</span></span>](#bkmk_3)

## <span data-ttu-id="5268b-108"><a name="bkmk_1"></a>Cómo crear y ejecutar scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-108"><a name="bkmk_1"></a>How to create and run scripts</span></span>
<span data-ttu-id="5268b-109">Puede abrir y editar archivos de Windows PowerShell® en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="5268b-109">You can open and edit Windows PowerShell® files in the Script Pane.</span></span> <span data-ttu-id="5268b-110">Los tipos de archivo de interés específicos de Windows PowerShell® son los archivos de script (.ps1), los archivos de datos de script (.psd1) y los archivos de módulo de script (.psm1).</span><span class="sxs-lookup"><span data-stu-id="5268b-110">Specific file types of interest in Windows PowerShell® are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="5268b-111">Estos tipos de archivo presentan color de sintaxis en el editor de panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="5268b-111">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="5268b-112">Otros tipos de archivo comunes que puede abrir en el panel de scripts son los archivos de configuración (.ps1xml), los archivos XML y los archivos de texto.</span><span class="sxs-lookup"><span data-stu-id="5268b-112">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="5268b-113">La directiva de ejecución de Windows PowerShell determina si puede ejecutar scripts y cargar archivos de configuración y perfiles de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5268b-113">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="5268b-114">La directiva de ejecución predeterminada, Restricted, impide que se ejecuten todos los scripts y que se carguen perfiles.</span><span class="sxs-lookup"><span data-stu-id="5268b-114">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="5268b-115">Para cambiar la directiva de ejecución a fin de permitir cargar y usar perfiles, consulte [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) y [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span><span class="sxs-lookup"><span data-stu-id="5268b-115">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="5268b-116">Para crear un nuevo archivo de script</span><span class="sxs-lookup"><span data-stu-id="5268b-116">To create a new script file</span></span>
<span data-ttu-id="5268b-117">En la barra de herramientas, haga clic en **Nuevo**, o bien, en el menú **Archivo**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="5268b-117">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="5268b-118">El archivo creado aparece en una nueva pestaña de archivo en la ficha actual de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5268b-118">The created file appears in a new file tab under the current PowerShell tab.</span></span> <span data-ttu-id="5268b-119">Recuerde que las pestañas de PowerShell solo están visibles cuando hay más de una.</span><span class="sxs-lookup"><span data-stu-id="5268b-119">Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="5268b-120">De forma predeterminada, se crea un archivo de tipo script (.ps1), pero se puede guardar con un nombre y una extensión diferentes.</span><span class="sxs-lookup"><span data-stu-id="5268b-120">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="5268b-121">Se pueden crear varios archivos de script en la misma pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5268b-121">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="5268b-122">Para abrir un script existente</span><span class="sxs-lookup"><span data-stu-id="5268b-122">To open an existing script</span></span>
<span data-ttu-id="5268b-123">En la barra de herramientas, haga clic en **Abrir**, o bien, en el menú **Archivo**, haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="5268b-123">On the toolbar, click **Open…**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="5268b-124">En el cuadro de diálogo **Abrir**, seleccione el archivo que quiera abrir.</span><span class="sxs-lookup"><span data-stu-id="5268b-124">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="5268b-125">El archivo abierto aparece en una nueva pestaña.</span><span class="sxs-lookup"><span data-stu-id="5268b-125">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="5268b-126">Para cerrar una pestaña de script</span><span class="sxs-lookup"><span data-stu-id="5268b-126">To close a script tab</span></span>
<span data-ttu-id="5268b-127">Haga clic en la pestaña de script que quiera cerrar y realice una de las siguientes acciones:</span><span class="sxs-lookup"><span data-stu-id="5268b-127">Click the script tab of the script you want to close, then do one of the following:</span></span>

1.  <span data-ttu-id="5268b-128">Haga clic en el icono **Cerrar** (X) de la pestaña de script.</span><span class="sxs-lookup"><span data-stu-id="5268b-128">Click the **Close** icon (X) on the script tab.</span></span>

2.  <span data-ttu-id="5268b-129">En el menú **Archivo**, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="5268b-129">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="5268b-130">Si el archivo se ha modificado desde que se guardó por última vez, se le preguntará si desea guardar o descartar los cambios.</span><span class="sxs-lookup"><span data-stu-id="5268b-130">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="5268b-131">Para mostrar la ruta de acceso del archivo</span><span class="sxs-lookup"><span data-stu-id="5268b-131">To display the file path</span></span>
<span data-ttu-id="5268b-132">En la pestaña del archivo, señale el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="5268b-132">On the file tab, point to the file name.</span></span> <span data-ttu-id="5268b-133">La ruta de acceso completa al archivo de script se muestra en una información sobre herramientas.</span><span class="sxs-lookup"><span data-stu-id="5268b-133">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="5268b-134">Para ejecutar un script</span><span class="sxs-lookup"><span data-stu-id="5268b-134">To run a script</span></span>
<span data-ttu-id="5268b-135">En la barra de herramientas, haga clic en **Ejecutar script**, o bien, en el menú **Archivo**, haga clic en **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="5268b-135">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="5268b-136">Para ejecutar parte de un script</span><span class="sxs-lookup"><span data-stu-id="5268b-136">To run a portion of a script</span></span>

1.  <span data-ttu-id="5268b-137">En el panel de scripts, seleccione una parte de un script.</span><span class="sxs-lookup"><span data-stu-id="5268b-137">In the Script Pane, select a portion of a script.</span></span>

2.  <span data-ttu-id="5268b-138">En el menú **Archivo**, haga clic en **Ejecutar selección**, o bien haga clic en **Ejecutar selección** en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="5268b-138">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="5268b-139">Para detener un script que se está ejecutando</span><span class="sxs-lookup"><span data-stu-id="5268b-139">To stop a running script</span></span>
<span data-ttu-id="5268b-140">En la barra de herramientas, haga clic en **Detener la operación**, presione CTRL+Interrumpir, o bien, en el menú **Archivo**, haga clic en **Detener la operación**.</span><span class="sxs-lookup"><span data-stu-id="5268b-140">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="5268b-141">Presionar **CTRL+C** también funciona a menos que ya haya texto seleccionado, en cuyo caso **CTRL+C** se asigna a la función de copia del texto seleccionado.</span><span class="sxs-lookup"><span data-stu-id="5268b-141">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <span data-ttu-id="5268b-142"><a name="bkmk_2"></a>Cómo escribir y editar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-142"><a name="bkmk_2"></a>How to write and edit text in the Script Pane</span></span>
<span data-ttu-id="5268b-143">Use los siguientes pasos para editar texto en el panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="5268b-143">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="5268b-144">Puede copiar, cortar, pegar, buscar y reemplazar texto.</span><span class="sxs-lookup"><span data-stu-id="5268b-144">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="5268b-145">También puede deshacer y rehacer la última acción que ha realizado.</span><span class="sxs-lookup"><span data-stu-id="5268b-145">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="5268b-146">Los métodos abreviados de teclado para realizar estas acciones son los mismos que los usados para todas las aplicaciones de Windows.</span><span class="sxs-lookup"><span data-stu-id="5268b-146">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="5268b-147">Para escribir texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-147">To enter text in the Script Pane</span></span>

1.  <span data-ttu-id="5268b-148">Mueva el cursor al panel de scripts haciendo clic en cualquier lugar del panel de scripts o en **Ir al panel de scripts** en el menú **Ver**.</span><span class="sxs-lookup"><span data-stu-id="5268b-148">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2.  <span data-ttu-id="5268b-149">Cree un script.</span><span class="sxs-lookup"><span data-stu-id="5268b-149">Create a script.</span></span> <span data-ttu-id="5268b-150">El color de la sintaxis y la finalización con tabulación hacen que la experiencia sea mejor en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="5268b-150">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3.  <span data-ttu-id="5268b-151">Vea [Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obtener más información sobre el uso de la característica de finalización de con tabulación para facilitar la escritura.</span><span class="sxs-lookup"><span data-stu-id="5268b-151">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="5268b-152">Para buscar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-152">To find text in the Script Pane</span></span>

1.  <span data-ttu-id="5268b-153">Para buscar texto en cualquier lugar, presione **CTRL+F** o, en el menú **Edición**, haga clic en **Buscar en el script**.</span><span class="sxs-lookup"><span data-stu-id="5268b-153">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2.  <span data-ttu-id="5268b-154">Para buscar texto después del cursor, presione **F3** o, en el menú **Edición**, haga clic en **Buscar siguiente en el script**.</span><span class="sxs-lookup"><span data-stu-id="5268b-154">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3.  <span data-ttu-id="5268b-155">Para buscar texto antes del cursor, presione **MAYÚS+F3** o, en el menú **Edición**, haga clic en **Buscar anterior en el script**.</span><span class="sxs-lookup"><span data-stu-id="5268b-155">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="5268b-156">Para buscar y reemplazar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-156">To find and replace text in the Script Pane</span></span>
<span data-ttu-id="5268b-157">Presione **CRTL+H** o, en el menú **Edición**, haga clic en **Reemplazar en script**.</span><span class="sxs-lookup"><span data-stu-id="5268b-157">Press **CRTL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="5268b-158">Escriba el texto que quiera buscar y el texto con el que desee reemplazarlo y, a continuación, presione **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="5268b-158">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="5268b-159">Para ir a una línea determinada de texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-159">To go to a particular line of text in the Script Pane</span></span>

1.  <span data-ttu-id="5268b-160">En el panel de scripts, presione **CTRL+G** o, en el menú **Edición**, haga clic en **Ir a la línea**.</span><span class="sxs-lookup"><span data-stu-id="5268b-160">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2.  <span data-ttu-id="5268b-161">Escriba un número de línea.</span><span class="sxs-lookup"><span data-stu-id="5268b-161">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="5268b-162">Para copiar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-162">To copy text in the Script Pane</span></span>

1.  <span data-ttu-id="5268b-163">En el panel de scripts, seleccione el texto que desee copiar.</span><span class="sxs-lookup"><span data-stu-id="5268b-163">In the Script Pane, select the text that you want to copy.</span></span>

2.  <span data-ttu-id="5268b-164">Presione **CTRL+C** o haga clic en el icono **Copiar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="5268b-164">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="5268b-165">Para cortar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-165">To cut text in the Script Pane</span></span>

1.  <span data-ttu-id="5268b-166">En el panel de scripts, seleccione el texto que desee cortar.</span><span class="sxs-lookup"><span data-stu-id="5268b-166">In the Script Pane, select the text that you want to cut.</span></span>

2.  <span data-ttu-id="5268b-167">Presione **CTRL+X** o haga clic en el icono **Cortar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Cortar**.</span><span class="sxs-lookup"><span data-stu-id="5268b-167">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="5268b-168">Para pegar texto en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-168">To paste text into the Script Pane</span></span>
<span data-ttu-id="5268b-169">Presione **CTRL+V** o haga clic en el icono **Pegar** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Pegar**.</span><span class="sxs-lookup"><span data-stu-id="5268b-169">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="5268b-170">Para deshacer una acción en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-170">To undo an action in the Script Pane</span></span>
<span data-ttu-id="5268b-171">Presione **CTRL+Z** o haga clic en el icono **Deshacer** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Deshacer**.</span><span class="sxs-lookup"><span data-stu-id="5268b-171">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="5268b-172">Para rehacer una acción en el panel de scripts</span><span class="sxs-lookup"><span data-stu-id="5268b-172">To redo an action in the Script Pane</span></span>
<span data-ttu-id="5268b-173">Presione **CTRL+Y** o haga clic en el icono **Rehacer** de la barra de herramientas. O bien, en el menú **Edición**, haga clic en **Rehacer**.</span><span class="sxs-lookup"><span data-stu-id="5268b-173">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <span data-ttu-id="5268b-174"><a name="bkmk_3"></a>Cómo guardar un script</span><span class="sxs-lookup"><span data-stu-id="5268b-174"><a name="bkmk_3"></a>How to save a script</span></span>
<span data-ttu-id="5268b-175">Use los pasos siguientes para guardar un script y asignarle un nombre.</span><span class="sxs-lookup"><span data-stu-id="5268b-175">Use the following steps to save and name a script.</span></span> <span data-ttu-id="5268b-176">Aparece un asterisco junto al nombre del script para marcar un archivo que no se ha guardado desde que se modificó.</span><span class="sxs-lookup"><span data-stu-id="5268b-176">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="5268b-177">El asterisco desaparecerá cuando se guarda el archivo.</span><span class="sxs-lookup"><span data-stu-id="5268b-177">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="5268b-178">Para guardar un script</span><span class="sxs-lookup"><span data-stu-id="5268b-178">To save a script</span></span>
<span data-ttu-id="5268b-179">Presione **CTRL+S** o haga clic en el icono **Guardar** de la barra de herramientas. O bien, en el menú **Archivo**, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="5268b-179">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="5268b-180">Para guardar un script y asignarle un nombre</span><span class="sxs-lookup"><span data-stu-id="5268b-180">To save and name a script</span></span>

1.  <span data-ttu-id="5268b-181">En el menú **Archivo**, haga clic en **Guardar como**.</span><span class="sxs-lookup"><span data-stu-id="5268b-181">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="5268b-182">Se abre el cuadro de diálogo **Guardar como**.</span><span class="sxs-lookup"><span data-stu-id="5268b-182">The **Save As** dialog box will appear.</span></span>

2.  <span data-ttu-id="5268b-183">En el cuadro **Nombre de archivo**, escriba un nombre para el archivo.</span><span class="sxs-lookup"><span data-stu-id="5268b-183">In the **File name** box, enter a name for the file.</span></span>

3.  <span data-ttu-id="5268b-184">En el cuadro **Guardar como tipo**, seleccione un tipo de archivo.</span><span class="sxs-lookup"><span data-stu-id="5268b-184">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="5268b-185">Por ejemplo, en el cuadro **Guardar como tipo**, seleccione “Scripts de PowerShell (\* .ps1)”.</span><span class="sxs-lookup"><span data-stu-id="5268b-185">For example, in the **Save as type** box, select “PowerShell Scripts (\* .ps1)”.</span></span>

4.  <span data-ttu-id="5268b-186">Haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="5268b-186">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="5268b-187">Para guardar un script en la codificación ASCII</span><span class="sxs-lookup"><span data-stu-id="5268b-187">To save a script in ASCII encoding</span></span>
<span data-ttu-id="5268b-188">De forma predeterminada, Windows PowerShell ISE guarda los nuevos archivos de script (.ps1), los archivos de datos de script (.psd1) y los archivos de módulo de script (.psm1) como Unicode (BigEndianUnicode).</span><span class="sxs-lookup"><span data-stu-id="5268b-188">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.</span></span> <span data-ttu-id="5268b-189">Para guardar un script en otra codificación, como ASCII (ANSI), use los métodos **Save** o **SaveAs** en el objeto [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile).</span><span class="sxs-lookup"><span data-stu-id="5268b-189">To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="5268b-190">El siguiente comando guarda un nuevo script como MyScript.ps1 con la codificación ASCII.</span><span class="sxs-lookup"><span data-stu-id="5268b-190">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="5268b-191">El siguiente comando reemplaza el archivo de script actual con un archivo con el mismo nombre, pero con la codificación ASCII.</span><span class="sxs-lookup"><span data-stu-id="5268b-191">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="5268b-192">El comando siguiente obtiene la codificación del archivo actual.</span><span class="sxs-lookup"><span data-stu-id="5268b-192">The following command gets the encoding of the current file.</span></span>

```
$psise.CurrentFile.encoding
```

<span data-ttu-id="5268b-193">Windows PowerShell ISE admite las siguientes opciones de codificación: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 y predeterminada.</span><span class="sxs-lookup"><span data-stu-id="5268b-193">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="5268b-194">El valor de la opción predeterminada varía según el sistema.</span><span class="sxs-lookup"><span data-stu-id="5268b-194">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="5268b-195">Windows PowerShell ISE no cambia la codificación de los scripts creados en otros editores, aunque se usen los comandos Guardar o Guardar como en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="5268b-195">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="5268b-196">Véase también</span><span class="sxs-lookup"><span data-stu-id="5268b-196">See Also</span></span>
- [<span data-ttu-id="5268b-197">Usar Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="5268b-197">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)

