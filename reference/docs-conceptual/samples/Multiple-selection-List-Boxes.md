---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Cuadros de lista de selección múltiple
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: a762145dc197ec7e1424b2fbdcef5e7380d13803
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057968"
---
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="a6a43-103">Cuadros de lista de selección múltiple</span><span class="sxs-lookup"><span data-stu-id="a6a43-103">Multiple-selection List Boxes</span></span>

<span data-ttu-id="a6a43-104">Use Windows PowerShell 3.0 (y versiones posteriores) para crear un control de cuadro de lista de selección múltiple en un formulario de Windows Forms personalizado.</span><span class="sxs-lookup"><span data-stu-id="a6a43-104">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="a6a43-105">Crear controles de cuadro de lista que permiten selecciones múltiples</span><span class="sxs-lookup"><span data-stu-id="a6a43-105">Create list box controls that allow multiple selections</span></span>

<span data-ttu-id="a6a43-106">Copie y pegue lo siguiente en Windows PowerShell ISE y, después, guárdelo como un script de Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="a6a43-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)

$listBox.SelectionMode = 'MultiExtended'

[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')

$listBox.Height = 70
$form.Controls.Add($listBox)
$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

<span data-ttu-id="a6a43-107">El script comienza con la carga de dos clases de .NET Framework: **System.Drawing** y **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="a6a43-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="a6a43-108">A continuación, se inicia una nueva instancia de la clase de .NET Framework **System.Windows.Forms.Form**, que proporciona un formulario o ventana en blanco en la que puede empezar a agregar controles.</span><span class="sxs-lookup"><span data-stu-id="a6a43-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="a6a43-109">Tras crear una instancia de la clase Form, asigne valores a las tres propiedades de esta clase.</span><span class="sxs-lookup"><span data-stu-id="a6a43-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="a6a43-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="a6a43-110">**Text.**</span></span> <span data-ttu-id="a6a43-111">Es el título de la ventana.</span><span class="sxs-lookup"><span data-stu-id="a6a43-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="a6a43-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="a6a43-112">**Size.**</span></span> <span data-ttu-id="a6a43-113">Es el tamaño del formulario en píxeles.</span><span class="sxs-lookup"><span data-stu-id="a6a43-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="a6a43-114">El script anterior crea un formulario de 300 píxeles de ancho y 200 píxeles de alto.</span><span class="sxs-lookup"><span data-stu-id="a6a43-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="a6a43-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="a6a43-115">**StartingPosition.**</span></span> <span data-ttu-id="a6a43-116">Esta propiedad opcional está establecida en **CenterScreen** en el script anterior.</span><span class="sxs-lookup"><span data-stu-id="a6a43-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="a6a43-117">Si no agrega esta propiedad, Windows selecciona una ubicación cuando el formulario se abre.</span><span class="sxs-lookup"><span data-stu-id="a6a43-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="a6a43-118">Cuando **StartingPosition** se establece en **CenterScreen**, el formulario aparece automáticamente en el centro de la pantalla cada vez que se carga.</span><span class="sxs-lookup"><span data-stu-id="a6a43-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="a6a43-119">A continuación, cree un botón **Aceptar** para el formulario.</span><span class="sxs-lookup"><span data-stu-id="a6a43-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="a6a43-120">Indique un tamaño y el comportamiento del botón **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="a6a43-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="a6a43-121">En este ejemplo, la posición del botón es de 120 píxeles desde el borde superior del formulario y de 75 píxeles desde el borde izquierdo.</span><span class="sxs-lookup"><span data-stu-id="a6a43-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="a6a43-122">La altura del botón es 23 píxeles y la longitud, 75 píxeles.</span><span class="sxs-lookup"><span data-stu-id="a6a43-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="a6a43-123">El script usa tipos predefinidos de Windows Forms para definir el comportamiento del botón.</span><span class="sxs-lookup"><span data-stu-id="a6a43-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="a6a43-124">De manera similar, cree un botón **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="a6a43-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="a6a43-125">El botón **Cancelar** está a 120 píxeles de la parte superior, pero a 150 píxeles del borde izquierdo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="a6a43-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="a6a43-126">A continuación, escriba texto de etiqueta en la ventana para describir la información que quiera que los usuarios proporcionen.</span><span class="sxs-lookup"><span data-stu-id="a6a43-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

<span data-ttu-id="a6a43-127">Agregue el control (en este caso, un cuadro de lista) que permita a los usuarios proporcionar la información descrita en el texto de etiqueta.</span><span class="sxs-lookup"><span data-stu-id="a6a43-127">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="a6a43-128">Aparte de los cuadros de texto, hay otros muchos controles que se pueden aplicar; para conocerlos, vea el tema sobre el [espacio de nombres System.Windows.Forms](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) en MSDN.</span><span class="sxs-lookup"><span data-stu-id="a6a43-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

<span data-ttu-id="a6a43-129">Aquí indicamos cómo especificar que se quiere permitir a los usuarios seleccionar varios valores en la lista.</span><span class="sxs-lookup"><span data-stu-id="a6a43-129">Here’s how you specify that you want to allow users to select multiple values from the list.</span></span>

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

<span data-ttu-id="a6a43-130">En la sección siguiente, hay que especificar los valores que quiere que el cuadro de lista muestre a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="a6a43-130">In the next section, you specify the values you want the list box to display to users.</span></span>

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

<span data-ttu-id="a6a43-131">Especifique el alto máximo del control de cuadro de lista.</span><span class="sxs-lookup"><span data-stu-id="a6a43-131">Specify the maximum height of the list box control.</span></span>

```powershell
$listBox.Height = 70
```

<span data-ttu-id="a6a43-132">Agregue el control de cuadro de lista al formulario e indique a Windows que, cuando el formulario se abra, lo haga encima del resto de ventanas y cuadros de diálogo abiertos.</span><span class="sxs-lookup"><span data-stu-id="a6a43-132">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="a6a43-133">Agregue la siguiente línea de código para mostrar el formulario en Windows.</span><span class="sxs-lookup"><span data-stu-id="a6a43-133">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="a6a43-134">Por último, el código del bloque **If** indica a Windows qué hacer con el formulario después de que los usuarios seleccionen una o varias opciones en el cuadro de lista y hagan clic en **Aceptar** o presionen la tecla **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="a6a43-134">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="a6a43-135">Véase también</span><span class="sxs-lookup"><span data-stu-id="a6a43-135">See Also</span></span>

- <span data-ttu-id="a6a43-136">[Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644) (Hey Scripting Guy: ¿Por qué estos ejemplos de GUI de PowerShell no funcionan?)</span><span class="sxs-lookup"><span data-stu-id="a6a43-136">[Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644)</span></span>
- <span data-ttu-id="a6a43-137">[GitHub: ](https://github.com/dlwyatt/WinFormsExampleUpdates)Dave Wyatt's WinFormsExampleUpdates (GitHub: WinFormsExampleUpdates de Dave Wyatt)</span><span class="sxs-lookup"><span data-stu-id="a6a43-137">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)</span></span>
- <span data-ttu-id="a6a43-138">[Windows PowerShell Tip of the Week:  Multi-Select List Boxes - And More!](https://technet.microsoft.com/library/ff730950.aspx) (Consejo de la semana de Windows PowerShell: cuadros de lista de selección múltiple, ¡y mucho más!)</span><span class="sxs-lookup"><span data-stu-id="a6a43-138">[Windows PowerShell Tip of the Week:  Multi-Select List Boxes - And More!](https://technet.microsoft.com/library/ff730950.aspx)</span></span>