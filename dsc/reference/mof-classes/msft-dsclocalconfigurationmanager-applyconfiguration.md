---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079173"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager

Usa el agente de configuración para aplicar la configuración que está pendiente.

Si no hay ninguna configuración pendiente, este método vuelve a aplicar la configuración actual.

## <a name="syntax"></a>Sintaxis

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parámetros

*force* \[in\] Si este parámetro es **true**, se vuelve a aplicar la configuración actual, aunque haya una configuración pendiente.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vea también

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)