---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método RemoveConfiguration
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734390"
---
# <a name="removeconfiguration-method"></a>Método RemoveConfiguration

Quita los archivos de configuración.

## <a name="syntax"></a>Sintaxis

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>Parámetros

*Stage* \[in\] Especifica qué documento de configuración quiere quitar. Los valores siguientes son válidos:

|Value |Descripción |
|:--- |:---|
|**1** | Documento de configuración **Current** (current.mof). |
|**2** | Documento de configuración **Pending** (pending.mof).  |
|**4** | Documento de configuración **Previous** (previous.mof). |

*Force* \[in\] **true** para forzar la eliminación de la configuración.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vea también

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
