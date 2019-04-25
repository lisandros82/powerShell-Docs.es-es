---
title: Elemento WideEntries para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083695"
---
# <a name="wideentries-element-for-widecontrol-format"></a>Elemento WideEntries para WideControl (formato)

Proporciona las definiciones de la vista ampliada. La vista ampliada debe especificar una o varias definiciones.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) WideEntries elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `WideEntries` elemento. Debe especificarse al menos un elemento secundario.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Proporciona una definición de la vista ampliada.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideControl (formato)](./widecontrol-element-format.md)|Define una amplia (valor single) formato de lista para la vista.|

## <a name="remarks"></a>Observaciones

Una vista amplia es un formato de lista que muestra un solo valor de propiedad o valor de la secuencia de comandos para cada objeto. Para obtener más información acerca de los componentes de una vista amplia, consulte [los componentes de vista amplia](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `WideEntries` elemento que define una sola `WideEntry` elemento. El `WideEntry` elemento contiene un único `WideItem` elemento que define qué valor de propiedad o el script se muestra en la vista.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Para obtener un ejemplo completo de una vista amplia, consulte [vista amplia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Véase también

[Creación de una vista amplia](./creating-a-wide-view.md)

[Elemento WideControl (formato)](./widecontrol-element-format.md)

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
