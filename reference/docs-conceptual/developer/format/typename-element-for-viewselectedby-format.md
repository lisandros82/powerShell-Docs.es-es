---
title: Elemento TypeName para ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361444"
---
# <a name="typename-element-for-viewselectedby-format"></a>Elemento TypeName para ViewSelectedBy (formato)

Especifica un objeto .NET que se muestra en la vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ViewSelectedBy (Format) elemento TypeName para ViewSelectedBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `TypeName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md)|Define los objetos .NET que se muestran en la vista.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observaciones

Para obtener más información sobre cómo se usa este elemento en diferentes vistas, vea [crear una vista de tabla](./creating-a-table-view.md), [crear una vista de lista](./creating-a-list-view.md), [crear una vista amplia](./creating-a-wide-view.md)y [componentes de vista personalizada](./creating-custom-controls.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo especificar el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) para una vista de lista. Se usa el mismo esquema para las vistas de tabla, ancho y personalizado.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Véase también

[Crear una vista de lista](./creating-a-list-view.md)

[Crear una vista de tabla](./creating-a-table-view.md)

[Crear una vista amplia](./creating-a-wide-view.md)

[Creación de controles personalizados](./creating-custom-controls.md)

[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
