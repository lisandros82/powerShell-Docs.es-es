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
# <a name="creating-custom-controls"></a><span data-ttu-id="e75e0-102">Creación de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="e75e0-102">Creating Custom Controls</span></span>

<span data-ttu-id="e75e0-103">Los controles personalizados son los componentes más flexibles de un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="e75e0-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="e75e0-104">A diferencia de las vistas de tabla, lista y ancho que definen una estructura formal de datos, como una tabla de datos, los controles personalizados permiten definir cómo se muestra un fragmento de datos individual.</span><span class="sxs-lookup"><span data-stu-id="e75e0-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="e75e0-105">Puede definir un conjunto común de controles personalizados que están disponibles para todas las vistas del archivo de formato, puede definir controles personalizados que están disponibles para una vista específica, o puede definir un conjunto de controles que están disponibles para un grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="e75e0-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="e75e0-106">Ejemplo de control personalizado</span><span class="sxs-lookup"><span data-stu-id="e75e0-106">Custom Control Example</span></span>

<span data-ttu-id="e75e0-107">En el ejemplo siguiente se muestra un control personalizado que se define en el archivo Certificates. Format. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="e75e0-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="e75e0-108">Este control personalizado se utiliza para separar los objetos [System. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) mostrados en una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="e75e0-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e75e0-109">Véase también</span><span class="sxs-lookup"><span data-stu-id="e75e0-109">See Also</span></span>

[<span data-ttu-id="e75e0-110">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e75e0-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
