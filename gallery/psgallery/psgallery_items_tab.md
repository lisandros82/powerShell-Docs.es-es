---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_items_tab
ms.openlocfilehash: 5058253678a4f996b080e43820fee06b35b681f4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="items-tab"></a>Pestaña Elementos

La pestaña [Elementos](https://www.powershellgallery.com/items) muestra todos los elementos disponibles en la Galería de PowerShell.

Hay varias maneras de filtrar, ordenar y buscar los elementos.
Para obtener más información sobre un elemento determinado, haga clic en el elemento.

## <a name="filter-by"></a>Filtrar por

La lista desplegable bajo "Filtrar por" permite a los usuarios filtrar los resultados por:
* Incluir versión preliminar
* Solo estable

Para obtener información acerca de "Versión preliminar" y "Estable", consulte [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Versiones preliminares agregadas a PowerShellGet y la Galería de PowerShell) en el blog del equipo de PowerShell.

Las casillas bajo la lista desplegable permiten a los usuarios filtrar los resultados por:
* Tipos de elemento
  - Módulo
  - Script
* Categorías
  - Cmdlet
  - Recurso de DSC
  - Función
  - Capacidad de rol
  - Flujo de trabajo

Para ver solo módulos en la Galería de PowerShell, active Módulo en Tipos de elementos.
De igual manera, para ver solo scripts en la Galería de PowerShell, active Script en Tipos de elementos.

> [!NOTE]
> Los filtros son inclusivos.
> Por ejemplo, un elemento que contenga cmdlets y funciones aparecerá si se activa Cmdlet o Función (o ambos).
> Si no se selecciona ninguna opción, el elemento no aparecerá.
> Del mismo modo, si se seleccionan todas las categorías, solo aparecerán los elementos que contengan alguna de esas categorías.
> **No aparecerán los elementos que no pertenezcan a ninguna de esas categorías.**

## <a name="sort-by"></a>Ordenar por

La lista desplegable Ordenar por permite a los usuarios ordenar los resultados según los criterios siguientes:
* Popularidad: la popularidad está determinada por el número de descargas
* A-Z: alfabéticamente según el nombre de elemento
* Reciente: los elementos aparecen ordenados por fecha de publicación

## <a name="search-box"></a>Cuadro de búsqueda

El cuadro de búsqueda permite a los usuarios buscar elementos por palabras clave.
Para obtener más información, consulte [Sintaxis de búsqueda de la Galería](psgallery_search_syntax.md).