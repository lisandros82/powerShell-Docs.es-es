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
# <a name="removing-objects-from-the-pipeline-where-object"></a>Quitar objetos de la canalización (Where-Object)

En PowerShell, se suelen generar y pasar más objetos de los deseados a una canalización. Puede especificar las propiedades de los objetos concretos que quiere que se muestren mediante los cmdlets `Format-*`, pero esto no ayuda a resolver el problema de eliminación de objetos completos de la presentación. Es posible que quiera filtrar objetos antes del final de una canalización, para poder realizar acciones solo en un subconjunto de los objetos generados inicialmente.

PowerShell incluye el cmdlet `Where-Object`, que permite probar cada objeto de la canalización y pasarlo solo a la canalización si cumple una condición de prueba determinada. Los objetos que no pasan la prueba se quitan de la canalización. Debe indicar la condición de prueba como el valor del parámetro **FilterScript**.

## <a name="performing-simple-tests-with-where-object"></a>Realizar pruebas simples con Where-Object

El valor de **FilterScript** es un *bloque de script*; es decir, uno o más comandos de PowerShell entre llaves (`{}`), que se evalúa como true o false. Estos bloques de script pueden ser muy simples, pero su creación requiere el conocimiento de otro concepto de PowerShell: los operadores de comparación. Un operador de comparación compara los elementos que aparecen en cada uno de sus lados. Los operadores de comparación comienzan con un carácter (`-`) seguido de un nombre. Los operadores de comparación básicos funcionan en casi todos los tipos de objeto. Es posible que los operadores de comparación más avanzados solo funcionen en texto o matrices.

> [!NOTE]
> De manera predeterminada, al trabajar con texto, los operadores de comparación de PowerShell no distinguen mayúsculas de minúsculas.

Debido a consideraciones de análisis, los símbolos como `<`, `>` y `=` no se usan como operadores de comparación. En su lugar, los operadores de comparación están formados por letras. Los operadores lógicos básicos se muestran en la tabla siguiente.

| Operador de comparación |                  Significado                   |    Ejemplo (devuelve true)    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| -eq                 | es igual a                                | 1 -eq 1                      |
| -ne                 | No es igual a                            | 1 -ne 2                      |
| -lt                 | Es menor que                               | 1 -lt 2                      |
| -le                 | Es menor o igual que                   | 1 -le 2                      |
| -gt                 | Es mayor que                            | 2 -gt 1                      |
| -ge                 | Es mayor o igual que                | 2 -ge 1                      |
| -like               | Es como (comparación de comodín para texto)     | "file.doc" -like "f*.do?"    |
| -notlike            | No es como (comparación de comodín para texto) | "file.doc" -notlike "p*.doc" |
| -contains           | Contains                                   | 1,2,3 -contains 1            |
| -notcontains        | No contiene                           | 1,2,3 -notcontains 4         |

Los bloques de script `Where-Object` usan la variable especial `$_` para hacer referencia al objeto actual en la canalización. A continuación se incluye un ejemplo de cómo funciona: Si tiene una lista de números y solo quiere que se devuelvan los que sean inferiores a 3, puede usar `Where-Object` para filtrar los números; para ello, escriba:

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>Filtrar por las propiedades de objeto

Dado que `$_` hace referencia al objeto de canalización actual, podemos acceder a sus propiedades para nuestras pruebas.

Por ejemplo, podemos observar la clase **Win32_SystemDriver** en WMI. Puede haber cientos de controladores del sistema en un determinado sistema, pero puede que solo esté interesado en un conjunto concreto de estos controladores, como, por ejemplo, aquellos que se están ejecutando actualmente. En la clase **Win32_SystemDriver**, la propiedad pertinente es **State**. Para filtrar los controladores del sistema seleccione solo los que se estén ejecutando. Para ello, escriba:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

Esto sigue produciendo una larga lista. Es posible que también quiera filtrar para seleccionar solo los controladores configurados para iniciarse automáticamente al probar el valor **StartMode**:

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

Esto nos da mucha información que ya no necesitamos porque sabemos que los controladores se están ejecutando.
De hecho, los únicos datos que probablemente necesitamos en este momento son el nombre y el nombre para mostrar. El siguiente comando solo incluye esas dos propiedades, lo que produce una salida mucho más simple:

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

Hay dos elementos `Where-Object` en el comando anterior, pero puede expresarse en un único elemento `Where-Object` mediante el operador lógico `-and`, de manera similar a la siguiente:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

Los operadores lógicos estándar se muestran en la tabla siguiente.

| Operador lógico |                 Significado                  |  Ejemplo (devuelve true)  |
| ---------------- | ---------------------------------------- | ------------------------ |
| -and             | Lógico and; true si ambos lados son true | (1 -eq 1) -and (2 -eq 2) |
| -or              | Lógico or; true si algún lado es true  | (1 -eq 1) -or (1 -eq 2)  |
| -not             | Lógico not; invierte true y false     | -not (1 -eq 2)           |
| \!               | Lógico not; invierte true y false     | \!(1 -eq 2)              |
