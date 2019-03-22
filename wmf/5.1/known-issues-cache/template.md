---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: plantilla de ejemplo de una escritura de problema o limitación conocida
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794505"
---
 >Nota: Especifique un título descriptivo propuesto y una breve descripción

## <a name="example-erroneous-executionpolicy-errors"></a>Ejemplo: errores de ExecutionPolicy errónea
En Windows 7, el uso de módulos de PowerShell y recursos de DSC puede provocar la notificación de errores sobre ExecutionPolicy.

### <a name="resolution"></a>Solución

Para resolverlo, establezca **ExecutionPolicy** en **RemoteSigned**. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```
