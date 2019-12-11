---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Ordenar objetos
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030772"
---
# <a name="sorting-objects"></a>Ordenar objetos

Mediante el cmdlet `Sort-Object` se pueden organizar los datos que se muestran para facilitar su examen. `Sort-Object` toma el nombre de una o varias propiedades por los que se ordena y devuelve los datos ordenados por los valores de dichas propiedades.

## <a name="basic-sorting"></a>Ordenación básica

Considere el problema de enumerar los subdirectorios y los archivos del directorio actual.
Si queremos ordenar por **LastWriteTime** y luego por **Name**, podemos escribir lo siguiente para hacerlo:

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

También puede ordenar los objetos en orden inverso especificando el parámetro de modificador **Descending**.

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a>Uso de las tablas hash

Puede ordenar propiedades diferentes en distintos órdenes mediante el uso de las tablas hash en una matriz.
Cada tabla hash utiliza una clave **Expression** para especificar el nombre de la propiedad como cadena y una clave **Ascending** o **Descending** para especificar el criterio de ordenación por `$true` o `$false`.
La clave **Expression** es obligatoria.
La clave **Ascending** o **Descending** es opcional.

El ejemplo siguiente ordena los objetos en orden descendente por **LastWriteTime** y en orden ascendente por **Name**.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

También puede establecer un bloque de script en la clave **Expression**.
Cuando se ejecuta el cmdlet `Sort-Object`, se ejecuta el bloque de script y el resultado se utiliza para ordenar.

El ejemplo siguiente ordena los objetos en orden descendente según el intervalo de tiempo entre **CreationTime** y **LastWriteTime**.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a>Sugerencias

Puede omitir el nombre de parámetro **Property** del modo siguiente:

```powershell
Sort-Object LastWriteTime, Name
```

Además, puede hacer referencia a `Sort-Object` mediante su alias integrado, `sort`:

```powershell
sort LastWriteTime, Name
```

Las claves de las tablas hash para la ordenación se pueden abreviar como sigue:

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

En este ejemplo, **e** significa **Expression**, **d** significa **Descending** y **a** significa **Ascending**.

Para mejorar la legibilidad, puede colocar las tablas hash en una variable independiente:

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
