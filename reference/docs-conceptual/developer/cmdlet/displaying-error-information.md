---
title: Mostrando información de error | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369974"
---
# <a name="displaying-error-information"></a>Muestra de información del error

En este tema se describen las formas en que los usuarios pueden mostrar información de errores.

Cuando el cmdlet se encuentra con un error, la presentación de la información de error será, de forma predeterminada, similar a la siguiente salida de error.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Sin embargo, los usuarios pueden ver los errores por categoría estableciendo la variable `$ErrorView` en `"CategoryView"`. La vista de categorías muestra información específica del registro de errores en lugar de una descripción de texto libre del error. Esta vista puede resultar útil si tiene una larga lista de errores que se van a examinar. En la vista por categorías, el mensaje de error anterior se muestra a continuación.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Para obtener más información sobre las categorías de error, consulte [registros de errores de Windows PowerShell](./windows-powershell-error-records.md).

## <a name="see-also"></a>Véase también

[Registros de errores de Windows PowerShell](./windows-powershell-error-records.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
