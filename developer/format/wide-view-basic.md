---
title: Vista amplia (Basic) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083746"
---
# <a name="wide-view-basic"></a>Vista amplia (Basic)

¿En este ejemplo se muestra cómo implementar una vista amplia básica que muestra la [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) los objetos devueltos por la `Get-Service` cmdlet. Para obtener más información acerca de los componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Para cargar este archivo de formato

1. Copie el XML de la sección de ejemplo de este tema en un archivo de texto.

2. Guarde el archivo de texto. No olvide agregar el `format.ps1xml` extensión al archivo para identificarlo como un archivo de formato.

3. Abra Windows PowerShell y ejecute el siguiente comando para cargar el archivo de formato en la sesión actual: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Este archivo de formato define la presentación de un objeto que ya está definido por un archivo de formato de Windows PowerShell. Debe usar el `prependPath` parámetro cuando se ejecuta el cmdlet, y no se puede cargar este formato de archivo como un módulo.

## <a name="demonstrates"></a>Muestra

Este archivo de formato muestra los elementos XML siguientes:

- El [nombre](./name-element-for-view-format.md) (elemento) para la vista.

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define los objetos que se muestran en la vista.

- El [WideItem](./wideitem-element-for-widecontrol-format.md) elemento que define qué propiedad se muestra la vista.

## <a name="example"></a>Ejemplo

El código XML siguiente define una vista amplia que muestra el valor de la [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) propiedad.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a>Véase también

[Ejemplos de archivos de formato](./examples-of-formatting-files.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
