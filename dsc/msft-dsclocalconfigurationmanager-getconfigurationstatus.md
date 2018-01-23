---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager

Obtiene el historial de estado de la configuración.

<a name="syntax"></a>Sintaxis
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a>Parámetros
----------

*All* \[in\]  
**true** si este método debe devolver información sobre toda la configuración que se ejecuta en el equipo, incluidas la aplicación de configuración y la comprobación de coherencia.

*configurationStatus* \[out\]  
En la devolución, contiene una instancia incrustada de la clase **MSFT_DSCConfigurationStatus** que define la configuración.

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


 

 



