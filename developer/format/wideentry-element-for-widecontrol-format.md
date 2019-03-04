---
title: Elemento WideEntry para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856531"
---
# <a name="wideentry-element-for-widecontrol-format"></a>Elemento WideEntry para WideControl (formato)

Proporciona una definición de la vista ampliada.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) WideEntry elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `WideEntry` elemento. Debe especificar una sola `WideItem` elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Elemento opcional.<br /><br /> Define los tipos de .NET que usan esta definición de entrada amplia o la condición que debe existir para que esta definición para usarse.|
|[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)|Elemento necesario.<br /><br /> Define la propiedad o el script cuyo valor se muestra.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)|Proporciona las definiciones de la vista ampliada.|

## <a name="remarks"></a>Observaciones

Una vista amplia es un formato de lista que muestra un solo valor de propiedad o valor de la secuencia de comandos para cada objeto. A diferencia de otros tipos de vistas, puede especificar solo un elemento de elemento para cada definición de vista. Para obtener más información acerca de los demás componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `WideEntry` elemento que define una sola `WideItem` elemento. El `WideItem` elemento define la propiedad cuyo valor se muestra en la vista.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Para obtener un ejemplo completo de una vista amplia, consulte [vista amplia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[Creación de una vista amplia](./creating-a-wide-view.md)

[Elemento SelectionCondition para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento TypeName para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)

[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
