---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método RemoveConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método RemoveConfiguration de la clase MSFT_DSCLocalConfigurationManager

Quita los archivos de configuración.

<a name="syntax"></a>Sintaxis
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a>Parámetros
----------

*Stage* \[in\]  
Especifica qué documento de configuración quiere quitar. Los valores siguientes son válidos:

|Value |Descripción |
|:--- |:---|
|**1** | Documento de configuración **Current** (current.mof). |
|**2** | Documento de configuración **Pending** (pending.mof).  |
|**4** | Documento de configuración **Previous** (previous.mof). |

*Force* \[in\]  
**true** para forzar la eliminación de la configuración.

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


 

 



