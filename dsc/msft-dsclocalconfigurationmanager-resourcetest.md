---
title: "Método ResourceTest de la clase MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 4129c83dd0b72159cbf1d47c037b9d462ca45f0e
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ResourceTest de la clase MSFT_DSCLocalConfigurationManager

Llama directamente al método **Test** de un recurso de DSC.

<a name="syntax"></a>Sintaxis
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a>Parámetros
----------

*ResourceType* \[in\]  
Nombre del recurso al que se llamará.

*ModuleName* \[in\]  
Nombre del módulo que contiene el recurso al que se llamará.

*resourceProperty* \[in\]  
Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente. Use el cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) para descubrir las propiedades del recurso y sus tipos.

*InDesiredState* \[out\]  
En la devolución, esta propiedad se establece en **true** si el nodo de destino está en el estado deseado.

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


 

 



