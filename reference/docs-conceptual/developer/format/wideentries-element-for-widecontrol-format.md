---
title: Elemento WideEntries para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361434"
---
# <a name="wideentries-element-for-widecontrol-format"></a>Elemento WideEntries para WideControl (formato)

Proporciona las definiciones de la vista amplia. La vista ancha debe especificar una o más definiciones.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format)

## <a name="syntax"></a>Sintaxis

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `WideEntries`. Se debe especificar al menos un elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Proporciona una definición de la vista amplia.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideControl (Format)](./widecontrol-element-format.md)|Define un formato de lista ancho (valor único) para la vista.|

## <a name="remarks"></a>Observaciones

Una vista amplia es un formato de lista que muestra un valor de propiedad único o un valor de script para cada objeto. Para obtener más información sobre los componentes de una vista amplia, vea [componentes de vista ancha](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un elemento `WideEntries` que define un solo elemento `WideEntry`. El elemento `WideEntry` contiene un solo elemento `WideItem` que define qué propiedad o valor de script se muestra en la vista.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Para obtener un ejemplo completo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[Crear una vista amplia](./creating-a-wide-view.md)

[Elemento WideControl (Format)](./widecontrol-element-format.md)

[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
