---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método PerformRequiredConfigurationChecks
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955012"
---
# <a name="performrequiredconfigurationchecks-method"></a>Método PerformRequiredConfigurationChecks

Inicia una comprobación de coherencia mediante el Programador de tareas.

## <a name="syntax"></a>Sintaxis

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Parámetros

*Flags* \[in\] Máscara de bits que especifica el tipo de comprobación de coherencia que se va a ejecutar. Los valores siguientes son válidos y se pueden combinar mediante el uso de una operación **O** bit a bit:

|Value |Descripción |
|:--- |:---|
|**1** | Comprobación de coherencia normal. |
|**2** | Continuación de una comprobación de coherencia después de reiniciar el equipo. Este valor no debe combinarse con otros valores. |
|**4** | Debe extraerse la configuración del servidor de extracción especificado en la metaconfiguración del nodo. Este valor siempre debe combinarse con **1**, para un valor de **5**. |
|**8** | Envía el estado al servidor de informes. |

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vea también

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
