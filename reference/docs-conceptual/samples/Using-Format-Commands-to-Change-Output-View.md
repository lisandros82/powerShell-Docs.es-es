---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Usar comandos de formato para cambiar la vista de salida
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 97d3a9e04abb61bb80a0b8c67d9fb9e885a0b91b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403122"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="42a15-103">Usar comandos de formato para cambiar la vista de salida</span><span class="sxs-lookup"><span data-stu-id="42a15-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="42a15-104">Windows PowerShell tiene un conjunto de cmdlets que permite controlar las propiedades que se muestran para determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="42a15-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="42a15-105">Los nombres de todos los cmdlets empiezan con el verbo **Format**.</span><span class="sxs-lookup"><span data-stu-id="42a15-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="42a15-106">Permiten seleccionar una o más propiedades para mostrar.</span><span class="sxs-lookup"><span data-stu-id="42a15-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="42a15-107">Los cmdlets **Format** son **Format-Wide**, **Format-List**, **Format-Table** y **Format-Custom**.</span><span class="sxs-lookup"><span data-stu-id="42a15-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="42a15-108">Solo describiremos los cmdlets **Format-Wide**, **Format-List** y **Format-Table** en esta guía de usuario.</span><span class="sxs-lookup"><span data-stu-id="42a15-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="42a15-109">Cada cmdlet de formato tiene propiedades predeterminadas que se usarán si no indica propiedades específicas para mostrar.</span><span class="sxs-lookup"><span data-stu-id="42a15-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="42a15-110">Asimismo, cada cmdlet usa el mismo nombre de parámetro, **Property**, para especificar las propiedades que se deben mostrar.</span><span class="sxs-lookup"><span data-stu-id="42a15-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="42a15-111">Dado que **Format-Wide** solo muestra una propiedad única, su parámetro **Property** solo toma un valor único, pero los parámetros de propiedad de **Format-List** y **Format-Table** aceptarán una lista de nombres de propiedad.</span><span class="sxs-lookup"><span data-stu-id="42a15-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="42a15-112">Si usa el comando **Get-Process -Name powershell** con dos instancias de ejecución de Windows PowerShell, obtendrá una salida similar a la siguiente:</span><span class="sxs-lookup"><span data-stu-id="42a15-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="42a15-113">En el resto de esta sección, exploraremos cómo usar los cmdlets **Format** para cambiar la manera en que se muestra la salida de este comando.</span><span class="sxs-lookup"><span data-stu-id="42a15-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

### <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="42a15-114">Usar Format-Wide para la salida de un solo elemento</span><span class="sxs-lookup"><span data-stu-id="42a15-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="42a15-115">De forma predeterminada, el cmdlet **Format-Wide** muestra solo la propiedad predeterminada de un objeto.</span><span class="sxs-lookup"><span data-stu-id="42a15-115">The **Format-Wide** cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="42a15-116">La información asociada a cada objeto se muestra en una sola columna:</span><span class="sxs-lookup"><span data-stu-id="42a15-116">The information associated with each object is displayed in a single column:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

<span data-ttu-id="42a15-117">También puede especificar una propiedad no predeterminada:</span><span class="sxs-lookup"><span data-stu-id="42a15-117">You can also specify a non-default property:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="42a15-118">Controlar la presentación de Format-Wide con Column</span><span class="sxs-lookup"><span data-stu-id="42a15-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="42a15-119">Con el cmdlet **Format-Wide**, solo puede mostrar una única propiedad a la vez.</span><span class="sxs-lookup"><span data-stu-id="42a15-119">With the **Format-Wide** cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="42a15-120">Resulta útil para mostrar listas simples que muestren solo un elemento por línea.</span><span class="sxs-lookup"><span data-stu-id="42a15-120">This makes it useful for displaying simple lists that show only one element per line.</span></span> <span data-ttu-id="42a15-121">Para obtener una lista simple, establezca el valor del parámetro **Column** en 1. Para ello, escriba:</span><span class="sxs-lookup"><span data-stu-id="42a15-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```powershell
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="42a15-122">Usar Format-List para obtener una vista de lista</span><span class="sxs-lookup"><span data-stu-id="42a15-122">Using Format-List for a List View</span></span>

<span data-ttu-id="42a15-123">El cmdlet **Format-List** muestra un objeto en forma de una lista, donde cada propiedad aparece etiquetada y en una línea diferente:</span><span class="sxs-lookup"><span data-stu-id="42a15-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="42a15-124">Puede especificar tantas propiedades como desee:</span><span class="sxs-lookup"><span data-stu-id="42a15-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="42a15-125">Obtener información detallada usando Format-List con caracteres comodín</span><span class="sxs-lookup"><span data-stu-id="42a15-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="42a15-126">El cmdlet **Format-List** permite usar un carácter comodín como valor de su parámetro **Property**.</span><span class="sxs-lookup"><span data-stu-id="42a15-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="42a15-127">Esto le permite visualizar información detallada.</span><span class="sxs-lookup"><span data-stu-id="42a15-127">This lets you display detailed information.</span></span> <span data-ttu-id="42a15-128">A menudo, los objetos incluyen más información de la que necesita, motivo por el cual Windows PowerShell no muestra todos los valores de propiedad de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="42a15-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="42a15-129">Para mostrar todas las propiedades de un objeto, use el comando **Format-List -Property \&#42;**.</span><span class="sxs-lookup"><span data-stu-id="42a15-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="42a15-130">El siguiente comando genera más de 60 líneas de salida para un único proceso:</span><span class="sxs-lookup"><span data-stu-id="42a15-130">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="42a15-131">Aunque el comando **Format-List** resulta útil para mostrar detalles, si desea una introducción de la salida que incluya muchos elementos, una vista tabular más sencilla suele ser más útil.</span><span class="sxs-lookup"><span data-stu-id="42a15-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

### <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="42a15-132">Usar Format-Table para la salida tabular</span><span class="sxs-lookup"><span data-stu-id="42a15-132">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="42a15-133">Si usa el cmdlet **Format-Table** sin ningún nombre de propiedad especificado para formatear la salida del comando **Get-Process**, obtendrá exactamente la misma salida que al aplicar cualquier formato.</span><span class="sxs-lookup"><span data-stu-id="42a15-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="42a15-134">El motivo es que los procesos se suelen mostrar en formato tabular, como la mayoría de los objetos de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42a15-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="42a15-135">Mejorar la salida de Format-Table (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="42a15-135">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="42a15-136">Aunque una vista tabular resulta útil para mostrar mucha información comparable, puede ser difícil de interpretar si la presentación es demasiado estrecha para los datos.</span><span class="sxs-lookup"><span data-stu-id="42a15-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="42a15-137">Por ejemplo, si intenta mostrar la ruta de acceso del proceso, el identificador, el nombre y la empresa, obtendrá una salida truncada para la ruta de acceso del proceso y la columna de la empresa:</span><span class="sxs-lookup"><span data-stu-id="42a15-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="42a15-138">Si especifica el parámetro **AutoSize** al ejecutar el comando **Format-Table**, Windows PowerShell calculará los anchos de columna en función de los datos reales que va a mostrar.</span><span class="sxs-lookup"><span data-stu-id="42a15-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="42a15-139">Esto hace que la columna **Path** se pueda leer, pero la columna de la empresa sigue estando truncada:</span><span class="sxs-lookup"><span data-stu-id="42a15-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="42a15-140">El cmdlet **Format-Table** todavía podría truncar datos, pero solo lo hace al final de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="42a15-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="42a15-141">Las propiedades distintas de la última que se muestra obtienen el tamaño que necesitan para que su elemento de datos más largo se muestre correctamente.</span><span class="sxs-lookup"><span data-stu-id="42a15-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="42a15-142">Puede ver que el nombre de la empresa es visible, pero la ruta de acceso está truncada si intercambia las ubicaciones de **Path** y **Company** en la lista de valores **Property**:</span><span class="sxs-lookup"><span data-stu-id="42a15-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="42a15-143">El comando **Format-Table** supone que, cuanto más cerca está una propiedad del principio de la lista de propiedades, más importante es.</span><span class="sxs-lookup"><span data-stu-id="42a15-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="42a15-144">Por tanto, intenta mostrar las propiedades lo más cerca posible del principio.</span><span class="sxs-lookup"><span data-stu-id="42a15-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="42a15-145">Si el comando **Format-Table** no puede mostrar todas las propiedades, quitará algunas columnas de la presentación y mostrará una advertencia.</span><span class="sxs-lookup"><span data-stu-id="42a15-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="42a15-146">Puede ver este comportamiento si hace que **Name** sea la última propiedad de la lista:</span><span class="sxs-lookup"><span data-stu-id="42a15-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="42a15-147">En la salida anterior, la columna ID se ha truncado para caber en la lista y los encabezados de columna están apilados.</span><span class="sxs-lookup"><span data-stu-id="42a15-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="42a15-148">El cambio automático del tamaño de las columnas no siempre produce el resultado deseado.</span><span class="sxs-lookup"><span data-stu-id="42a15-148">Automatically resizing the columns does not always do what you want.</span></span>

#### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="42a15-149">Ajustar la salida de Format-Table en columnas (Wrap)</span><span class="sxs-lookup"><span data-stu-id="42a15-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="42a15-150">Puede forzar los datos de **Format-Table** extensos para ajustar la columna de presentación mediante el parámetro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="42a15-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="42a15-151">El parámetro **Wrap** solo no realizará necesariamente la acción prevista, ya que usa la configuración predeterminada si no se especifica también **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="42a15-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="42a15-152">Una ventaja de usar el parámetro **Wrap** solo es no ralentiza en exceso el procesamiento.</span><span class="sxs-lookup"><span data-stu-id="42a15-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="42a15-153">Si realiza una lista de archivo recursiva de un sistema de directorio de gran tamaño, podría tardar mucho tiempo y usar una gran cantidad de memoria antes de mostrar los primeros elementos de salida si usa **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="42a15-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="42a15-154">Si no le preocupa la carga del sistema, **AutoSize** funciona bien con el parámetro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="42a15-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="42a15-155">Siempre se asigna el ancho necesario a las columnas iniciales, ya que deben mostrar los elementos en una sola línea, al igual que cuando se especifica **AutoSize** sin el parámetro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="42a15-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="42a15-156">La única diferencia es que la última columna se ajustará si es necesario:</span><span class="sxs-lookup"><span data-stu-id="42a15-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="42a15-157">Es posible que algunas columnas no se muestren correctamente si especifica primero las columnas más anchas, por lo que es más seguro especificar los elementos de datos más pequeños en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="42a15-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="42a15-158">En el siguiente ejemplo, especificamos el elemento de ruta de acceso extremadamente ancho en primer lugar y, a pesar del ajuste, perdemos la columna **Name** final:</span><span class="sxs-lookup"><span data-stu-id="42a15-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a><span data-ttu-id="42a15-159">Organización de la salida tabular (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="42a15-159">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="42a15-160">Otro parámetro útil para el control de la salida tabular es **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="42a15-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="42a15-161">Las listas tabulares largas pueden ser especialmente difíciles de comparar.</span><span class="sxs-lookup"><span data-stu-id="42a15-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="42a15-162">El parámetro **GroupBy** agrupa la salida según un valor de propiedad.</span><span class="sxs-lookup"><span data-stu-id="42a15-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="42a15-163">Por ejemplo, podemos agrupar procesos por empresa para facilitar la inspección. Para ello, se omite el valor de la empresa de la lista de propiedades:</span><span class="sxs-lookup"><span data-stu-id="42a15-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```