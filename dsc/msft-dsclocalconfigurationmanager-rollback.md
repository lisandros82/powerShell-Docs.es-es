---
title: "Método RollBack de la clase MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 771a9c7b50aba26f89dbf6b24eb3df67bafeac0a
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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

*configurationNumber* \[in\]  
Especifica la configuración solicitada. 

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


 

 



