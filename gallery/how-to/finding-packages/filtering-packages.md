---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Filtración de los resultados de la búsqueda
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003938"
---
# <a name="filtering-search-results"></a>Filtración de los resultados de la búsqueda

La pestaña [Paquetes](https://www.powershellgallery.com/packages) muestra todos los paquetes disponibles en la Galería de PowerShell.

Hay varias maneras de filtrar, ordenar y buscar los paquetes.
Para más información sobre un paquete determinado, haga clic en el paquete.

## <a name="filter-by"></a>Filtrar por

La lista desplegable bajo "Filtrar por" permite a los usuarios filtrar los resultados por:
- Incluir versión preliminar
- Solo estable

Para obtener información acerca de "Versión preliminar" y "Estable", consulte [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Versiones preliminares agregadas a PowerShellGet y la Galería de PowerShell) en el blog del equipo de PowerShell.

Las casillas bajo la lista desplegable permiten a los usuarios filtrar los resultados por:
- Tipos de paquetes
  - Módulo
  - Script
- Categorías
  - Cmdlet
  - Recurso de DSC
  - Función
  - Capacidad de rol
  - Flujo de trabajo

Para ver solo módulos en la Galería de PowerShell, active Módulo en Tipos de paquetes.
De igual manera, para ver solo scripts en la Galería de PowerShell, active Script en Tipos de paquetes.

> [!NOTE]
> Los filtros son inclusivos.
> Por ejemplo, un paquete que contenga cmdlets y funciones aparecerá si se activa Cmdlet o Función, o ambos.
> Si no se selecciona ninguna opción, el paquete no aparecerá.
> Del mismo modo, si se seleccionan todas las categorías, solo aparecerán los paquetes que contengan alguna de esas categorías.
> **No aparecerán los paquetes que no pertenezcan a ninguna de esas categorías.**

## <a name="sort-by"></a>Ordenar por

La lista desplegable Ordenar por permite a los usuarios ordenar los resultados según los criterios siguientes:
- Popularidad: la popularidad está determinada por el número de descargas
- A-Z: alfabéticamente según el nombre de paquete
- Reciente: los paquetes aparecen ordenados por fecha de publicación

## <a name="search-box"></a>Cuadro de búsqueda

El cuadro de búsqueda permite a los usuarios buscar paquetes por palabras clave.
Para obtener más información, consulte [Sintaxis de búsqueda de la Galería](search-syntax.md).
