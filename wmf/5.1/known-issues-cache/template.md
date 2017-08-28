---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: "plantilla de ejemplo de una escritura de problema o limitación conocida"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
>Nota: Especifique un título descriptivo propuesto y una breve descripción

## <a name="example-erroneous-executionpolicy-errors"></a>Ejemplo: Errores de ExecutionPolicy errónea ##
En Windows 7, el uso de módulos de PowerShell y recursos de DSC puede provocar la notificación de errores sobre ExecutionPolicy.

### <a name="resolution"></a>Solución

Para resolverlo, establezca **ExecutionPolicy** en **RemoteSigned**. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```

