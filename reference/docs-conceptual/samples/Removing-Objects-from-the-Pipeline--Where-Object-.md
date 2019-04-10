---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Quitar objetos de la canalización Where Object
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 1f7d064c7bf2dd551ea96b29762fbccad8174084
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293153"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="a1f63-103">Quitar objetos de la canalización (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="a1f63-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="a1f63-104">En Windows PowerShell, se suelen generar y pasar más objetos de los deseados a una canalización.</span><span class="sxs-lookup"><span data-stu-id="a1f63-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="a1f63-105">Puede especificar las propiedades de los objetos concretos que quiere que se muestren mediante los cmdlets **Format**, pero esto no ayuda a resolver el problema de eliminación de objetos completos de la presentación.</span><span class="sxs-lookup"><span data-stu-id="a1f63-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="a1f63-106">Es posible que quiera filtrar objetos antes del final de una canalización, para poder realizar acciones solo en un subconjunto de los objetos generados inicialmente.</span><span class="sxs-lookup"><span data-stu-id="a1f63-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="a1f63-107">Windows PowerShell incluye el cmdlet`Where-Object`, que permite probar cada objeto de la canalización y pasarlo solo a la canalización si cumple una condición de prueba determinada.</span><span class="sxs-lookup"><span data-stu-id="a1f63-107">Windows PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="a1f63-108">Los objetos que no pasan la prueba se quitan de la canalización.</span><span class="sxs-lookup"><span data-stu-id="a1f63-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="a1f63-109">Debe indicar la condición de prueba como el valor del parámetro `Where-Object` **FilterScript**.</span><span class="sxs-lookup"><span data-stu-id="a1f63-109">You supply the test condition as the value of the `Where-Object` **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="a1f63-110">Realizar pruebas simples con Where-Object</span><span class="sxs-lookup"><span data-stu-id="a1f63-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="a1f63-111">El valor de **FilterScript** es un *bloque de script*; es decir, uno o más comandos de Windows PowerShell entre llaves {}, que se evalúa como true o false.</span><span class="sxs-lookup"><span data-stu-id="a1f63-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="a1f63-112">Estos bloques de script pueden ser muy simples, pero su creación requiere el conocimiento de otro concepto de Windows PowerShell: los operadores de comparación.</span><span class="sxs-lookup"><span data-stu-id="a1f63-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="a1f63-113">Un operador de comparación compara los elementos que aparecen en cada uno de sus lados.</span><span class="sxs-lookup"><span data-stu-id="a1f63-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="a1f63-114">Los operadores de comparación comienzan con un carácter '-' seguido de un nombre.</span><span class="sxs-lookup"><span data-stu-id="a1f63-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="a1f63-115">Los operadores de comparación básicos funcionan en casi todos los tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="a1f63-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="a1f63-116">Es posible que los operadores de comparación más avanzados solo funcionen en texto o matrices.</span><span class="sxs-lookup"><span data-stu-id="a1f63-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="a1f63-117">De manera predeterminada, al trabajar con texto, los operadores de comparación de Windows PowerShell no distinguen mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="a1f63-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="a1f63-118">Debido a consideraciones de análisis, los símbolos como <, > y = no se usan como operadores de comparación.</span><span class="sxs-lookup"><span data-stu-id="a1f63-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="a1f63-119">En su lugar, los operadores de comparación están formados por letras.</span><span class="sxs-lookup"><span data-stu-id="a1f63-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="a1f63-120">Los operadores lógicos básicos se muestran en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="a1f63-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="a1f63-121">Operador de comparación</span><span class="sxs-lookup"><span data-stu-id="a1f63-121">Comparison Operator</span></span>|<span data-ttu-id="a1f63-122">Significado</span><span class="sxs-lookup"><span data-stu-id="a1f63-122">Meaning</span></span>|<span data-ttu-id="a1f63-123">Ejemplo (devuelve true)</span><span class="sxs-lookup"><span data-stu-id="a1f63-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="a1f63-124">-eq</span><span class="sxs-lookup"><span data-stu-id="a1f63-124">-eq</span></span>|<span data-ttu-id="a1f63-125">es igual a</span><span class="sxs-lookup"><span data-stu-id="a1f63-125">is equal to</span></span>|<span data-ttu-id="a1f63-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="a1f63-126">1 -eq 1</span></span>|
|<span data-ttu-id="a1f63-127">-ne</span><span class="sxs-lookup"><span data-stu-id="a1f63-127">-ne</span></span>|<span data-ttu-id="a1f63-128">No es igual a</span><span class="sxs-lookup"><span data-stu-id="a1f63-128">Is not equal to</span></span>|<span data-ttu-id="a1f63-129">1 -ne 2</span><span class="sxs-lookup"><span data-stu-id="a1f63-129">1 -ne 2</span></span>|
|<span data-ttu-id="a1f63-130">-lt</span><span class="sxs-lookup"><span data-stu-id="a1f63-130">-lt</span></span>|<span data-ttu-id="a1f63-131">Es menor que</span><span class="sxs-lookup"><span data-stu-id="a1f63-131">Is less than</span></span>|<span data-ttu-id="a1f63-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="a1f63-132">1 -lt 2</span></span>|
|<span data-ttu-id="a1f63-133">-le</span><span class="sxs-lookup"><span data-stu-id="a1f63-133">-le</span></span>|<span data-ttu-id="a1f63-134">Es menor o igual que</span><span class="sxs-lookup"><span data-stu-id="a1f63-134">Is less than or equal to</span></span>|<span data-ttu-id="a1f63-135">1 -le 2</span><span class="sxs-lookup"><span data-stu-id="a1f63-135">1 -le 2</span></span>|
|<span data-ttu-id="a1f63-136">-gt</span><span class="sxs-lookup"><span data-stu-id="a1f63-136">-gt</span></span>|<span data-ttu-id="a1f63-137">Es mayor que</span><span class="sxs-lookup"><span data-stu-id="a1f63-137">Is greater than</span></span>|<span data-ttu-id="a1f63-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="a1f63-138">2 -gt 1</span></span>|
|<span data-ttu-id="a1f63-139">-ge</span><span class="sxs-lookup"><span data-stu-id="a1f63-139">-ge</span></span>|<span data-ttu-id="a1f63-140">Es mayor o igual que</span><span class="sxs-lookup"><span data-stu-id="a1f63-140">Is greater than or equal to</span></span>|<span data-ttu-id="a1f63-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="a1f63-141">2 -ge 1</span></span>|
|<span data-ttu-id="a1f63-142">-like</span><span class="sxs-lookup"><span data-stu-id="a1f63-142">-like</span></span>|<span data-ttu-id="a1f63-143">Es como (comparación de comodín para texto)</span><span class="sxs-lookup"><span data-stu-id="a1f63-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="a1f63-144">"file.doc" -like "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="a1f63-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="a1f63-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="a1f63-145">-notlike</span></span>|<span data-ttu-id="a1f63-146">No es como (comparación de comodín para texto)</span><span class="sxs-lookup"><span data-stu-id="a1f63-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="a1f63-147">"file.doc" -notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="a1f63-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="a1f63-148">-contains</span><span class="sxs-lookup"><span data-stu-id="a1f63-148">-contains</span></span>|<span data-ttu-id="a1f63-149">Contiene</span><span class="sxs-lookup"><span data-stu-id="a1f63-149">Contains</span></span>|<span data-ttu-id="a1f63-150">1,2,3 -contains 1</span><span class="sxs-lookup"><span data-stu-id="a1f63-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="a1f63-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="a1f63-151">-notcontains</span></span>|<span data-ttu-id="a1f63-152">No contiene</span><span class="sxs-lookup"><span data-stu-id="a1f63-152">Does not contain</span></span>|<span data-ttu-id="a1f63-153">1,2,3 -notcontains 4</span><span class="sxs-lookup"><span data-stu-id="a1f63-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="a1f63-154">Los bloques de script Where-Object usan la variable especial `$_` para hacer referencia al objeto actual en la canalización.</span><span class="sxs-lookup"><span data-stu-id="a1f63-154">Where-Object script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="a1f63-155">A continuación se incluye un ejemplo de cómo funciona:</span><span class="sxs-lookup"><span data-stu-id="a1f63-155">Here is an example of how it works.</span></span> <span data-ttu-id="a1f63-156">Si tiene una lista de números y solo quiere que se devuelvan los que sean inferiores a 3, puede usar Where-Object para filtrar los números. Para ellos, escriba:</span><span class="sxs-lookup"><span data-stu-id="a1f63-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="a1f63-157">Filtrar por las propiedades de objeto</span><span class="sxs-lookup"><span data-stu-id="a1f63-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="a1f63-158">Dado que `$_` hace referencia al objeto de canalización actual, podemos acceder a sus propiedades para nuestras pruebas.</span><span class="sxs-lookup"><span data-stu-id="a1f63-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="a1f63-159">Por ejemplo, podemos observar la clase Win32_SystemDriver en WMI.</span><span class="sxs-lookup"><span data-stu-id="a1f63-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="a1f63-160">Puede haber cientos de controladores del sistema en un determinado sistema, pero puede que solo esté interesado en un conjunto concreto de estos controladores, como, por ejemplo, aquellos que se están ejecutando actualmente.</span><span class="sxs-lookup"><span data-stu-id="a1f63-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="a1f63-161">Si usa Get-Member para ver los miembros de Win32_SystemDriver (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**), verá que la propiedad correspondiente es State y que tiene un valor "Running" cuando se ejecuta el controlador.</span><span class="sxs-lookup"><span data-stu-id="a1f63-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="a1f63-162">Para filtrar los controladores del sistema seleccione solo los que se estén ejecutando. Para ello, escriba:</span><span class="sxs-lookup"><span data-stu-id="a1f63-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

<span data-ttu-id="a1f63-163">Esto sigue produciendo una larga lista.</span><span class="sxs-lookup"><span data-stu-id="a1f63-163">This still produces a long list.</span></span> <span data-ttu-id="a1f63-164">Es posible que también quiera filtrar para seleccionar solo los controladores configurados para iniciarse automáticamente al probar el valor StartMode:</span><span class="sxs-lookup"><span data-stu-id="a1f63-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

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
```

<span data-ttu-id="a1f63-165">Esto nos da mucha información que ya no necesitamos porque sabemos que los controladores se están ejecutando.</span><span class="sxs-lookup"><span data-stu-id="a1f63-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="a1f63-166">De hecho, los únicos datos que probablemente necesitamos en este momento son el nombre y el nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="a1f63-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="a1f63-167">El siguiente comando solo incluye esas dos propiedades, lo que produce una salida mucho más simple:</span><span class="sxs-lookup"><span data-stu-id="a1f63-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

<span data-ttu-id="a1f63-168">Hay dos elementos Where-Object en el comando anterior, pero puede expresarse en un único elemento Where-Object mediante el operador lógico -and, de manera similar a la siguiente:</span><span class="sxs-lookup"><span data-stu-id="a1f63-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="a1f63-169">Los operadores lógicos estándar se muestran en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="a1f63-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="a1f63-170">Operador lógico</span><span class="sxs-lookup"><span data-stu-id="a1f63-170">Logical Operator</span></span>|<span data-ttu-id="a1f63-171">Significado</span><span class="sxs-lookup"><span data-stu-id="a1f63-171">Meaning</span></span>|<span data-ttu-id="a1f63-172">Ejemplo (devuelve true)</span><span class="sxs-lookup"><span data-stu-id="a1f63-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="a1f63-173">-and</span><span class="sxs-lookup"><span data-stu-id="a1f63-173">-and</span></span>|<span data-ttu-id="a1f63-174">Lógico and; true si ambos lados son true</span><span class="sxs-lookup"><span data-stu-id="a1f63-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="a1f63-175">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="a1f63-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="a1f63-176">-or</span><span class="sxs-lookup"><span data-stu-id="a1f63-176">-or</span></span>|<span data-ttu-id="a1f63-177">Lógico or; true si algún lado es true</span><span class="sxs-lookup"><span data-stu-id="a1f63-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="a1f63-178">(1 -eq 1) -or (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="a1f63-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="a1f63-179">-not</span><span class="sxs-lookup"><span data-stu-id="a1f63-179">-not</span></span>|<span data-ttu-id="a1f63-180">Lógico not; invierte true y false</span><span class="sxs-lookup"><span data-stu-id="a1f63-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="a1f63-181">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="a1f63-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="a1f63-182">Lógico not; invierte true y false</span><span class="sxs-lookup"><span data-stu-id="a1f63-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="a1f63-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="a1f63-183">\!(1 -eq 2)</span></span>|
