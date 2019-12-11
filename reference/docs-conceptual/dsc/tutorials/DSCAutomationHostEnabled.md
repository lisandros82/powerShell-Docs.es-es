---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Clave del Registro DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954272"
---
>Se aplica a: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Clave del Registro DSCAutomationHostEnabled

DSC usa la clave del Registro **DSCAutomationHostEnabled** en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** para habilitar la configuración de la máquina en el arranque inicial.
**DSCAutomationHostEnabled** admite tres modos:

|  Valor de DSCAutomationHostEnabled  |  Descripción   |
|---|---|
0 | Deshabilita la configuración de la máquina en el arranque. |
1 | Habilita la configuración de la máquina en el arranque. |
2 | Habilita la configuración de la máquina solo si DSC está en estado pendiente o actual. Este es el valor predeterminado. |

## <a name="see-also"></a>Véase también

Para obtener un ejemplo de cómo usar esta función para ejecutar configuraciones en el arranque inicial, consulte [Configuración de máquinas virtuales en el arranque inicial mediante DSC](bootstrapDsc.md).
