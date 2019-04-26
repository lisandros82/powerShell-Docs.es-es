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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065672"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="5b0af-102">Datos de formato mostrados</span><span class="sxs-lookup"><span data-stu-id="5b0af-102">Formatting Displayed Data</span></span>

<span data-ttu-id="5b0af-103">Puede especificar cómo se muestran los puntos de datos individuales en la lista, tabla o vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="5b0af-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="5b0af-104">Puede usar el `FormatString` elemento al definir los elementos de la vista, o bien puede usar el `ScriptBlock` elemento que se va a llamar a la `FormatString` método en los datos.</span><span class="sxs-lookup"><span data-stu-id="5b0af-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="5b0af-105">Mediante el elemento FormatString</span><span class="sxs-lookup"><span data-stu-id="5b0af-105">Using the FormatString Element</span></span>

<span data-ttu-id="5b0af-106">En el ejemplo siguiente, el valor de la `TotalProcessorTime` propiedad de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto tiene el formato mediante el elemento FormatString.</span><span class="sxs-lookup"><span data-stu-id="5b0af-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="5b0af-107">El `TotalProcessorTime` propiedad</span><span class="sxs-lookup"><span data-stu-id="5b0af-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



