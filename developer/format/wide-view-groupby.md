---
title: Vista amplia (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861631"
---
# <a name="wide-view-groupby"></a>Vista amplia (GroupBy)

¿En este ejemplo se muestra cómo implementar una vista amplia que muestra los grupos de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) los objetos devueltos por la `Get-Service` cmdlet. Para obtener más información acerca de los componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Para cargar este archivo de formato

1. Copie el XML de la sección de ejemplo de este tema en un archivo de texto.

2. Guarde el archivo de texto. No olvide agregar el `format.ps1xml` extensión al archivo para identificarlo como un archivo de formato.

3. Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Este archivo de formato define la presentación de un objeto que ya está definido por un archivos de formato de Windows PowerShell. Debe usar el `prependPath` parámetro cuando se ejecuta el cmdlet, y no se puede cargar este formato de archivo como un módulo.

## <a name="demonstrates"></a>Demostraciones

Este archivo de formato muestra los elementos XML siguientes:

- El [nombre](./name-element-for-view-format.md) (elemento) para la vista.

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define los objetos que se muestran en la vista.

- El [GroupBy](./groupby-element-for-view-format.md) elemento que define cuándo se muestra un nuevo grupo.

- El [WideItem](./wideitem-element-for-widecontrol-format.md) elemento que define qué propiedad se muestra la vista.

## <a name="example"></a>Ejemplo

El código XML siguiente define una vista amplia que muestra los grupos de objetos. Cada nuevo grupo se inicia cuando el valor de la [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) los cambios de propiedad.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

¿El ejemplo siguiente muestra cómo Windows PowerShell muestra el [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de carga este archivo de formato.

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a>Véase también

[Ejemplos de archivos de formato](./examples-of-formatting-files.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
