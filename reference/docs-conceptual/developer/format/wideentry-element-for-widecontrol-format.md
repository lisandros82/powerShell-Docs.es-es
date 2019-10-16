---
title: Elemento WideEntry para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367904"
---
# <a name="wideentry-element-for-widecontrol-format"></a>Elemento WideEntry para WideControl (formato)

Proporciona una definición de la vista amplia.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format)

## <a name="syntax"></a>Sintaxis

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `WideEntry`. Debe especificar un único elemento secundario `WideItem`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Elemento opcional.<br /><br /> Define los tipos .NET que usan esta definición de entrada ancha o la condición que debe existir para que se use esta definición.|
|[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Elemento obligatorio.<br /><br /> Define la propiedad o el script cuyo valor se muestra.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)|Proporciona las definiciones de la vista amplia.|

## <a name="remarks"></a>Observaciones

Una vista amplia es un formato de lista que muestra un valor de propiedad único o un valor de script para cada objeto. A diferencia de otros tipos de vistas, solo se puede especificar un elemento para cada definición de vista. Para obtener más información sobre los demás componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un elemento `WideEntry` que define un solo elemento `WideItem`. El elemento `WideItem` define la propiedad cuyo valor se muestra en la vista.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Para obtener un ejemplo completo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[Crear una vista amplia](./creating-a-wide-view.md)

[Elemento SelectionCondition para WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName para WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento TypeName para WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Elemento WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)

[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
