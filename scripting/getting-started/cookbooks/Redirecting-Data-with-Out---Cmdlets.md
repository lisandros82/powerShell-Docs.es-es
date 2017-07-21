---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Redirigir datos con cmdlets Out
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: e570ca1c2c665a4a5d23abb50d4102a012b160e9
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="69ab5-103">Redirigir datos con cmdlets Out-*</span><span class="sxs-lookup"><span data-stu-id="69ab5-103">Redirecting Data with Out-* Cmdlets</span></span>
<span data-ttu-id="69ab5-104">Windows PowerShell ofrece varios cmdlets que permiten controlar la salida de datos directamente.</span><span class="sxs-lookup"><span data-stu-id="69ab5-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="69ab5-105">Estos cmdlets comparten dos características importantes.</span><span class="sxs-lookup"><span data-stu-id="69ab5-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="69ab5-106">En primer lugar, suelen transformar datos a algún formato de texto.</span><span class="sxs-lookup"><span data-stu-id="69ab5-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="69ab5-107">Lo hacen para aplicar la salida de datos a componentes del sistema que la entrada de texto.</span><span class="sxs-lookup"><span data-stu-id="69ab5-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="69ab5-108">Esto significa que deben representar los objetos como texto.</span><span class="sxs-lookup"><span data-stu-id="69ab5-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="69ab5-109">Por lo tanto, el texto tiene el formato que puede ver en la ventana de la consola de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69ab5-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="69ab5-110">En segundo lugar, estos cmdlets usan el verbo de Windows PowerShell **Out** porque envían información fuera de Windows PowerShell a alguna otra ubicación.</span><span class="sxs-lookup"><span data-stu-id="69ab5-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="69ab5-111">El cmdlet **Out-Host** no es una excepción: la presentación de la ventana host se encuentra fuera de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69ab5-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="69ab5-112">Esto es importante porque los datos se eliminan realmente cuando se envían fuera de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69ab5-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="69ab5-113">Puede verlo si intenta crear una canalización que pagine los datos en la ventana host y, luego, intenta formatearla como una lista, tal como se muestra aquí:</span><span class="sxs-lookup"><span data-stu-id="69ab5-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```
PS> Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="69ab5-114">Es de esperar que el comando muestre páginas de información de proceso en formato de lista.</span><span class="sxs-lookup"><span data-stu-id="69ab5-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="69ab5-115">En su lugar, muestra la lista tabular predeterminada:</span><span class="sxs-lookup"><span data-stu-id="69ab5-115">Instead, it displays the default tabular list:</span></span>

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="69ab5-116">El cmdlet **Out-Host** envía los datos directamente a la consola, de modo que el comando **Format-List** nunca reciba datos para formatear.</span><span class="sxs-lookup"><span data-stu-id="69ab5-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="69ab5-117">La manera correcta de estructurar este comando es colocar el cmdlet **Out-Host** al final de la canalización, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="69ab5-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="69ab5-118">Esto hace que los datos de proceso se formateen en una lista antes de paginarse y mostrarse.</span><span class="sxs-lookup"><span data-stu-id="69ab5-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="69ab5-119">Esto se aplica a todos los cmdlets **Out**.</span><span class="sxs-lookup"><span data-stu-id="69ab5-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="69ab5-120">Un cmdlet **Out** siempre debe aparecer al final de la canalización.</span><span class="sxs-lookup"><span data-stu-id="69ab5-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="69ab5-121">Todos los cmdlets **Out** representan la salida como texto, con el formato vigente para la ventana de consola, incluidos los límites de longitud de línea.</span><span class="sxs-lookup"><span data-stu-id="69ab5-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="69ab5-122">Paginar la salida de la consola (Out-Host)</span><span class="sxs-lookup"><span data-stu-id="69ab5-122">Paging Console Output (Out-Host)</span></span>
<span data-ttu-id="69ab5-123">De forma predeterminada, Windows PowerShell envía datos a la ventana host, que es exactamente lo que hace el cmdlet Out-Host.</span><span class="sxs-lookup"><span data-stu-id="69ab5-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="69ab5-124">El uso principal del cmdlet Out-Host es paginar datos como se explicó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="69ab5-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="69ab5-125">Por ejemplo, el siguiente comando usa Out-Host para paginar la salida del comando Get-Command:</span><span class="sxs-lookup"><span data-stu-id="69ab5-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```
PS> Get-Command | Out-Host -Paging
```

<span data-ttu-id="69ab5-126">También puede usar la función **more** para paginar datos.</span><span class="sxs-lookup"><span data-stu-id="69ab5-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="69ab5-127">En Windows PowerShell, **more** es una función que llama a **Out-Host -Paging**.</span><span class="sxs-lookup"><span data-stu-id="69ab5-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="69ab5-128">El comando siguiente muestra cómo usar la función **more** para paginar la salida de Get-Command:</span><span class="sxs-lookup"><span data-stu-id="69ab5-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```
PS> Get-Command | more
```

<span data-ttu-id="69ab5-129">Si incluye uno o más nombres de archivo como argumentos en la función more, la función leerá los archivos especificados y paginará su contenido en el host:</span><span class="sxs-lookup"><span data-stu-id="69ab5-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="69ab5-130">Descartar la salida (Out-Null)</span><span class="sxs-lookup"><span data-stu-id="69ab5-130">Discarding Output (Out-Null)</span></span>
<span data-ttu-id="69ab5-131">El cmdlet **Out-Null** está diseñado para descartar inmediatamente cualquier entrada que reciba.</span><span class="sxs-lookup"><span data-stu-id="69ab5-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="69ab5-132">Esto es útil para descartar los datos innecesarios que obtiene como efecto secundario de la ejecución de un comando.</span><span class="sxs-lookup"><span data-stu-id="69ab5-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="69ab5-133">Si escribe el comando siguiente, no obtiene nada del comando:</span><span class="sxs-lookup"><span data-stu-id="69ab5-133">When type the following command, you do not get anything back from the command:</span></span>

```
PS> Get-Command | Out-Null
```

<span data-ttu-id="69ab5-134">El cmdlet **Out-Null** no descarta la salida de error.</span><span class="sxs-lookup"><span data-stu-id="69ab5-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="69ab5-135">Por ejemplo, si escribe el comando siguiente, se muestra un mensaje que le informa de que Windows PowerShell no reconoce 'Is-NotACommand':</span><span class="sxs-lookup"><span data-stu-id="69ab5-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="69ab5-136">Imprimir datos (Out-Printer)</span><span class="sxs-lookup"><span data-stu-id="69ab5-136">Printing Data (Out-Printer)</span></span>
<span data-ttu-id="69ab5-137">Puede imprimir los datos mediante el cmdlet **Out-Printer**.</span><span class="sxs-lookup"><span data-stu-id="69ab5-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="69ab5-138">El cmdlet **Out-Printer** usará la impresora predeterminada si no proporciona un nombre de impresora.</span><span class="sxs-lookup"><span data-stu-id="69ab5-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="69ab5-139">Puede usar cualquier impresora basada en Windows especificando su nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="69ab5-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="69ab5-140">No se requiere ningún tipo de asignación de puerto de impresora ni una impresora física real.</span><span class="sxs-lookup"><span data-stu-id="69ab5-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="69ab5-141">Por ejemplo, si tiene las herramientas de creación de imágenes de documentos de Microsoft Office instaladas, puede enviar los datos a un archivo de imagen. Para ello, escriba:</span><span class="sxs-lookup"><span data-stu-id="69ab5-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```
PS> Get-Command Get-Command | Out-Printer -Name "Microsoft Office Document Image Writer"
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="69ab5-142">Guardar datos (Out-File)</span><span class="sxs-lookup"><span data-stu-id="69ab5-142">Saving Data (Out-File)</span></span>
<span data-ttu-id="69ab5-143">Puede enviar la salida a un archivo en lugar de a la ventana de la consola mediante el cmdlet **Out-File**.</span><span class="sxs-lookup"><span data-stu-id="69ab5-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="69ab5-144">La línea de comandos siguiente envía una lista de procesos al archivo **C:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="69ab5-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="69ab5-145">Los resultados del uso del cmdlet **Out-File** pueden no ser los esperados si está acostumbrado al redireccionamiento de salida tradicional.</span><span class="sxs-lookup"><span data-stu-id="69ab5-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="69ab5-146">Para entender su comportamiento, debe tener en cuenta el contexto en el que opera el cmdlet **Out-File**.</span><span class="sxs-lookup"><span data-stu-id="69ab5-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="69ab5-147">De forma predeterminada, el cmdlet **Out-File** crea un archivo Unicode.</span><span class="sxs-lookup"><span data-stu-id="69ab5-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="69ab5-148">Es el mejor valor predeterminado a largo plazo, pero significa que las herramientas que esperan archivos ASCII no funcionarán correctamente con el formato de salida predeterminado.</span><span class="sxs-lookup"><span data-stu-id="69ab5-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="69ab5-149">Puede cambiar el formato de salida predeterminado a ASCII mediante el parámetro **Encoding**:</span><span class="sxs-lookup"><span data-stu-id="69ab5-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="69ab5-150">**Out-File** formatea el contenido del archivo para que se parezca a la salida de la consola.</span><span class="sxs-lookup"><span data-stu-id="69ab5-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="69ab5-151">Esto hace que la salida se trunque igual que en una ventana de la consola en la mayoría de las circunstancias.</span><span class="sxs-lookup"><span data-stu-id="69ab5-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="69ab5-152">Por ejemplo, si ejecuta el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="69ab5-152">For example, if you run the following command:</span></span>

```
PS> Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="69ab5-153">El resultado tendrá este aspecto:</span><span class="sxs-lookup"><span data-stu-id="69ab5-153">The output will look like this:</span></span>

```
CommandType     Name                            Definition                     
-----------     ----                            ----------                     
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="69ab5-154">Para obtener una salida que no fuerce ajustes de línea para coincidir con el ancho de pantalla, puede usar el parámetro **Width** para especificar el ancho de línea.</span><span class="sxs-lookup"><span data-stu-id="69ab5-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="69ab5-155">Dado que **Width** es un parámetro entero de 32 bits, el valor máximo que puede tener es 2147483647.</span><span class="sxs-lookup"><span data-stu-id="69ab5-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="69ab5-156">Escriba lo siguiente para establecer el ancho de línea en este valor máximo:</span><span class="sxs-lookup"><span data-stu-id="69ab5-156">Type the following to set the line width to this maximum value:</span></span>

```
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="69ab5-157">El cmdlet **Out-File** resulta especialmente útil cuando desea guardar la salida como se habría mostrado en la consola.</span><span class="sxs-lookup"><span data-stu-id="69ab5-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="69ab5-158">Para un mayor control sobre el formato de salida, necesita herramientas más avanzadas.</span><span class="sxs-lookup"><span data-stu-id="69ab5-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="69ab5-159">Las veremos en el próximo capítulo, junto con algunos detalles sobre la manipulación de objetos.</span><span class="sxs-lookup"><span data-stu-id="69ab5-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>

