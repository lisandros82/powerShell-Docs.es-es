---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078663"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager

Envía el documento de configuración al nodo administrado y usa el método **Get** del agente de configuración para aplicar la configuración.

## <a name="syntax"></a>Sintaxis

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a>Parámetros

*configurationData* \[in\] Especifica los datos de configuración que se van a enviar.

*configurations* \[out\] En la devolución, contiene una instancia insertada de las configuraciones.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vea también

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)