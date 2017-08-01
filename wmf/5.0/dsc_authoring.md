---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 555e01e88647b40717417360fb74bb6554a9c122
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="authoring-improvements-using-powershell-ise"></a>Mejoras de creación mediante PowerShell ISE

La creación de configuraciones de DSC en Windows PowerShell ISE es mucho más fácil gracias a las siguientes mejoras:

- Para enumerar todos los recursos de DSC en un bloque de **configuración** o un bloque de **nodo**, escriba **Ctrl+Space** en una línea en blanco dentro de él.
- Finalización automática de propiedades de recurso de tipo **enumeración**.
- Finalización automática de la propiedad **DependsOn** de los recursos de DSC, en función de otras instancias de recurso de la configuración.
- Mejor finalización con tabulación de los valores de propiedad de recurso.

**Nota:** Debe tener una cadena vacía para los valores de propiedad de recurso para poder usar Ctrl+Space para mostrar las opciones. Presione **Tabulador** para recorrer las opciones.

