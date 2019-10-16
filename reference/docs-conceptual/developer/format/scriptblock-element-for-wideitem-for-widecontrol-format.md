---
title: Elemento ScriptBlock para WideItem para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362034"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>Elemento ScriptBlock para WideItem for WideControl (formato)

Especifica el script cuyo valor se muestra en la vista amplia.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) WideEntry (Format) elemento WideItem (Format) elemento ScriptBlock para WideItem (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Define la propiedad o el bloque de script cuyo valor se muestra en la vista amplia.|

## <a name="text-value"></a>Valor de texto

Especifique el script cuyo valor se muestra.

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra un elemento `WideItem` que define un script cuyo valor se muestra en la vista.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Véase también

[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Crear una vista amplia](./creating-a-wide-view.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
