---
title: "Registros de servidor de extracción mejorados"
author: jaimeo
contributor: Indhu Sivaramakrishnan
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: d9f7dea63e6541b673ac6be5ccad59368b301440

---

## Registro de servidor de extracción mejorado ##

En las versiones anteriores de WMF, si se realizaban solicitudes de informes y registros concurrentes al servidor de extracción de DSC mientras se usaba la base de datos ESENT provocaban que LCM no pudiera registrarlas o informar al respecto. En tales casos, los registros de eventos del servidor de extracción mostrarán el error "El nombre de instancia ya está en uso".
Esto se debe a que se usa un patrón incorrecto para acceder a la base de datos ESENT en un escenario de varios subprocesos. En WMF 5.1, este problema se ha corregido. Los informes o registros simultáneos (que implican la base de datos ESENT) funcionan correctamente en WMF 5.1. Este problema solo concierne a la base de datos ESENT, no se aplica a la base de datos OLEDB. 



<!--HONumber=Aug16_HO3-->


