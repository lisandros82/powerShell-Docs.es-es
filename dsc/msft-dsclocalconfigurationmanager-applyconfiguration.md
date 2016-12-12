---
title: "Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 6f9c6a8851732574ac72bc4f3a3db1a73fbbecf2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager

Usa el agente de configuración para aplicar la configuración que está pendiente. 

Si no hay ninguna configuración pendiente, este método vuelve a aplicar la configuración actual.


## <a name="syntax"></a>Sintaxis
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parámetros
----------

*force* \[in\]  
Si es **true**, se vuelve a aplicar la configuración actual, incluso si hay una configuración pendiente.

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

 

 



