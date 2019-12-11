---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Redirigir datos con cmdlets Out
ms.openlocfilehash: d4cc14e26bdef0f973f948177d0c1e68929605fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030077"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Redirigir datos con cmdlets Out-*

Windows PowerShell ofrece varios cmdlets que permiten controlar la salida de datos directamente. Estos cmdlets comparten dos características importantes.

En primer lugar, suelen transformar datos a algún formato de texto. Lo hacen para aplicar la salida de datos a componentes del sistema que la entrada de texto. Esto significa que deben representar los objetos como texto. Por lo tanto, el texto tiene el formato que puede ver en la ventana de la consola de Windows PowerShell.

En segundo lugar, estos cmdlets usan el verbo de Windows PowerShell **Out** porque envían información fuera de Windows PowerShell a alguna otra ubicación. El cmdlet **Out-Host** no es una excepción: la presentación de la ventana host se encuentra fuera de Windows PowerShell. Esto es importante porque los datos se eliminan realmente cuando se envían fuera de Windows PowerShell. Puede verlo si intenta crear una canalización que pagine los datos en la ventana host y, luego, intenta formatearla como una lista, tal como se muestra aquí:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

Es de esperar que el comando muestre páginas de información de proceso en formato de lista. En su lugar, muestra la lista tabular predeterminada:

```output
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

El cmdlet **Out-Host** envía los datos directamente a la consola, de modo que el comando **Format-List** nunca reciba datos para formatear.

La manera correcta de estructurar este comando es colocar el cmdlet **Out-Host** al final de la canalización, como se muestra a continuación. Esto hace que los datos de proceso se formateen en una lista antes de paginarse y mostrarse.

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

Esto se aplica a todos los cmdlets **Out**. Un cmdlet **Out** siempre debe aparecer al final de la canalización.

> [!NOTE]
> Todos los cmdlets **Out** representan la salida como texto, con el formato vigente para la ventana de consola, incluidos los límites de longitud de línea.

## <a name="paging-console-output-out-host"></a>Paginar la salida de la consola (Out-Host)

De forma predeterminada, Windows PowerShell envía datos a la ventana host, que es exactamente lo que hace el cmdlet Out-Host. El uso principal del cmdlet Out-Host es paginar datos como se explicó anteriormente. Por ejemplo, el siguiente comando usa Out-Host para paginar la salida del comando Get-Command:

```powershell
Get-Command | Out-Host -Paging
```

También puede usar la función **more** para paginar datos. En Windows PowerShell, **more** es una función que llama a **Out-Host -Paging**. El comando siguiente muestra cómo usar la función **more** para paginar la salida de Get-Command:

```powershell
Get-Command | more
```

Si incluye uno o más nombres de archivo como argumentos en la función more, la función leerá los archivos especificados y paginará su contenido en el host:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a>Descartar la salida (Out-Null)

El cmdlet **Out-Null** está diseñado para descartar inmediatamente cualquier entrada que reciba. Esto es útil para descartar los datos innecesarios que obtiene como efecto secundario de la ejecución de un comando. Si escribe el comando siguiente, no obtiene nada del comando:

```powershell
Get-Command | Out-Null
```

El cmdlet **Out-Null** no descarta la salida de error. Por ejemplo, si escribe el comando siguiente, se muestra un mensaje que le informa de que Windows PowerShell no reconoce 'Is-NotACommand':

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a>Imprimir datos (Out-Printer)

Puede imprimir los datos mediante el cmdlet **Out-Printer**. El cmdlet **Out-Printer** usará la impresora predeterminada si no proporciona un nombre de impresora. Puede usar cualquier impresora basada en Windows especificando su nombre para mostrar. No se requiere ningún tipo de asignación de puerto de impresora ni una impresora física real. Por ejemplo, si tiene las herramientas de creación de imágenes de documentos de Microsoft Office instaladas, puede enviar los datos a un archivo de imagen. Para ello, escriba:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a>Guardar datos (Out-File)

Puede enviar la salida a un archivo en lugar de a la ventana de la consola mediante el cmdlet **Out-File**. La línea de comandos siguiente envía una lista de procesos al archivo **C:\\temp\\processlist.txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

Los resultados del uso del cmdlet **Out-File** pueden no ser los esperados si está acostumbrado al redireccionamiento de salida tradicional. Para entender su comportamiento, debe tener en cuenta el contexto en el que opera el cmdlet **Out-File**.

De forma predeterminada, el cmdlet **Out-File** crea un archivo Unicode. Es el mejor valor predeterminado a largo plazo, pero significa que las herramientas que esperan archivos ASCII no funcionarán correctamente con el formato de salida predeterminado. Puede cambiar el formato de salida predeterminado a ASCII mediante el parámetro **Encoding**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-File** formatea el contenido del archivo para que se parezca a la salida de la consola. Esto hace que la salida se trunque igual que en una ventana de la consola en la mayoría de las circunstancias. Por ejemplo, si ejecuta el siguiente comando:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

El resultado tendrá este aspecto:

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Para obtener una salida que no fuerce ajustes de línea para coincidir con el ancho de pantalla, puede usar el parámetro **Width** para especificar el ancho de línea. Dado que **Width** es un parámetro entero de 32 bits, el valor máximo que puede tener es 2147483647. Escriba lo siguiente para establecer el ancho de línea en este valor máximo:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

El cmdlet **Out-File** resulta especialmente útil cuando desea guardar la salida como se habría mostrado en la consola. Para un mayor control sobre el formato de salida, necesita herramientas más avanzadas. Las veremos en el próximo capítulo, junto con algunos detalles sobre la manipulación de objetos.
