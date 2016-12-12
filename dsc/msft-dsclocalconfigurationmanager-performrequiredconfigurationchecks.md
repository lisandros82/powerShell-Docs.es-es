---
title: "Método PerformRequiredConfigurationChecks de la clase MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: f9eb975845f6ccabcac80e2591fd987f80f81331
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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

*Flags* \[in\]  
Máscara de bits que especifica el tipo de comprobación de coherencia que se ejecutará. Los valores siguientes son válidos y se pueden combinar mediante el uso de una operación **O** bit a bit:

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


 

 



