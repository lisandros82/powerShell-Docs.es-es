---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfigurationApplyAsync de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078284"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método SendConfigurationApplyAsync de la clase MSFT_DSCLocalConfigurationManager

Envía el documento de configuración de forma asincrónica al nodo administrado y usa el agente de configuración para aplicar la configuración.

## <a name="syntax"></a>Sintaxis

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>Parámetros

*ConfigurationData* \[in\] Datos del entorno para la configuración.

*force* \[in\] **true** para forzar la configuración a detenerse.

*jobId* \[in\] Identificador del trabajo al que se va a enviar la configuración.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vea también

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)