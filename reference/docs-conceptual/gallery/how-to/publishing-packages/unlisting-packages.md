---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Ocultar paquetes
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328276"
---
# <a name="unlisting-packages"></a>Ocultar paquetes

**¿Por qué no se ofrece como opción la acción de quitar un paquete de la Galería de PowerShell?**

La Galería de PowerShell no permite que los usuarios eliminen sus paquetes permanentemente.
Esto permite que otros usuarios establezcan dependencias con los paquetes sin preocuparse de posibles interrupciones en el futuro.
Por ejemplo, si el módulo de Pester depende del módulo de Azure y este se quita de la Galería, el usuario ya no puede usar el módulo de Pester.

En lugar de quitar un paquete, puede ocultarlo.

**¿Qué pasa cuando se oculta un paquete en la Galería de PowerShell?**

Cuando se oculta un paquete como un módulo o un script en la Galería de PowerShell, se quita de la pestaña Paquetes. Además, los paquetes que se han ocultado no se podrán detectar mediante la barra de búsqueda.
La única manera de descargar un paquete que se ha ocultado consiste en especificar el nombre exacto y la versión de dicho paquete.
Por este motivo, la acción de ocultar un paquete no interrumpe otros módulos o scripts que dependen de él.

Para ocultar el paquete, visite la página de detalles del paquete y seleccione Eliminar paquete. Desactive la casilla Listed (Enumerado) y haga clic en Guardar.

**¿Cómo se puede quitar un paquete?**

Si se encuentra en un escenario en el que es necesario eliminar un paquete, póngase en contacto con los administradores de la Galería de PowerShell.
Los escenarios de eliminación válidos son los siguientes:
- Problemas de infracción de los derechos de autor.
- El paquete tiene un contenido potencialmente dañino.
- El paquete contiene información confidencial.

Para enviar una solicitud de eliminación de paquete a los administradores de la Galería de PowerShell, visite la página de detalles del paquete y seleccione Ponerse en contacto con soporte técnico.
