---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Quitar objetos de la canalización Where Object
ms.openlocfilehash: 370e7745341b70c0794352a690d5750d21f53ac2
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737192"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="9a1b6-103">Quitar objetos de la canalización (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="9a1b6-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="9a1b6-104">En PowerShell, se suelen generar y pasar más objetos de los deseados a una canalización.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-104">In PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="9a1b6-105">Puede especificar las propiedades de los objetos concretos que quiere que se muestren mediante los cmdlets `Format-*`, pero esto no ayuda a resolver el problema de eliminación de objetos completos de la presentación.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-105">You can specify the properties of particular objects to display by using the `Format-*` cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="9a1b6-106">Es posible que quiera filtrar objetos antes del final de una canalización, para poder realizar acciones solo en un subconjunto de los objetos generados inicialmente.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="9a1b6-107">PowerShell incluye el cmdlet `Where-Object`, que permite probar cada objeto de la canalización y pasarlo solo a la canalización si cumple una condición de prueba determinada.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-107">PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="9a1b6-108">Los objetos que no pasan la prueba se quitan de la canalización.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="9a1b6-109">Debe indicar la condición de prueba como el valor del parámetro **FilterScript**.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-109">You supply the test condition as the value of the **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="9a1b6-110">Realizar pruebas simples con Where-Object</span><span class="sxs-lookup"><span data-stu-id="9a1b6-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="9a1b6-111">El valor de **FilterScript** es un *bloque de script*; es decir, uno o más comandos de PowerShell entre llaves (`{}`), que se evalúa como true o false.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-111">The value of **FilterScript** is a *script block* - one or more PowerShell commands surrounded by braces (`{}`) - that evaluates to true or false.</span></span> <span data-ttu-id="9a1b6-112">Estos bloques de script pueden ser muy simples, pero su creación requiere el conocimiento de otro concepto de PowerShell: los operadores de comparación.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-112">These script blocks can be very simple, but creating them requires knowing about another PowerShell concept, comparison operators.</span></span> <span data-ttu-id="9a1b6-113">Un operador de comparación compara los elementos que aparecen en cada uno de sus lados.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="9a1b6-114">Los operadores de comparación comienzan con un carácter (`-`) seguido de un nombre.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-114">Comparison operators begin with a hyphen character (`-`) and are followed by a name.</span></span> <span data-ttu-id="9a1b6-115">Los operadores de comparación básicos funcionan en casi todos los tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="9a1b6-116">Es posible que los operadores de comparación más avanzados solo funcionen en texto o matrices.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="9a1b6-117">De manera predeterminada, al trabajar con texto, los operadores de comparación de PowerShell no distinguen mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-117">By default, when working with text, PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="9a1b6-118">Debido a consideraciones de análisis, los símbolos como `<`, `>` y `=` no se usan como operadores de comparación.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-118">Due to parsing considerations, symbols such as `<`,`>`, and `=` are not used as comparison operators.</span></span> <span data-ttu-id="9a1b6-119">En su lugar, los operadores de comparación están formados por letras.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="9a1b6-120">Los operadores lógicos básicos se muestran en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-120">The basic comparison operators are listed in the following table.</span></span>

| <span data-ttu-id="9a1b6-121">Operador de comparación</span><span class="sxs-lookup"><span data-stu-id="9a1b6-121">Comparison Operator</span></span> |                  <span data-ttu-id="9a1b6-122">Significado</span><span class="sxs-lookup"><span data-stu-id="9a1b6-122">Meaning</span></span>                   |    <span data-ttu-id="9a1b6-123">Ejemplo (devuelve true)</span><span class="sxs-lookup"><span data-stu-id="9a1b6-123">Example (returns true)</span></span>    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| <span data-ttu-id="9a1b6-124">-eq</span><span class="sxs-lookup"><span data-stu-id="9a1b6-124">-eq</span></span>                 | <span data-ttu-id="9a1b6-125">es igual a</span><span class="sxs-lookup"><span data-stu-id="9a1b6-125">is equal to</span></span>                                | <span data-ttu-id="9a1b6-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="9a1b6-126">1 -eq 1</span></span>                      |
| <span data-ttu-id="9a1b6-127">-ne</span><span class="sxs-lookup"><span data-stu-id="9a1b6-127">-ne</span></span>                 | <span data-ttu-id="9a1b6-128">No es igual a</span><span class="sxs-lookup"><span data-stu-id="9a1b6-128">Is not equal to</span></span>                            | <span data-ttu-id="9a1b6-129">1 -ne 2</span><span class="sxs-lookup"><span data-stu-id="9a1b6-129">1 -ne 2</span></span>                      |
| <span data-ttu-id="9a1b6-130">-lt</span><span class="sxs-lookup"><span data-stu-id="9a1b6-130">-lt</span></span>                 | <span data-ttu-id="9a1b6-131">Es menor que</span><span class="sxs-lookup"><span data-stu-id="9a1b6-131">Is less than</span></span>                               | <span data-ttu-id="9a1b6-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="9a1b6-132">1 -lt 2</span></span>                      |
| <span data-ttu-id="9a1b6-133">-le</span><span class="sxs-lookup"><span data-stu-id="9a1b6-133">-le</span></span>                 | <span data-ttu-id="9a1b6-134">Es menor o igual que</span><span class="sxs-lookup"><span data-stu-id="9a1b6-134">Is less than or equal to</span></span>                   | <span data-ttu-id="9a1b6-135">1 -le 2</span><span class="sxs-lookup"><span data-stu-id="9a1b6-135">1 -le 2</span></span>                      |
| <span data-ttu-id="9a1b6-136">-gt</span><span class="sxs-lookup"><span data-stu-id="9a1b6-136">-gt</span></span>                 | <span data-ttu-id="9a1b6-137">Es mayor que</span><span class="sxs-lookup"><span data-stu-id="9a1b6-137">Is greater than</span></span>                            | <span data-ttu-id="9a1b6-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="9a1b6-138">2 -gt 1</span></span>                      |
| <span data-ttu-id="9a1b6-139">-ge</span><span class="sxs-lookup"><span data-stu-id="9a1b6-139">-ge</span></span>                 | <span data-ttu-id="9a1b6-140">Es mayor o igual que</span><span class="sxs-lookup"><span data-stu-id="9a1b6-140">Is greater than or equal to</span></span>                | <span data-ttu-id="9a1b6-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="9a1b6-141">2 -ge 1</span></span>                      |
| <span data-ttu-id="9a1b6-142">-like</span><span class="sxs-lookup"><span data-stu-id="9a1b6-142">-like</span></span>               | <span data-ttu-id="9a1b6-143">Es como (comparación de comodín para texto)</span><span class="sxs-lookup"><span data-stu-id="9a1b6-143">Is like (wildcard comparison for text)</span></span>     | <span data-ttu-id="9a1b6-144">"file.doc" -like "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="9a1b6-144">"file.doc" -like "f\*.do?"</span></span>    |
| <span data-ttu-id="9a1b6-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="9a1b6-145">-notlike</span></span>            | <span data-ttu-id="9a1b6-146">No es como (comparación de comodín para texto)</span><span class="sxs-lookup"><span data-stu-id="9a1b6-146">Is not like (wildcard comparison for text)</span></span> | <span data-ttu-id="9a1b6-147">"file.doc" -notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="9a1b6-147">"file.doc" -notlike "p\*.doc"</span></span> |
| <span data-ttu-id="9a1b6-148">-contains</span><span class="sxs-lookup"><span data-stu-id="9a1b6-148">-contains</span></span>           | <span data-ttu-id="9a1b6-149">Contains</span><span class="sxs-lookup"><span data-stu-id="9a1b6-149">Contains</span></span>                                   | <span data-ttu-id="9a1b6-150">1,2,3 -contains 1</span><span class="sxs-lookup"><span data-stu-id="9a1b6-150">1,2,3 -contains 1</span></span>            |
| <span data-ttu-id="9a1b6-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="9a1b6-151">-notcontains</span></span>        | <span data-ttu-id="9a1b6-152">No contiene</span><span class="sxs-lookup"><span data-stu-id="9a1b6-152">Does not contain</span></span>                           | <span data-ttu-id="9a1b6-153">1,2,3 -notcontains 4</span><span class="sxs-lookup"><span data-stu-id="9a1b6-153">1,2,3 -notcontains 4</span></span>         |

<span data-ttu-id="9a1b6-154">Los bloques de script `Where-Object` usan la variable especial `$_` para hacer referencia al objeto actual en la canalización.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-154">`Where-Object` script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="9a1b6-155">A continuación se incluye un ejemplo de cómo funciona:</span><span class="sxs-lookup"><span data-stu-id="9a1b6-155">Here is an example of how it works.</span></span> <span data-ttu-id="9a1b6-156">Si tiene una lista de números y solo quiere que se devuelvan los que sean inferiores a 3, puede usar `Where-Object` para filtrar los números; para ello, escriba:</span><span class="sxs-lookup"><span data-stu-id="9a1b6-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use `Where-Object` to filter the numbers by typing:</span></span>

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="9a1b6-157">Filtrar por las propiedades de objeto</span><span class="sxs-lookup"><span data-stu-id="9a1b6-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="9a1b6-158">Dado que `$_` hace referencia al objeto de canalización actual, podemos acceder a sus propiedades para nuestras pruebas.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="9a1b6-159">Por ejemplo, podemos observar la clase **Win32_SystemDriver** en WMI.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-159">As an example, we can look at the **Win32_SystemDriver** class in WMI.</span></span> <span data-ttu-id="9a1b6-160">Puede haber cientos de controladores del sistema en un determinado sistema, pero puede que solo esté interesado en un conjunto concreto de estos controladores, como, por ejemplo, aquellos que se están ejecutando actualmente.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="9a1b6-161">En la clase **Win32_SystemDriver**, la propiedad pertinente es **State**.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-161">For the **Win32_SystemDriver** class the relevant property is **State**.</span></span> <span data-ttu-id="9a1b6-162">Para filtrar los controladores del sistema seleccione solo los que se estén ejecutando. Para ello, escriba:</span><span class="sxs-lookup"><span data-stu-id="9a1b6-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

<span data-ttu-id="9a1b6-163">Esto sigue produciendo una larga lista.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-163">This still produces a long list.</span></span> <span data-ttu-id="9a1b6-164">Es posible que también quiera filtrar para seleccionar solo los controladores configurados para iniciarse automáticamente al probar el valor **StartMode**:</span><span class="sxs-lookup"><span data-stu-id="9a1b6-164">You may want to filter to only select the drivers set to start automatically by testing the **StartMode** value as well:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
...
```

<span data-ttu-id="9a1b6-165">Esto nos da mucha información que ya no necesitamos porque sabemos que los controladores se están ejecutando.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span>
<span data-ttu-id="9a1b6-166">De hecho, los únicos datos que probablemente necesitamos en este momento son el nombre y el nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="9a1b6-167">El siguiente comando solo incluye esas dos propiedades, lo que produce una salida mucho más simple:</span><span class="sxs-lookup"><span data-stu-id="9a1b6-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

<span data-ttu-id="9a1b6-168">Hay dos elementos `Where-Object` en el comando anterior, pero puede expresarse en un único elemento `Where-Object` mediante el operador lógico `-and`, de manera similar a la siguiente:</span><span class="sxs-lookup"><span data-stu-id="9a1b6-168">There are two `Where-Object` elements in the above command, but they can be expressed in a single `Where-Object` element by using the `-and` logical operator, like this:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

<span data-ttu-id="9a1b6-169">Los operadores lógicos estándar se muestran en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="9a1b6-169">The standard logical operators are listed in the following table.</span></span>

| <span data-ttu-id="9a1b6-170">Operador lógico</span><span class="sxs-lookup"><span data-stu-id="9a1b6-170">Logical Operator</span></span> |                 <span data-ttu-id="9a1b6-171">Significado</span><span class="sxs-lookup"><span data-stu-id="9a1b6-171">Meaning</span></span>                  |  <span data-ttu-id="9a1b6-172">Ejemplo (devuelve true)</span><span class="sxs-lookup"><span data-stu-id="9a1b6-172">Example (returns true)</span></span>  |
| ---------------- | ---------------------------------------- | ------------------------ |
| <span data-ttu-id="9a1b6-173">-and</span><span class="sxs-lookup"><span data-stu-id="9a1b6-173">-and</span></span>             | <span data-ttu-id="9a1b6-174">Lógico and; true si ambos lados son true</span><span class="sxs-lookup"><span data-stu-id="9a1b6-174">Logical and; true if both sides are true</span></span> | <span data-ttu-id="9a1b6-175">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="9a1b6-175">(1 -eq 1) -and (2 -eq 2)</span></span> |
| <span data-ttu-id="9a1b6-176">-or</span><span class="sxs-lookup"><span data-stu-id="9a1b6-176">-or</span></span>              | <span data-ttu-id="9a1b6-177">Lógico or; true si algún lado es true</span><span class="sxs-lookup"><span data-stu-id="9a1b6-177">Logical or; true if either side is true</span></span>  | <span data-ttu-id="9a1b6-178">(1 -eq 1) -or (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="9a1b6-178">(1 -eq 1) -or (1 -eq 2)</span></span>  |
| <span data-ttu-id="9a1b6-179">-not</span><span class="sxs-lookup"><span data-stu-id="9a1b6-179">-not</span></span>             | <span data-ttu-id="9a1b6-180">Lógico not; invierte true y false</span><span class="sxs-lookup"><span data-stu-id="9a1b6-180">Logical not; reverses true and false</span></span>     | <span data-ttu-id="9a1b6-181">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="9a1b6-181">-not (1 -eq 2)</span></span>           |
| \!               | <span data-ttu-id="9a1b6-182">Lógico not; invierte true y false</span><span class="sxs-lookup"><span data-stu-id="9a1b6-182">Logical not; reverses true and false</span></span>     | <span data-ttu-id="9a1b6-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="9a1b6-183">\!(1 -eq 2)</span></span>              |
