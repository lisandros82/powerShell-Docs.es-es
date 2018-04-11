---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Método PerformRequiredConfigurationChecks de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9cc4384088fcc39b09979b8ae4d023fc46307b13
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método PerformRequiredConfigurationChecks de la clase MSFT_DSCLocalConfigurationManager

Inicia una comprobación de coherencia mediante el Programador de tareas.

<a name="syntax"></a>Sintaxis
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a>Parámetros
----------

*Flags* \[in\] Máscara de bits que especifica el tipo de comprobación de coherencia que se va a ejecutar. Los valores siguientes son válidos y se pueden combinar mediante el uso de una operación **O** bit a bit:

|Value |Descripción |
|:--- |:---|
|**1** | Comprobación de coherencia normal. |
|**2** | Continuación de una comprobación de coherencia después de reiniciar el equipo. Este valor no debe combinarse con otros valores. |
|**4** | Debe extraerse la configuración del servidor de extracción especificado en la metaconfiguración del nodo. Este valor siempre debe combinarse con **1**, para un valor de **5**. |
|**8** | Envía el estado al servidor de informes. |

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