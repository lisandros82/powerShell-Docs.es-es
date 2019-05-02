---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078782"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager

Obtiene el historial de estado de la configuración.

## <a name="syntax"></a>Sintaxis

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a>Parámetros

*All* \[in\] **true** si este método debe devolver información sobre toda la configuración que se ejecuta en la máquina, incluidas la aplicación de configuración y la comprobación de coherencia.

*configurationStatus* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_DSCConfigurationStatus** que define la configuración.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vea también

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)