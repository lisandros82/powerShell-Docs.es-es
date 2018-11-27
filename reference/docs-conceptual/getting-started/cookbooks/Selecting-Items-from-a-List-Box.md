---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Seleccionar elementos de un cuadro de lista
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: e3d52839409a2fd58fbdc924a2b92d96fbecee53
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320829"
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="12bc1-103">Seleccionar elementos de un cuadro de lista</span><span class="sxs-lookup"><span data-stu-id="12bc1-103">Selecting Items from a List Box</span></span>

<span data-ttu-id="12bc1-104">Use Windows PowerShell 3.0 (y versiones posteriores) para crear un cuadro de diálogo donde los usuarios puedan seleccionar elementos de un control de cuadro de lista.</span><span class="sxs-lookup"><span data-stu-id="12bc1-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="12bc1-105">Crear un control de cuadro de lista y seleccionar elementos en él</span><span class="sxs-lookup"><span data-stu-id="12bc1-105">Create a list box control, and select items from it</span></span>

<span data-ttu-id="12bc1-106">Copie y pegue lo siguiente en Windows PowerShell ISE y, después, guárdelo como un script de Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="12bc1-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
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
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80

[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')

$form.Controls.Add($listBox)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

<span data-ttu-id="12bc1-107">El script comienza con la carga de dos clases de .NET Framework: **System.Drawing** y **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="12bc1-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="12bc1-108">A continuación, se inicia una nueva instancia de la clase de .NET Framework **System.Windows.Forms.Form**, que proporciona un formulario o ventana en blanco en la que puede empezar a agregar controles.</span><span class="sxs-lookup"><span data-stu-id="12bc1-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="12bc1-109">Tras crear una instancia de la clase Form, asigne valores a las tres propiedades de esta clase.</span><span class="sxs-lookup"><span data-stu-id="12bc1-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="12bc1-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="12bc1-110">**Text.**</span></span> <span data-ttu-id="12bc1-111">Es el título de la ventana.</span><span class="sxs-lookup"><span data-stu-id="12bc1-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="12bc1-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="12bc1-112">**Size.**</span></span> <span data-ttu-id="12bc1-113">Es el tamaño del formulario en píxeles.</span><span class="sxs-lookup"><span data-stu-id="12bc1-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="12bc1-114">El script anterior crea un formulario de 300 píxeles de ancho y 200 píxeles de alto.</span><span class="sxs-lookup"><span data-stu-id="12bc1-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="12bc1-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="12bc1-115">**StartingPosition.**</span></span> <span data-ttu-id="12bc1-116">Esta propiedad opcional está establecida en **CenterScreen** en el script anterior.</span><span class="sxs-lookup"><span data-stu-id="12bc1-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="12bc1-117">Si no agrega esta propiedad, Windows selecciona una ubicación cuando el formulario se abre.</span><span class="sxs-lookup"><span data-stu-id="12bc1-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="12bc1-118">Cuando **StartingPosition** se establece en **CenterScreen**, el formulario aparece automáticamente en el centro de la pantalla cada vez que se carga.</span><span class="sxs-lookup"><span data-stu-id="12bc1-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="12bc1-119">A continuación, cree un botón **Aceptar** para el formulario.</span><span class="sxs-lookup"><span data-stu-id="12bc1-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="12bc1-120">Indique un tamaño y el comportamiento del botón **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="12bc1-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="12bc1-121">En este ejemplo, la posición del botón es de 120 píxeles desde el borde superior del formulario y de 75 píxeles desde el borde izquierdo.</span><span class="sxs-lookup"><span data-stu-id="12bc1-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="12bc1-122">La altura del botón es 23 píxeles y la longitud, 75 píxeles.</span><span class="sxs-lookup"><span data-stu-id="12bc1-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="12bc1-123">El script usa tipos predefinidos de Windows Forms para definir el comportamiento del botón.</span><span class="sxs-lookup"><span data-stu-id="12bc1-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="12bc1-124">De manera similar, cree un botón **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="12bc1-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="12bc1-125">El botón **Cancelar** está a 120 píxeles de la parte superior, pero a 150 píxeles del borde izquierdo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="12bc1-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="12bc1-126">A continuación, escriba texto de etiqueta en la ventana para describir la información que quiera que los usuarios proporcionen.</span><span class="sxs-lookup"><span data-stu-id="12bc1-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="12bc1-127">En este caso, lo que se pretende es que los usuarios seleccionen un equipo.</span><span class="sxs-lookup"><span data-stu-id="12bc1-127">In this case, you want users to select a computer.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

<span data-ttu-id="12bc1-128">Agregue el control (en este caso, un cuadro de lista) que permita a los usuarios proporcionar la información descrita en el texto de etiqueta.</span><span class="sxs-lookup"><span data-stu-id="12bc1-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="12bc1-129">Aparte de los cuadros de lista, hay otros muchos controles que se pueden aplicar; para conocerlos, vea el tema sobre el [espacio de nombres System.Windows.Forms](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) en MSDN.</span><span class="sxs-lookup"><span data-stu-id="12bc1-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

<span data-ttu-id="12bc1-130">En la sección siguiente, hay que especificar los valores que quiere que el cuadro de lista muestre a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="12bc1-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="12bc1-131">El cuadro de lista creado con este script solo permite realizar una selección.</span><span class="sxs-lookup"><span data-stu-id="12bc1-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="12bc1-132">Para crear un control de cuadro de lista que permita selecciones múltiples, especifique un valor para la propiedad **SelectionMode**, como aquí: `$listBox.SelectionMode = 'MultiExtended'`.</span><span class="sxs-lookup"><span data-stu-id="12bc1-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following:  `$listBox.SelectionMode = 'MultiExtended'`.</span></span> <span data-ttu-id="12bc1-133">Para más información, consulte [Cuadros de lista de selección múltiple](Multiple-selection-List-Boxes.md).</span><span class="sxs-lookup"><span data-stu-id="12bc1-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

<span data-ttu-id="12bc1-134">Agregue el control de cuadro de lista al formulario e indique a Windows que, cuando el formulario se abra, lo haga encima del resto de ventanas y cuadros de diálogo abiertos.</span><span class="sxs-lookup"><span data-stu-id="12bc1-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="12bc1-135">Agregue la siguiente línea de código para mostrar el formulario en Windows.</span><span class="sxs-lookup"><span data-stu-id="12bc1-135">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="12bc1-136">Por último, el código del bloque **If** indica a Windows qué hacer con el formulario después de que los usuarios seleccionen una opción en el cuadro de lista y hagan clic en **Aceptar** o presionen la tecla **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="12bc1-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="12bc1-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="12bc1-137">See Also</span></span>

- <span data-ttu-id="12bc1-138">[Hey Scripting Guy: Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644) (Hey Scripting Guy: ¿Por qué estos ejemplos de GUI de PowerShell no funcionan?)</span><span class="sxs-lookup"><span data-stu-id="12bc1-138">[Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644)</span></span>
- <span data-ttu-id="12bc1-139">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates) (GitHub: WinFormsExampleUpdates de Dave Wyatt)</span><span class="sxs-lookup"><span data-stu-id="12bc1-139">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)</span></span>
- <span data-ttu-id="12bc1-140">[Windows PowerShell Tip of the Week: Selecting Items from a List Box](https://technet.microsoft.com/library/ff730949.aspx) (Sugerencia de la semana de Windows PowerShell: Seleccionar elementos de un cuadro de lista)</span><span class="sxs-lookup"><span data-stu-id="12bc1-140">[Windows PowerShell Tip of the Week:  Selecting Items from a List Box](https://technet.microsoft.com/library/ff730949.aspx)</span></span>