---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Crear un selector de fecha gráfico
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: d3b24af935e781a8a36fc346a6108baaed37b6db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058614"
---
# <a name="creating-a-graphical-date-picker"></a>Crear un selector de fecha gráfico

Use Windows PowerShell 3.0 (y versiones posteriores) para crear un formulario con un control gráfico de estilo de calendario que permita a los usuarios seleccionar un día del mes.

## <a name="create-a-graphical-date-picker-control"></a>Crear un control gráfico de selector de fecha

Copie y pegue lo siguiente en Windows PowerShell ISE y, después, guárdelo como un script de Windows PowerShell (.ps1).

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

El script comienza con la carga de dos clases de .NET Framework: **System.Drawing** y **System.Windows.Forms**.
A continuación, inicie una nueva instancia de la clase de .NET Framework **Windows.Forms.Form**, que proporciona un formulario o una ventana en blanco en la que puede empezar a agregar controles.

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

En este ejemplo se asignan valores a cuatro propiedades de esta clase mediante la propiedad **Property** y la tabla hash.

1. **StartPosition**: Si no agrega esta propiedad, Windows selecciona una ubicación cuando el formulario se abre.
   Al establecer esta propiedad en **CenterScreen**, el formulario aparece automáticamente en el centro de la pantalla cada vez que se carga.

2. **Size**: Es el tamaño del formulario en píxeles.
   El script anterior crea un formulario de 243 píxeles de ancho y 230 píxeles de alto.

3. **Text**: Es el título de la ventana.

4. **Topmost**: Al establecer esta propiedad en `$true`, puede forzar a que la ventana se abra encima del resto de ventanas y cuadros de diálogo abiertos.

A continuación, cree un control de calendario y agréguelo al formulario.
En este ejemplo, el día actual no está resaltado o dentro de un círculo.
Los usuarios pueden seleccionar un solo día en el calendario cada vez.

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

A continuación, cree un botón **Aceptar** para el formulario.
Indique un tamaño y el comportamiento del botón **Aceptar**.
En este ejemplo, la posición del botón es de 165 píxeles desde el borde superior del formulario y de 38 píxeles desde el borde izquierdo.
La altura del botón es 23 píxeles y la longitud, 75 píxeles.
El script usa tipos predefinidos de Windows Forms para definir el comportamiento del botón.

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

De manera similar, cree un botón **Cancelar**.
El botón **Cancelar** está a 165 píxeles de la parte superior, pero a 113 píxeles del borde izquierdo de la ventana.

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

Agregue la siguiente línea de código para mostrar el formulario en Windows.

```powershell
$result = $form.ShowDialog()
```

Por último, el código del bloque `if` indica a Windows qué hacer con el formulario después de que los usuarios seleccionen un día en el calendario y hagan clic en el botón **Aceptar** o presionen la tecla **Entrar**.
Windows PowerShell muestra la fecha seleccionada a los usuarios.

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Véase también

- [Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644) (Hey Scripting Guy: ¿Por qué estos ejemplos de GUI de PowerShell no funcionan?)
- [GitHub: ](https://github.com/dlwyatt/WinFormsExampleUpdates)Dave Wyatt's WinFormsExampleUpdates (GitHub: WinFormsExampleUpdates de Dave Wyatt)
- [Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker](https://technet.microsoft.com/library/ff730942.aspx) (Consejo de la semana de Windows PowerShell: crear un selector de fecha gráfico)