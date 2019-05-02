---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078775"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager

Habilita la depuración de recursos de DSC.

## <a name="syntax"></a>Sintaxis

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a>Parámetros

*BreakAll* \[in\] Establece un punto de interrupción en cada línea del script de recursos.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vea también

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)