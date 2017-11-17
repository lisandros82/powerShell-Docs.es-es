---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Finalidad del modelo de objetos de scripting de Windows PowerShell ISE
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 3256d8bff3885d266f0db6f52932e40c4beaf8b1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="d3801-103">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d3801-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>
  <span data-ttu-id="d3801-104">Los objetos están asociados con la forma y la función de Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="d3801-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="d3801-105">La referencia del modelo de objeto proporciona detalles sobre los métodos y las propiedades de los miembros que estos objetos exponen.</span><span class="sxs-lookup"><span data-stu-id="d3801-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="d3801-106">Se proporcionan ejemplos que muestran cómo puede utilizar scripts para acceder directamente a estos métodos y propiedades.</span><span class="sxs-lookup"><span data-stu-id="d3801-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="d3801-107">El modelo de objetos de scripting facilita el siguiente intervalo de tareas.</span><span class="sxs-lookup"><span data-stu-id="d3801-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="d3801-108">Personalización de la apariencia de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d3801-108">Customizing the appearance of Windows PowerShell ISE</span></span>
 <span data-ttu-id="d3801-109">Puede utilizar el modelo de objetos para modificar las opciones y la configuración de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d3801-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="d3801-110">Por ejemplo, puede modificarlas como sigue:</span><span class="sxs-lookup"><span data-stu-id="d3801-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="d3801-111">Puede cambiar el color de los errores, las advertencias, los resultados detallados y los resultados de depuración.</span><span class="sxs-lookup"><span data-stu-id="d3801-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>

- <span data-ttu-id="d3801-112">Puede obtener o establecer los colores de fondo del panel de comandos, del panel de resultados y del panel de scripts.</span><span class="sxs-lookup"><span data-stu-id="d3801-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>

- <span data-ttu-id="d3801-113">Puede definir el color de primer plano del panel de resultados.</span><span class="sxs-lookup"><span data-stu-id="d3801-113">You can set the foreground color for the Output pane.</span></span>

- <span data-ttu-id="d3801-114">Puede establecer el nombre y el tamaño de la fuente para Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d3801-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="d3801-115">Puede configurar las advertencias.</span><span class="sxs-lookup"><span data-stu-id="d3801-115">You can configure warnings.</span></span> <span data-ttu-id="d3801-116">Esta configuración incluye advertencias que se emiten cuando se abre un archivo en varias pestañas de PowerShell o cuando se ejecuta un script en el archivo antes de que se haya guardado el archivo.</span><span class="sxs-lookup"><span data-stu-id="d3801-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>

- <span data-ttu-id="d3801-117">Puede cambiar entre una vista en la que el panel de scripts y el panel de resultados se encuentran en paralelo y una vista en la que el panel de scripts está en la parte superior del panel de resultados.</span><span class="sxs-lookup"><span data-stu-id="d3801-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="d3801-118">Puede acoplar el panel de comandos en la parte inferior o superior del panel de resultados.</span><span class="sxs-lookup"><span data-stu-id="d3801-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="d3801-119">Mejora de la funcionalidad de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d3801-119">Enhancing the functionality of Windows PowerShell ISE</span></span>
 <span data-ttu-id="d3801-120">Puede utilizar el modelo de objetos para mejorar la funcionalidad de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d3801-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="d3801-121">Por ejemplo, puede:</span><span class="sxs-lookup"><span data-stu-id="d3801-121">For example, you can:</span></span>

- <span data-ttu-id="d3801-122">Agregar y modificar la instancia del mismo Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d3801-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="d3801-123">Por ejemplo, para cambiar los menús, puede agregar nuevos elementos de menú y asignarlos a scripts.</span><span class="sxs-lookup"><span data-stu-id="d3801-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>

- <span data-ttu-id="d3801-124">Crear scripts que llevan a cabo algunas de las tareas que puede realizar mediante el uso de los botones y comandos de menú en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d3801-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="d3801-125">Por ejemplo, puede agregar, quitar o seleccionar una pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3801-125">For example, you can add, remove, or select a PowerShell tab.</span></span>

- <span data-ttu-id="d3801-126">Complementar tareas que se pueden realizar con el uso de botones y comandos de menú.</span><span class="sxs-lookup"><span data-stu-id="d3801-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="d3801-127">Por ejemplo, puede cambiar el nombre de una pestaña de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3801-127">For example, you can rename a PowerShell tab.</span></span>

- <span data-ttu-id="d3801-128">Manipular los búferes de texto para el panel de comandos, el panel de resultados y el panel de scripts que están asociados a un archivo.</span><span class="sxs-lookup"><span data-stu-id="d3801-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="d3801-129">Por ejemplo, puede:</span><span class="sxs-lookup"><span data-stu-id="d3801-129">For example, you can:</span></span>

    -   <span data-ttu-id="d3801-130">Obtener o establecer todo el texto.</span><span class="sxs-lookup"><span data-stu-id="d3801-130">Get or set all text.</span></span>

    -   <span data-ttu-id="d3801-131">Obtener o establecer una selección de texto.</span><span class="sxs-lookup"><span data-stu-id="d3801-131">Get or set a text selection.</span></span>

    -   <span data-ttu-id="d3801-132">Ejecutar un script o una parte seleccionada de un script.</span><span class="sxs-lookup"><span data-stu-id="d3801-132">Run a script or run a selected portion of a script.</span></span>

    -   <span data-ttu-id="d3801-133">Desplazar una línea en la vista.</span><span class="sxs-lookup"><span data-stu-id="d3801-133">Scroll a line into view.</span></span>

    -   <span data-ttu-id="d3801-134">Insertar texto en una posición de intercalación.</span><span class="sxs-lookup"><span data-stu-id="d3801-134">Insert text at a caret position.</span></span>

    -   <span data-ttu-id="d3801-135">Seleccionar un bloque de texto.</span><span class="sxs-lookup"><span data-stu-id="d3801-135">Select a block of text.</span></span>

    -   <span data-ttu-id="d3801-136">Obtener el último número de línea.</span><span class="sxs-lookup"><span data-stu-id="d3801-136">Get the last line number.</span></span>

- <span data-ttu-id="d3801-137">Realizar operaciones de archivo.</span><span class="sxs-lookup"><span data-stu-id="d3801-137">Perform file operations.</span></span> <span data-ttu-id="d3801-138">Por ejemplo, puede:</span><span class="sxs-lookup"><span data-stu-id="d3801-138">For example, you can:</span></span>

    -   <span data-ttu-id="d3801-139">Abrir un archivo, guardar un archivo o guardar un archivo con un nombre diferente.</span><span class="sxs-lookup"><span data-stu-id="d3801-139">Open a file, save a file, or save a file by using a different name.</span></span>

    -   <span data-ttu-id="d3801-140">Determinar si un archivo ha cambiado desde que se guardó por última vez.</span><span class="sxs-lookup"><span data-stu-id="d3801-140">Determine whether a file has been changed after it was last saved.</span></span>

    -   <span data-ttu-id="d3801-141">Obtener el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="d3801-141">Get the file name.</span></span>

    -   <span data-ttu-id="d3801-142">Seleccionar un archivo.</span><span class="sxs-lookup"><span data-stu-id="d3801-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="d3801-143">Automatización de tareas</span><span class="sxs-lookup"><span data-stu-id="d3801-143">Automating tasks</span></span>
 <span data-ttu-id="d3801-144">Puede utilizar el modelo de objetos de scripting para crear métodos abreviados de teclado para operaciones frecuentes.</span><span class="sxs-lookup"><span data-stu-id="d3801-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3801-145">Véase también</span><span class="sxs-lookup"><span data-stu-id="d3801-145">See Also</span></span>
- [<span data-ttu-id="d3801-146">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="d3801-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md) 
- [<span data-ttu-id="d3801-147">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3801-147">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="d3801-148">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3801-148">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
