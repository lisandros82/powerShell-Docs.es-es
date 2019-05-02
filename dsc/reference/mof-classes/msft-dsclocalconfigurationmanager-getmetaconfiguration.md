---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetMetaConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078527"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método GetMetaConfiguration de la clase MSFT_DSCLocalConfigurationManager

Obtiene la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.

## <a name="syntax"></a>Sintaxis

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a>Parámetros

*MetaConfiguration* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_DSCMetaConfiguration** que define la configuración.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vea también

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)