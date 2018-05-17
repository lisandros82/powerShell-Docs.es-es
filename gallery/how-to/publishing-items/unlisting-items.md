---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Ocultar elementos
ms.openlocfilehash: 35dcd283ddace5aec62d692b0ede12ae0bada765
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="unlisting-items"></a>Ocultar elementos

**¿Por qué no se ofrece como opción la acción de quitar un elemento de la Galería de PowerShell?**

La Galería de PowerShell no permite que los usuarios eliminen sus elementos permanentemente.
Esto permite que otros usuarios establezcan dependencias con los elementos sin preocuparse de posibles interrupciones en el futuro.
Por ejemplo, si el módulo de Pester depende del módulo de Azure y este se quita de la Galería, el usuario ya no puede usar el módulo de Pester.

En lugar de quitar un elemento, puede ocultarlo.

**¿Qué pasa cuando se oculta un elemento en la Galería de PowerShell?**

Cuando se oculta un elemento como un módulo o un script en la Galería de PowerShell, se quita de la pestaña Elementos. Además, los elementos que se han ocultado no se podrán detectar mediante la barra de búsqueda.
La única manera de descargar un elemento que se ha ocultado consiste en especificar el nombre exacto y la versión de dicho elemento.
Por este motivo, la acción de ocultar un elemento no interrumpe otros módulos o scripts que dependen de él.

Para ocultar el elemento, visite la página de detalles del elemento y seleccione Eliminar elemento. Desactive la casilla Listed (Enumerado) y haga clic en Guardar.

**¿Cómo se puede quitar un elemento?**

Si se encuentra en un escenario en el que es necesario eliminar un elemento, póngase en contacto con los administradores de la Galería de PowerShell.
Los escenarios de eliminación válidos son los siguientes:
- Problemas de infracción de los derechos de autor.
- El elemento tiene un contenido potencialmente dañino.
- El elemento contiene información confidencial.

Para enviar una solicitud de eliminación de elemento a los administradores de la Galería de PowerShell, visite la página de detalles del elemento y seleccione Ponerse en contacto con soporte técnico.