---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 1595a3e817fd711c35128f06927fd57df7a63fb8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="authoring-improvements-using-powershell-ise"></a>Mejoras de creación mediante PowerShell ISE

La creación de configuraciones de DSC en Windows PowerShell ISE es mucho más fácil gracias a las siguientes mejoras:

- Para enumerar todos los recursos de DSC en un bloque de **configuración** o un bloque de **nodo**, escriba **Ctrl+Space** en una línea en blanco dentro de él.
- Finalización automática de propiedades de recurso de tipo **enumeración**.
- Finalización automática de la propiedad **DependsOn** de los recursos de DSC, en función de otras instancias de recurso de la configuración.
- Mejor finalización con tabulación de los valores de propiedad de recurso.

**Nota:** Debe tener una cadena vacía para los valores de propiedad de recurso para poder usar Ctrl+Space para mostrar las opciones. Presione **Tabulador** para recorrer las opciones.
