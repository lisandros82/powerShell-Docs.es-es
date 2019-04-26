---
title: Mostrar información de Error | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068290"
---
# <a name="displaying-error-information"></a>Muestra de información del error

En este tema se describe las maneras en que los usuarios pueden mostrar información de error.

Cuando el cmdlet encuentra un error, la presentación de la información de error será, de forma predeterminada, similar a la siguiente salida de error.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Sin embargo, los usuarios pueden ver los errores por categoría estableciendo el `$ErrorView` variable `"CategoryView"`. Vista por categorías muestra información específica desde el registro de error en lugar de una descripción textual del error. Esta vista puede ser útil si tiene una larga lista de errores de análisis. En la vista por categorías, el mensaje de error anterior se muestra como se indica a continuación.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Para obtener más información acerca de las categorías de error, consulte [registros de Error de Windows PowerShell](./windows-powershell-error-records.md).

## <a name="see-also"></a>Véase también

[Registros de errores de PowerShell de Windows](./windows-powershell-error-records.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
