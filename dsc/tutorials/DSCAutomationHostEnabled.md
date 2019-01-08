---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Clave del Registro DSCAutomationHostEnabled
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402234"
---
>Se aplica a: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Clave del Registro DSCAutomationHostEnabled

DSC usa la clave del Registro **DSCAutomationHostEnabled** en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** para habilitar la configuración de la máquina en el arranque inicial.
DSCAutomationHostEnabled admite tres modos:

|  Valor de DSCAutomationHostEnabled  |  Descripción   |
|---|---|
0 | Deshabilita la configuración de la máquina en el arranque. |
1 | Habilita la configuración de la máquina en el arranque. |
2 | Habilita la configuración de la máquina solo si DSC está en estado pendiente o actual. Este es el valor predeterminado. |

## <a name="see-also"></a>Véase también

Para obtener un ejemplo de cómo usar esta función para ejecutar configuraciones en el arranque inicial, consulte [Configuración de máquinas virtuales en el arranque inicial mediante DSC](bootstrapDsc.md).