---
title: Elemento WideItem para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361404"
---
# <a name="wideitem-element-for-widecontrol-format"></a>Elemento WideItem para WideControl (formato)

Define la propiedad o el script cuyo valor se muestra.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) WideEntry (Format) elemento WideItem (Format)

## <a name="syntax"></a>Sintaxis

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `WideItem`. El elemento `FormatString` es opcional. Sin embargo, debe especificar un elemento `PropertyName` o `ScriptBlock`, pero no puede especificar ambos.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento FormatString para WideItem para WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica un modelo de formato que define cómo se muestra la propiedad o el valor de script en la vista.|
|[Elemento PropertyName para WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Especifica la propiedad del objeto cuyo valor se muestra en la vista amplia.|
|[Elemento ScriptBlock para WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Especifica el script cuyo valor se muestra en la vista amplia.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Proporciona una definición de la vista amplia.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los componentes de una vista amplia, vea [vista amplia](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un elemento `WideEntry` que define un solo elemento `WideItem`. El elemento `WideItem` define la propiedad o el script cuyo valor se muestra en la vista.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Para obtener un ejemplo completo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[Elemento FormatString para WideItem para WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[Elemento PropertyName para WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Elemento ScriptBlock para WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
