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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363704"
---
# <a name="formatting-displayed-data"></a>Datos de formato mostrados

Puede especificar cómo se muestran los puntos de datos individuales en la lista, la tabla o la vista ampliada. Puede usar el elemento `FormatString` al definir los elementos de la vista, o puede usar el elemento `ScriptBlock` para llamar al método `FormatString` en los datos.

## <a name="using-the-formatstring-element"></a>Usar el elemento FormatString

En el ejemplo siguiente, se da formato al valor de la propiedad `TotalProcessorTime` del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) mediante el elemento FormatString. la propiedad `TotalProcessorTime`

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



