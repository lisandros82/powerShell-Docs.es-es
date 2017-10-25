---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3261e5a07b8181190a04de3f210da50f23bb2953
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Compatibilidad del control de versiones de módulos en paralelo para recursos de DSC

Los módulos que contienen recursos de DSC pueden instalarse en paralelo y las configuraciones de DSC pueden usar una versión específica del recurso que está instalado en el sistema.

Para más información, consulte [Uso de recursos con varias versiones](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problemas conocidos

En esta versión, se conocen los siguientes problemas de instalación en paralelo:

-   No se admite el uso de dos versiones diferentes del recurso de DSC en la misma configuración.

