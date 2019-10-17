---
ms.date: 09/25/2019
keywords: powershell, cmdlet
title: Cómo usar la documentación de PowerShell
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281656"
---
# <a name="how-to-use-the-powershell-documentation"></a>Cómo usar la documentación de PowerShell

Le damos la bienvenida a la documentación en línea de PowerShell. Este sitio contiene referencia de cmdlets para las siguientes versiones de PowerShell:

- PowerShell 7 (versión preliminar)
- PowerShell 6
- PowerShell 5.1
- PowerShell 5.0
- PowerShell 4.0
- PowerShell 3.0

## <a name="selecting-your-version"></a>Selección de la versión

De forma predeterminada, este sitio muestra la documentación de la última versión publicada de PowerShell. Algunos cmdlets funcionan de forma diferente en las distintas versiones de PowerShell. Asegúrese de que está viendo la documentación de la versión de PowerShell que está usando.

Use el selector de versión en la parte superior de la página para seleccionar la versión de PowerShell que quiera.

![Selector de versión](images/how-to-use-docs/picker-vall.gif)

Revise el valor `$PSversionTable.PSVersion` para comprobar la versión de PowerShell que usa. En el ejemplo siguiente se muestra la salida de Windows PowerShell v5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a>Búsqueda de artículos

Hay dos maneras de buscar contenido en Docs. La manera más sencilla es usar el cuadro de filtro en el selector de versión. Basta con escribir una palabra que aparezca en el título de un artículo. En la página se muestra una lista de artículos coincidentes. También puede seleccionar la opción para buscar en todo el sitio de esa lista.

![cuadro de filtro](images/how-to-use-docs/filter-search.gif)
