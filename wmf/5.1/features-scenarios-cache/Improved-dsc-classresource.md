---
title: Mejoras en los recursos de la clase DSC
author: jaimeo
contributor: amitsara
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: b24e70c1e1aaf71487b00fbccaf6edb0f375b888

---

## Mejoras en los recursos de la clase DSC

En esta versión, hemos corregido los siguientes problemas conocidos de WMF 5.0:
* Get-DscConfiguration puede devolver valores vacíos (null) o errores si la función Get() de un recurso de DSC basado en clases devuelve un tipo complejo o de tabla hash.
* Get-DscConfiguration devuelve un error si se utiliza la credencial RunAs en la configuración de DSC.
* Un recurso basado en clases no se puede utilizar en una configuración compuesta.
* Start-DscConfiguration se bloquea si el recurso basado en clases tiene una propiedad de un tipo propio.
* Los recursos basados en clases no se pueden utilizar como recursos exclusivos.



<!--HONumber=Aug16_HO3-->


