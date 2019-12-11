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
# <a name="sorting-objects"></a><span data-ttu-id="25ceb-103">Ordenar objetos</span><span class="sxs-lookup"><span data-stu-id="25ceb-103">Sorting Objects</span></span>

<span data-ttu-id="25ceb-104">Mediante el cmdlet `Sort-Object` se pueden organizar los datos que se muestran para facilitar su examen.</span><span class="sxs-lookup"><span data-stu-id="25ceb-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="25ceb-105">`Sort-Object` toma el nombre de una o varias propiedades por los que se ordena y devuelve los datos ordenados por los valores de dichas propiedades.</span><span class="sxs-lookup"><span data-stu-id="25ceb-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="25ceb-106">Ordenación básica</span><span class="sxs-lookup"><span data-stu-id="25ceb-106">Basic sorting</span></span>

<span data-ttu-id="25ceb-107">Considere el problema de enumerar los subdirectorios y los archivos del directorio actual.</span><span class="sxs-lookup"><span data-stu-id="25ceb-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="25ceb-108">Si queremos ordenar por **LastWriteTime** y luego por **Name**, podemos escribir lo siguiente para hacerlo:</span><span class="sxs-lookup"><span data-stu-id="25ceb-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

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

<span data-ttu-id="25ceb-109">También puede ordenar los objetos en orden inverso especificando el parámetro de modificador **Descending**.</span><span class="sxs-lookup"><span data-stu-id="25ceb-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

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

## <a name="using-hash-tables"></a><span data-ttu-id="25ceb-110">Uso de las tablas hash</span><span class="sxs-lookup"><span data-stu-id="25ceb-110">Using hash tables</span></span>

<span data-ttu-id="25ceb-111">Puede ordenar propiedades diferentes en distintos órdenes mediante el uso de las tablas hash en una matriz.</span><span class="sxs-lookup"><span data-stu-id="25ceb-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="25ceb-112">Cada tabla hash utiliza una clave **Expression** para especificar el nombre de la propiedad como cadena y una clave **Ascending** o **Descending** para especificar el criterio de ordenación por `$true` o `$false`.</span><span class="sxs-lookup"><span data-stu-id="25ceb-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="25ceb-113">La clave **Expression** es obligatoria.</span><span class="sxs-lookup"><span data-stu-id="25ceb-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="25ceb-114">La clave **Ascending** o **Descending** es opcional.</span><span class="sxs-lookup"><span data-stu-id="25ceb-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="25ceb-115">El ejemplo siguiente ordena los objetos en orden descendente por **LastWriteTime** y en orden ascendente por **Name**.</span><span class="sxs-lookup"><span data-stu-id="25ceb-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

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

<span data-ttu-id="25ceb-116">También puede establecer un bloque de script en la clave **Expression**.</span><span class="sxs-lookup"><span data-stu-id="25ceb-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="25ceb-117">Cuando se ejecuta el cmdlet `Sort-Object`, se ejecuta el bloque de script y el resultado se utiliza para ordenar.</span><span class="sxs-lookup"><span data-stu-id="25ceb-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="25ceb-118">El ejemplo siguiente ordena los objetos en orden descendente según el intervalo de tiempo entre **CreationTime** y **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="25ceb-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

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

## <a name="tips"></a><span data-ttu-id="25ceb-119">Sugerencias</span><span class="sxs-lookup"><span data-stu-id="25ceb-119">Tips</span></span>

<span data-ttu-id="25ceb-120">Puede omitir el nombre de parámetro **Property** del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="25ceb-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="25ceb-121">Además, puede hacer referencia a `Sort-Object` mediante su alias integrado, `sort`:</span><span class="sxs-lookup"><span data-stu-id="25ceb-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="25ceb-122">Las claves de las tablas hash para la ordenación se pueden abreviar como sigue:</span><span class="sxs-lookup"><span data-stu-id="25ceb-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="25ceb-123">En este ejemplo, **e** significa **Expression**, **d** significa **Descending** y **a** significa **Ascending**.</span><span class="sxs-lookup"><span data-stu-id="25ceb-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="25ceb-124">Para mejorar la legibilidad, puede colocar las tablas hash en una variable independiente:</span><span class="sxs-lookup"><span data-stu-id="25ceb-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
