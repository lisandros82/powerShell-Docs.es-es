---
title: "Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 8f13964dfbbe1cd827c58232a35d1cbacddeed1b
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager

Obtiene la salida del agente de configuración asociada con un trabajo específico.

<a name="syntax"></a>Sintaxis
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a>Parámetros
----------

*jobId* \[in\]  
Identificador del trabajo del que quiere obtener datos de salida.

*resumeOutputBookmark* \[in\]  
Especifica que la salida debe tener una continuación de un marcador anterior.

*output* \[out\]  
Salida del trabajo especificado.

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

 

 



