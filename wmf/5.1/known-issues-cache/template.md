---
title: "plantilla de ejemplo de una escritura de problema o limitación conocida"
contributor: 
ms.openlocfilehash: e3b98044902cb6665e06582c8259bd5defd6f2ca
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
>Nota: Especifique un título descriptivo propuesto y una breve descripción

## <a name="example-erroneous-executionpolicy-errors"></a>Ejemplo: Errores de ExecutionPolicy errónea ##
En Windows 7, el uso de módulos de PowerShell y recursos de DSC puede provocar la notificación de errores sobre ExecutionPolicy.

### <a name="resolution"></a>Solución

Para resolverlo, establezca **ExecutionPolicy** en **RemoteSigned**. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```
