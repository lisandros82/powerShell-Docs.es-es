---
title: Elemento PropertyName para WideItem para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364944"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>Elemento PropertyName para WideItem for WideControl (formato)

Especifica la propiedad del objeto cuyo valor se muestra en la vista amplia.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)

## <a name="syntax"></a>Sintaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en la vista amplia.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad cuyo valor se muestra.

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra una vista amplia que muestra el valor de la propiedad processName del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>Véase también

[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Crear una vista amplia](./creating-a-wide-view.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
