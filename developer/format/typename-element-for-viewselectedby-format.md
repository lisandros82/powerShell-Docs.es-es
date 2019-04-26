---
title: Elemento TypeName para ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083763"
---
# <a name="typename-element-for-viewselectedby-format"></a>Elemento TypeName para ViewSelectedBy (formato)

Especifica un objeto .NET que se muestra la vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ViewSelectedBy (formato) TypeName elemento de configuración ViewSelectedBy (formato)

## <a name="syntax"></a>Sintaxis

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y los elementos primarios de la `TypeName` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)|Define los objetos de .NET que se muestran en la vista.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observaciones

Para obtener más información sobre cómo se usa este elemento en distintas vistas, consulte [crear una vista de tabla](./creating-a-table-view.md), [crear una vista de lista](./creating-a-list-view.md), [crear una vista amplia](./creating-a-wide-view.md), y [ Componentes de vista personalizada](./creating-custom-controls.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo especificar el [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto para obtener una vista de lista. Se usa el mismo esquema para las vistas de tabla, amplia y personalizadas.

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

[Creación de una vista de lista](./creating-a-list-view.md)

[Creación de una vista de tabla](./creating-a-table-view.md)

[Creación de una vista amplia](./creating-a-wide-view.md)

[Creación de controles personalizados](./creating-custom-controls.md)

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
