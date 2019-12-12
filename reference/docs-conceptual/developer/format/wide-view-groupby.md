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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367954"
---
# <a name="wide-view-groupby"></a>Vista amplia (GroupBy)

En este ejemplo se muestra cómo implementar una vista amplia que muestra grupos de [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos devueltos por el cmdlet `Get-Service`. Para obtener más información sobre los componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Para cargar este archivo de formato

1. Copie el XML de la sección de ejemplo de este tema en un archivo de texto.

2. Guarde el archivo de texto. Asegúrese de agregar la extensión de `format.ps1xml` al archivo para identificarlo como un archivo de formato.

3. Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Este archivo de formato define la presentación de un objeto que ya está definido por los archivos de formato de Windows PowerShell. Debe usar el parámetro `prependPath` al ejecutar el cmdlet y no puede cargar este archivo de formato como un módulo.

## <a name="demonstrates"></a>Demuestra

Este archivo de formato muestra los siguientes elementos XML:

- Elemento [Name](./name-element-for-view-format.md) de la vista.

- El elemento [ViewSelectedBy](./viewselectedby-element-format.md) que define qué objetos se muestran en la vista.

- El elemento [GroupBy](./groupby-element-for-view-format.md) que define cuándo se muestra un nuevo grupo.

- El elemento [WideItem](./wideitem-element-for-widecontrol-format.md) que define la propiedad que se muestra en la vista.

## <a name="example"></a>Ejemplo

En el código XML siguiente se define una vista amplia que muestra grupos de objetos. Cada nuevo grupo se inicia cuando cambia el valor de la propiedad [System. ServiceProcess. ServiceController. serviceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .

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

En el ejemplo siguiente se muestra cómo Windows PowerShell muestra [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos después de cargar este archivo de formato.

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
