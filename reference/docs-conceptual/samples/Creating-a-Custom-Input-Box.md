---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Crear un cuadro de entrada personalizado
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 2d04ad6df65cdb4ff13d136dea47bbba6a01f3a2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402226"
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="b9e4b-103">Crear un cuadro de entrada personalizado</span><span class="sxs-lookup"><span data-stu-id="b9e4b-103">Creating a Custom Input Box</span></span>

<span data-ttu-id="b9e4b-104">Cree un script de un cuadro de entrada gráfico personalizado usando las características de creación de formularios de Microsoft .NET Framework de Windows PowerShell 3.0 (y versiones posteriores).</span><span class="sxs-lookup"><span data-stu-id="b9e4b-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="b9e4b-105">Crear un cuadro de entrada gráfico personalizado</span><span class="sxs-lookup"><span data-stu-id="b9e4b-105">Create a custom, graphical input box</span></span>

<span data-ttu-id="b9e4b-106">Copie y pegue lo siguiente en Windows PowerShell ISE y, después, guárdelo como un script de Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="b9e4b-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)

$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)

$form.Topmost = $true

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

<span data-ttu-id="b9e4b-107">El script comienza cargando dos clases de .NET Framework: **System.Drawing** y **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="b9e4b-108">A continuación, se inicia una nueva instancia de la clase de .NET Framework **System.Windows.Forms.Form**, que proporciona un formulario o ventana en blanco en la que puede empezar a agregar controles.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="b9e4b-109">Tras crear una instancia de la clase Form, asigne valores a las tres propiedades de esta clase.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="b9e4b-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="b9e4b-110">**Text.**</span></span> <span data-ttu-id="b9e4b-111">Es el título de la ventana.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="b9e4b-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="b9e4b-112">**Size.**</span></span> <span data-ttu-id="b9e4b-113">Es el tamaño del formulario en píxeles.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="b9e4b-114">El script anterior crea un formulario de 300 píxeles de ancho y 200 píxeles de alto.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="b9e4b-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="b9e4b-115">**StartingPosition.**</span></span> <span data-ttu-id="b9e4b-116">Esta propiedad opcional está establecida en **CenterScreen** en el script anterior.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="b9e4b-117">Si no agrega esta propiedad, Windows selecciona una ubicación cuando el formulario se abre.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="b9e4b-118">Cuando **StartingPosition** se establece en **CenterScreen**, el formulario aparece automáticamente en el centro de la pantalla cada vez que se carga.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="b9e4b-119">A continuación, cree un botón **Aceptar** para el formulario.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="b9e4b-120">Indique un tamaño y el comportamiento del botón **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="b9e4b-121">En este ejemplo, la posición del botón es de 120 píxeles desde el borde superior del formulario y de 75 píxeles desde el borde izquierdo.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="b9e4b-122">La altura del botón es 23 píxeles y la longitud, 75 píxeles.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="b9e4b-123">El script usa tipos predefinidos de Windows Forms para definir el comportamiento del botón.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="b9e4b-124">De manera similar, cree un botón **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="b9e4b-125">El botón **Cancelar** está a 120 píxeles de la parte superior, pero a 150 píxeles del borde izquierdo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="b9e4b-126">A continuación, escriba texto de etiqueta en la ventana para describir la información que quiera que los usuarios proporcionen.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="b9e4b-127">Agregue el control (en este caso, un cuadro de texto) que permita a los usuarios proporcionar la información descrita en el texto de etiqueta.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="b9e4b-128">Aparte de los cuadros de texto, hay otros muchos controles que se pueden aplicar; para conocerlos, vea el tema sobre el [espacio de nombres System.Windows.Forms](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) en MSDN.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="b9e4b-129">Establezca la propiedad **Topmost** en **$True** para forzar que la ventana se abra encima del resto de ventanas y cuadros de diálogo abiertos.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="b9e4b-130">A continuación, agregue esta línea de código para activar el formulario y establezca el foco en el cuadro de texto que ha creado.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="b9e4b-131">Agregue la siguiente línea de código para mostrar el formulario en Windows.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-131">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="b9e4b-132">Por último, el código del bloque **If** indica a Windows qué hacer con el formulario después de que los usuarios proporcionen el texto en el cuadro de texto y hagan clic en **Aceptar** o presionen la tecla **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="b9e4b-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="b9e4b-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="b9e4b-133">See Also</span></span>

- <span data-ttu-id="b9e4b-134">[Hey Scripting Guy: Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644) (Hey Scripting Guy: ¿Por qué estos ejemplos de GUI de PowerShell no funcionan?)</span><span class="sxs-lookup"><span data-stu-id="b9e4b-134">[Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644)</span></span>
- <span data-ttu-id="b9e4b-135">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates) (GitHub: WinFormsExampleUpdates de Dave Wyatt)</span><span class="sxs-lookup"><span data-stu-id="b9e4b-135">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)</span></span>
- <span data-ttu-id="b9e4b-136">[Windows PowerShell Tip of the Week: Creating a Custom Input Box](https://technet.microsoft.com/library/ff730941.aspx) (Sugerencia de la semana de Windows PowerShell: Crear un cuadro de entrada personalizado)</span><span class="sxs-lookup"><span data-stu-id="b9e4b-136">[Windows PowerShell Tip of the Week:  Creating a Custom Input Box](https://technet.microsoft.com/library/ff730941.aspx)</span></span>