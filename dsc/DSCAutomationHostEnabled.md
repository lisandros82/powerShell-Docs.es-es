---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Clave del Registro DSCAutomationHostEnabled
ms.openlocfilehash: c58b7a8f2485ff02f09763749a3de8a75f882d19
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
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


