---
ms.date: 11/22/2019
keywords: powershell, cmdlet
title: Usar comandos de formato para cambiar la vista de salida
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417595"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="6292e-103">Usar comandos de formato para cambiar la vista de salida</span><span class="sxs-lookup"><span data-stu-id="6292e-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="6292e-104">PowerShell tiene un conjunto de cmdlets que permite controlar cómo se muestran las propiedades para determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="6292e-104">PowerShell has a set of cmdlets that allow you to control how properties are displayed for particular objects.</span></span> <span data-ttu-id="6292e-105">Los nombres de todos los cmdlets empiezan con el verbo `Format`.</span><span class="sxs-lookup"><span data-stu-id="6292e-105">The names of all the cmdlets begin with the verb `Format`.</span></span> <span data-ttu-id="6292e-106">Permiten seleccionar las propiedades que se quieren mostrar.</span><span class="sxs-lookup"><span data-stu-id="6292e-106">They let you select which properties you want to show.</span></span>

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

<span data-ttu-id="6292e-107">En este artículo se describen los cmdlets `Format-Wide`, `Format-List` y `Format-Table`.</span><span class="sxs-lookup"><span data-stu-id="6292e-107">This article describes the `Format-Wide`, `Format-List`, and `Format-Table` cmdlets.</span></span>

<span data-ttu-id="6292e-108">Cada tipo de objeto de PowerShell tiene propiedades predeterminadas que se usan si no se especifican las propiedades que se van a mostrar.</span><span class="sxs-lookup"><span data-stu-id="6292e-108">Each object type in PowerShell has default properties that are used when you don't specify which properties to display.</span></span> <span data-ttu-id="6292e-109">Cada cmdlet usa el mismo parámetro **Property** para especificar las propiedades que se quieren mostrar.</span><span class="sxs-lookup"><span data-stu-id="6292e-109">Each cmdlet also uses the same **Property** parameter to specify which properties you want to display.</span></span> <span data-ttu-id="6292e-110">Como `Format-Wide` solo muestra una única propiedad, su parámetro **Property** solo toma un único valor, pero los parámetros de propiedad de `Format-List` y `Format-Table` aceptan una lista de nombres de propiedades.</span><span class="sxs-lookup"><span data-stu-id="6292e-110">Because `Format-Wide` only shows a single property, its **Property** parameter only takes a single value, but the property parameters of `Format-List` and `Format-Table` accept a list of property names.</span></span>

<span data-ttu-id="6292e-111">En este ejemplo, la salida predeterminada del cmdlet `Get-Process` muestra que hay dos instancias de Internet Explorer en ejecución.</span><span class="sxs-lookup"><span data-stu-id="6292e-111">In this example, the default output of `Get-Process` cmdlet shows that we have two instances of Internet Explorer running.</span></span>

```powershell
Get-Process -Name iexplore
```

<span data-ttu-id="6292e-112">El formato predeterminado de los objetos **Process** muestra estas propiedades:</span><span class="sxs-lookup"><span data-stu-id="6292e-112">The default format for **Process** objects displays the properties shown here:</span></span>

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="6292e-113">Usar Format-Wide para la salida de un solo elemento</span><span class="sxs-lookup"><span data-stu-id="6292e-113">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="6292e-114">De manera predeterminada, el cmdlet `Format-Wide` solo muestra la propiedad predeterminada de un objeto.</span><span class="sxs-lookup"><span data-stu-id="6292e-114">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="6292e-115">La información asociada a cada objeto se muestra en una sola columna:</span><span class="sxs-lookup"><span data-stu-id="6292e-115">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

<span data-ttu-id="6292e-116">También puede especificar una propiedad no predeterminada:</span><span class="sxs-lookup"><span data-stu-id="6292e-116">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="6292e-117">Controlar la presentación de Format-Wide con Column</span><span class="sxs-lookup"><span data-stu-id="6292e-117">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="6292e-118">Con el cmdlet `Format-Wide`, no se pueden varias propiedades a la vez.</span><span class="sxs-lookup"><span data-stu-id="6292e-118">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="6292e-119">Esto resulta útil para mostrar listas grandes en varias columnas.</span><span class="sxs-lookup"><span data-stu-id="6292e-119">This makes it useful for displaying large lists in multiple columns.</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="6292e-120">Usar Format-List para obtener una vista de lista</span><span class="sxs-lookup"><span data-stu-id="6292e-120">Using Format-List for a List View</span></span>

<span data-ttu-id="6292e-121">El cmdlet `Format-List` muestra un objeto en forma de lista, donde cada propiedad aparece etiquetada en una línea distinta:</span><span class="sxs-lookup"><span data-stu-id="6292e-121">The `Format-List` cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

<span data-ttu-id="6292e-122">Puede especificar tantas propiedades como desee:</span><span class="sxs-lookup"><span data-stu-id="6292e-122">You can specify as many properties as you want:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="6292e-123">Obtener información detallada usando Format-List con caracteres comodín</span><span class="sxs-lookup"><span data-stu-id="6292e-123">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="6292e-124">El cmdlet `Format-List` permite usar un carácter comodín como valor de su parámetro **Property**.</span><span class="sxs-lookup"><span data-stu-id="6292e-124">The `Format-List` cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="6292e-125">Esto le permite visualizar información detallada.</span><span class="sxs-lookup"><span data-stu-id="6292e-125">This lets you display detailed information.</span></span> <span data-ttu-id="6292e-126">A menudo, los objetos incluyen más información de la necesaria, por lo que PowerShell no muestra todos los valores de propiedad de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="6292e-126">Often, objects include more information than you need, which is why PowerShell doesn't show all property values by default.</span></span> <span data-ttu-id="6292e-127">Para mostrar todas las propiedades de un objeto, use el comando `Format-List -Property *`.</span><span class="sxs-lookup"><span data-stu-id="6292e-127">To show all of properties of an object, use the `Format-List -Property *` command.</span></span> <span data-ttu-id="6292e-128">El siguiente comando genera más de 60 líneas de salida para un único proceso:</span><span class="sxs-lookup"><span data-stu-id="6292e-128">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

<span data-ttu-id="6292e-129">Aunque el comando `Format-List` resulta útil para mostrar detalles, si quiere una visión general de la salida que incluya muchos elementos, una vista tabular más sencilla suele ser más conveniente.</span><span class="sxs-lookup"><span data-stu-id="6292e-129">Although the `Format-List` command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="6292e-130">Usar Format-Table para la salida tabular</span><span class="sxs-lookup"><span data-stu-id="6292e-130">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="6292e-131">Si usa el cmdlet `Format-Table` sin nombres de propiedades especificados para dar formato a la salida del comando `Get-Process`, obtendrá exactamente la misma salida que sin un cmdlet `Format`.</span><span class="sxs-lookup"><span data-stu-id="6292e-131">If you use the `Format-Table` cmdlet with no property names specified to format the output of the `Get-Process` command, you get exactly the same output as you do without a `Format` cmdlet.</span></span> <span data-ttu-id="6292e-132">De forma predeterminada, PowerShell muestra los objetos **Process** en formato tabular.</span><span class="sxs-lookup"><span data-stu-id="6292e-132">By default, PowerShell displays **Process** objects in a tabular format.</span></span>

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="6292e-133">Mejorar la salida de Format-Table (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="6292e-133">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="6292e-134">Aunque una vista tabular resulta útil para mostrar mucha información, puede ser difícil de interpretar si la pantalla es demasiado estrecha para los datos.</span><span class="sxs-lookup"><span data-stu-id="6292e-134">Although a tabular view is useful for displaying lots of information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="6292e-135">En el ejemplo anterior, el resultado se trunca.</span><span class="sxs-lookup"><span data-stu-id="6292e-135">In the previous example, the output is truncated.</span></span> <span data-ttu-id="6292e-136">Si especifica el parámetro **AutoSize** al ejecutar el comando `Format-Table`, PowerShell calcula los anchos de columna en función de los datos reales que se muestran.</span><span class="sxs-lookup"><span data-stu-id="6292e-136">If you specify the **AutoSize** parameter when you run the `Format-Table` command, PowerShell calculates column widths based on the actual data displayed.</span></span> <span data-ttu-id="6292e-137">Esto hace que las columnas sean legibles.</span><span class="sxs-lookup"><span data-stu-id="6292e-137">This makes the columns readable.</span></span>

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

<span data-ttu-id="6292e-138">Es posible que el cmdlet `Format-Table` todavía trunque los datos, pero solo al final de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="6292e-138">The `Format-Table` cmdlet might still truncate data, but it only truncates at the end of the screen.</span></span> <span data-ttu-id="6292e-139">Las propiedades distintas de la última que se muestra obtienen el tamaño que necesitan para que su elemento de datos más largo se muestre correctamente.</span><span class="sxs-lookup"><span data-stu-id="6292e-139">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="6292e-140">El comando `Format-Table` asume que las propiedades se enumeran por orden de importancia.</span><span class="sxs-lookup"><span data-stu-id="6292e-140">The `Format-Table` command assumes that properties are listed in order of importance.</span></span> <span data-ttu-id="6292e-141">Por tanto, intenta mostrar de forma completa las propiedades lo más cerca posible del principio.</span><span class="sxs-lookup"><span data-stu-id="6292e-141">So it attempts to fully display the properties nearest the beginning.</span></span> <span data-ttu-id="6292e-142">Si el comando `Format-Table` no puede mostrar todas las propiedades, quita algunas columnas de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="6292e-142">If the `Format-Table` command can't display all the properties, it removes some columns from the display.</span></span> <span data-ttu-id="6292e-143">Puede ver este comportamiento en el ejemplo anterior de la propiedad **DependentServices**.</span><span class="sxs-lookup"><span data-stu-id="6292e-143">You can see this behavior in the **DependentServices** property previous example.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="6292e-144">Ajustar la salida de Format-Table en columnas (Wrap)</span><span class="sxs-lookup"><span data-stu-id="6292e-144">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="6292e-145">Puede forzar que los datos de `Format-Table` largos se encapsulen dentro de la columna de presentación mediante el parámetro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="6292e-145">You can force lengthy `Format-Table` data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="6292e-146">Es posible que el parámetro **Wrap** no realice la acción prevista, ya que usa la configuración predeterminada si no se especifica también **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="6292e-146">Using the **Wrap** parameter may not do what you expect, since it uses default settings if you don't also specify **AutoSize**:</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="6292e-147">El uso del parámetro **Wrap** por sí solo no ralentiza en exceso el procesamiento.</span><span class="sxs-lookup"><span data-stu-id="6292e-147">Using the **Wrap** parameter by itself doesn't slow down processing very much.</span></span> <span data-ttu-id="6292e-148">Sin embargo, el uso de **AutoSize** para dar formato a una lista de archivos recursiva de una estructura de directorios de gran tamaño puede tardar mucho tiempo y consumir una gran cantidad de memoria antes de que se muestren los primeros elementos de la salida.</span><span class="sxs-lookup"><span data-stu-id="6292e-148">However, using **AutoSize** to format a recursive file listing of a large directory structure can take a long time and use lots of memory before displaying the first output items.</span></span>

<span data-ttu-id="6292e-149">Si no le preocupa la carga del sistema, **AutoSize** funciona bien con el parámetro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="6292e-149">If you aren't concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span>
<span data-ttu-id="6292e-150">Las columnas iniciales siguen usando todo el ancho necesario para mostrar los elementos en una línea, pero la columna final se ajusta, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="6292e-150">The initial columns still use as much width as needed to display items on one line, but the final column is wrapped, if necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="6292e-151">Es posible que algunas columnas no se muestren si se especifican primero las más anchas.</span><span class="sxs-lookup"><span data-stu-id="6292e-151">Some columns may not be displayed when you specify the widest columns first.</span></span> <span data-ttu-id="6292e-152">Para obtener los mejores resultados, especifique primero los elementos de datos más pequeños.</span><span class="sxs-lookup"><span data-stu-id="6292e-152">For best results, specify the smallest data elements first.</span></span>

<span data-ttu-id="6292e-153">En el ejemplo siguiente, primero se especifican las propiedades más anchas.</span><span class="sxs-lookup"><span data-stu-id="6292e-153">In the following example, we specify the widest properties first.</span></span>

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

<span data-ttu-id="6292e-154">Incluso con el ajuste, se omite la columna **Id** final:</span><span class="sxs-lookup"><span data-stu-id="6292e-154">Even with wrapping, the final **Id** column is omitted:</span></span>

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="6292e-155">Organización de la salida tabular (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="6292e-155">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="6292e-156">Otro parámetro útil para el control de la salida tabular es **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="6292e-156">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="6292e-157">Las listas tabulares largas pueden ser especialmente difíciles de comparar.</span><span class="sxs-lookup"><span data-stu-id="6292e-157">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="6292e-158">El parámetro **GroupBy** agrupa la salida según un valor de propiedad.</span><span class="sxs-lookup"><span data-stu-id="6292e-158">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="6292e-159">Por ejemplo, los servicios se pueden agrupar por valor **StartType** para facilitar la inspección y omitir el valor **StartType** de la lista de propiedades:</span><span class="sxs-lookup"><span data-stu-id="6292e-159">For example, we can group services by **StartType** for easier inspection, omitting the **StartType** value from the property listing:</span></span>

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
