---
title: Elemento WideItem para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862631"
---
# <a name="wideitem-element-for-widecontrol-format"></a>Elemento WideItem para WideControl (formato)

Define la propiedad o el script cuyo valor se muestra.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) WideItem elemento de configuración (formato)

## <a name="syntax"></a>Sintaxis

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `WideItem` elemento. El elemento `FormatString` es opcional. Sin embargo, debe especificar un `PropertyName` o `ScriptBlock` elemento, pero no se puede especificar ambos.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento FormatString para WideItem para WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script en la vista.|
|[Elemento PropertyName para WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Especifica la propiedad del objeto cuyo valor se muestra en la vista ampliada.|
|[Elemento de bloque de script para WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Especifica la secuencia de comandos cuyo valor se muestra en la vista ampliada.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Proporciona una definición de la vista ampliada.|

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de los componentes de una vista amplia, consulte [vista amplia](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `WideEntry` elemento que define una sola `WideItem` elemento. El `WideItem` elemento define la propiedad o el script cuyo valor se muestra en la vista.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Para obtener un ejemplo completo de una vista amplia, consulte [vista amplia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[Elemento FormatString para WideItem para WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[Elemento PropertyName para WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Elemento de bloque de script para WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
