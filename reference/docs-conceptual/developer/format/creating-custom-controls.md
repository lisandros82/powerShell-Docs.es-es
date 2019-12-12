---
title: Crear controles personalizados | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363384"
---
# <a name="creating-custom-controls"></a>Creación de controles personalizados

Los controles personalizados son los componentes más flexibles de un archivo de formato. A diferencia de las vistas de tabla, lista y ancho que definen una estructura formal de datos, como una tabla de datos, los controles personalizados permiten definir cómo se muestra un fragmento de datos individual. Puede definir un conjunto común de controles personalizados que están disponibles para todas las vistas del archivo de formato, puede definir controles personalizados que están disponibles para una vista específica, o puede definir un conjunto de controles que están disponibles para un grupo de objetos.

## <a name="custom-control-example"></a>Ejemplo de control personalizado

En el ejemplo siguiente se muestra un control personalizado que se define en el archivo Certificates. Format. ps1xml. Este control personalizado se utiliza para separar los objetos [System. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) mostrados en una vista de tabla.

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
