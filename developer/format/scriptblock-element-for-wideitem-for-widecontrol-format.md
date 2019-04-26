---
title: Elemento de bloque de script para WideItem para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064210"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>Elemento ScriptBlock para WideItem for WideControl (formato)

Especifica la secuencia de comandos cuyo valor se muestra en la vista ampliada.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) elemento WideItem (formato) ScriptBlock elemento de configuración para WideItem (formato)

## <a name="syntax"></a>Sintaxis

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)|Define el bloque de script o la propiedad cuyo valor se muestra en la vista ampliada.|

## <a name="text-value"></a>Valor de texto

Especifique el script cuyo valor se muestra.

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de los componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

Este ejemplo se muestra un `WideItem` elemento que define una secuencia de comandos cuyo valor se muestra en la vista.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Véase también

[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)

[Creación de una vista amplia](./creating-a-wide-view.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
