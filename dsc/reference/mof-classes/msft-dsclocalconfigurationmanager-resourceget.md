---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método ResourceGet de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682215"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ResourceGet de la clase MSFT_DSCLocalConfigurationManager

Llama directamente al método **Get** de un recurso de DSC.

## <a name="syntax"></a>Sintaxis

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a>Parámetros

*ResourceType* \[in\] Nombre del recurso al que se va a llamar.

*ModuleName* \[in\] Nombre del módulo que contiene el recurso al que se va a llamar.

*resourceProperty* \[in\] Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente. Use el cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) para descubrir las propiedades del recurso y sus tipos.

*configurations* \[out\] En la devolución, contiene una instancia insertada de las configuraciones.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vea también

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)