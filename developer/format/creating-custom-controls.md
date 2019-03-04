---
title: Creación de controles personalizados | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853201"
---
# <a name="creating-custom-controls"></a>Creación de controles personalizados

Controles personalizados son los componentes más flexibles de un archivo de formato. A diferencia de la tabla, lista y vista amplia que definen una estructura formal de datos, como una tabla de datos, controles personalizados le permiten definir cómo se muestra un elemento individual de datos. Puede definir un conjunto común de controles personalizados que están disponibles para todas las vistas del archivo de formato, puede definir los controles personalizados que están disponibles para una vista específica o puede definir un conjunto de controles que están disponibles para un grupo de objetos.

## <a name="custom-control-example"></a>Ejemplo de Control personalizado

El ejemplo siguiente muestra un control personalizado que se define en el archivo Certificates.Format.ps1xml. Este control personalizado se usa para separar el [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objetos que se muestran en una vista de tabla.

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
