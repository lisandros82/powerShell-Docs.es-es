---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Crear un selector de fecha gráfico
ms.openlocfilehash: d05445963b41af61a61aa29a425e638d43fb5d9d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030256"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="f78cf-103">Crear un selector de fecha gráfico</span><span class="sxs-lookup"><span data-stu-id="f78cf-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="f78cf-104">Use Windows PowerShell 3.0 (y versiones posteriores) para crear un formulario con un control gráfico de estilo de calendario que permita a los usuarios seleccionar un día del mes.</span><span class="sxs-lookup"><span data-stu-id="f78cf-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="f78cf-105">Crear un control gráfico de selector de fecha</span><span class="sxs-lookup"><span data-stu-id="f78cf-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="f78cf-106">Copie y pegue lo siguiente en Windows PowerShell ISE y, después, guárdelo como un script de Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="f78cf-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="f78cf-107">El script comienza con la carga de dos clases de .NET Framework: **System.Drawing** y **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="f78cf-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span>
<span data-ttu-id="f78cf-108">A continuación, inicie una nueva instancia de la clase de .NET Framework **Windows.Forms.Form**, que proporciona un formulario o una ventana en blanco en la que puede empezar a agregar controles.</span><span class="sxs-lookup"><span data-stu-id="f78cf-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="f78cf-109">En este ejemplo se asignan valores a cuatro propiedades de esta clase mediante la propiedad **Property** y la tabla hash.</span><span class="sxs-lookup"><span data-stu-id="f78cf-109">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="f78cf-110">**StartPosition**: Si no agrega esta propiedad, Windows selecciona una ubicación cuando el formulario se abre.</span><span class="sxs-lookup"><span data-stu-id="f78cf-110">**StartPosition**: If you don’t add this property, Windows selects a location when the form is opened.</span></span>
   <span data-ttu-id="f78cf-111">Al establecer esta propiedad en **CenterScreen**, el formulario aparece automáticamente en el centro de la pantalla cada vez que se carga.</span><span class="sxs-lookup"><span data-stu-id="f78cf-111">By setting this property to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="f78cf-112">**Size**: Es el tamaño del formulario en píxeles.</span><span class="sxs-lookup"><span data-stu-id="f78cf-112">**Size**: This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="f78cf-113">El script anterior crea un formulario de 243 píxeles de ancho y 230 píxeles de alto.</span><span class="sxs-lookup"><span data-stu-id="f78cf-113">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="f78cf-114">**Text**: Es el título de la ventana.</span><span class="sxs-lookup"><span data-stu-id="f78cf-114">**Text**: This becomes the title of the window.</span></span>

4. <span data-ttu-id="f78cf-115">**Topmost**: Al establecer esta propiedad en `$true`, puede forzar a que la ventana se abra encima del resto de ventanas y cuadros de diálogo abiertos.</span><span class="sxs-lookup"><span data-stu-id="f78cf-115">**Topmost**: By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="f78cf-116">A continuación, cree un control de calendario y agréguelo al formulario.</span><span class="sxs-lookup"><span data-stu-id="f78cf-116">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="f78cf-117">En este ejemplo, el día actual no está resaltado o dentro de un círculo.</span><span class="sxs-lookup"><span data-stu-id="f78cf-117">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="f78cf-118">Los usuarios pueden seleccionar un solo día en el calendario cada vez.</span><span class="sxs-lookup"><span data-stu-id="f78cf-118">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="f78cf-119">A continuación, cree un botón **Aceptar** para el formulario.</span><span class="sxs-lookup"><span data-stu-id="f78cf-119">Next, create an **OK** button for your form.</span></span>
<span data-ttu-id="f78cf-120">Indique un tamaño y el comportamiento del botón **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="f78cf-120">Specify the size and behavior of the **OK** button.</span></span>
<span data-ttu-id="f78cf-121">En este ejemplo, la posición del botón es de 165 píxeles desde el borde superior del formulario y de 38 píxeles desde el borde izquierdo.</span><span class="sxs-lookup"><span data-stu-id="f78cf-121">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span>
<span data-ttu-id="f78cf-122">La altura del botón es 23 píxeles y la longitud, 75 píxeles.</span><span class="sxs-lookup"><span data-stu-id="f78cf-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span>
<span data-ttu-id="f78cf-123">El script usa tipos predefinidos de Windows Forms para definir el comportamiento del botón.</span><span class="sxs-lookup"><span data-stu-id="f78cf-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="f78cf-124">De manera similar, cree un botón **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="f78cf-124">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="f78cf-125">El botón **Cancelar** está a 165 píxeles de la parte superior, pero a 113 píxeles del borde izquierdo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="f78cf-125">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="f78cf-126">Agregue la siguiente línea de código para mostrar el formulario en Windows.</span><span class="sxs-lookup"><span data-stu-id="f78cf-126">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="f78cf-127">Por último, el código del bloque `if` indica a Windows qué hacer con el formulario después de que los usuarios seleccionen un día en el calendario y hagan clic en el botón **Aceptar** o presionen la tecla **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="f78cf-127">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span>
<span data-ttu-id="f78cf-128">Windows PowerShell muestra la fecha seleccionada a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="f78cf-128">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="f78cf-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="f78cf-129">See Also</span></span>

- <span data-ttu-id="f78cf-130">[Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644) (Hey Scripting Guy: ¿Por qué estos ejemplos de GUI de PowerShell no funcionan?)</span><span class="sxs-lookup"><span data-stu-id="f78cf-130">[Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644)</span></span>
- <span data-ttu-id="f78cf-131">[GitHub: ](https://github.com/dlwyatt/WinFormsExampleUpdates)Dave Wyatt's WinFormsExampleUpdates (GitHub: WinFormsExampleUpdates de Dave Wyatt)</span><span class="sxs-lookup"><span data-stu-id="f78cf-131">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)</span></span>
- <span data-ttu-id="f78cf-132">[Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker](https://technet.microsoft.com/library/ff730942.aspx) (Consejo de la semana de Windows PowerShell: crear un selector de fecha gráfico)</span><span class="sxs-lookup"><span data-stu-id="f78cf-132">[Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker](https://technet.microsoft.com/library/ff730942.aspx)</span></span>
