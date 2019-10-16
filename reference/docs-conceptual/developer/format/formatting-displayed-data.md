---
title: Aplicar formato a los datos mostrados | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363704"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="5e59b-102">Datos de formato mostrados</span><span class="sxs-lookup"><span data-stu-id="5e59b-102">Formatting Displayed Data</span></span>

<span data-ttu-id="5e59b-103">Puede especificar cómo se muestran los puntos de datos individuales en la lista, la tabla o la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="5e59b-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="5e59b-104">Puede usar el elemento `FormatString` al definir los elementos de la vista, o puede usar el elemento `ScriptBlock` para llamar al método `FormatString` en los datos.</span><span class="sxs-lookup"><span data-stu-id="5e59b-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="5e59b-105">Usar el elemento FormatString</span><span class="sxs-lookup"><span data-stu-id="5e59b-105">Using the FormatString Element</span></span>

<span data-ttu-id="5e59b-106">En el ejemplo siguiente, se da formato al valor de la propiedad `TotalProcessorTime` del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) mediante el elemento FormatString.</span><span class="sxs-lookup"><span data-stu-id="5e59b-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="5e59b-107">la propiedad `TotalProcessorTime`</span><span class="sxs-lookup"><span data-stu-id="5e59b-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



