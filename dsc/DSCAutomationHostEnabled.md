---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Clave del Registro DSCAutomationHostEnabled
ms.openlocfilehash: e47c929b366f93738343eabc431aab5a4428352d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
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


