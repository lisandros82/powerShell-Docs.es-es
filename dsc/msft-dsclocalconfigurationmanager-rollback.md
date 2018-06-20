---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método RollBack de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219885"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método RollBack de la clase MSFT_DSCLocalConfigurationManager

Revierte la configuración a una versión anterior.

<a name="syntax"></a>Sintaxis
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a>Parámetros
----------

*configurationNumber* \[in\] Especifica la configuración solicitada.

## <a name="return-value"></a>Valor devuelto
------------

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos
------------
>**MOF:** DscCore.mof

>**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Vea también


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)