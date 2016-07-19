---
title: "plantilla de ejemplo de una escritura de problema o limitación conocida"
contributor: 
translationtype: Human Translation
ms.sourcegitcommit: a952a27ec1695ce9951c352446194cf72d18f50a
ms.openlocfilehash: cfe0a6562743f1df81acb81e33c120cb67f9042c

---

>Nota: Especifique un título descriptivo propuesto y una breve descripción

## Ejemplo: Errores de ExecutionPolicy errónea ##
En Windows 7, el uso de módulos de PowerShell y recursos de DSC puede provocar la notificación de errores sobre ExecutionPolicy.

### Solución

Para resolverlo, establezca **ExecutionPolicy** en **RemoteSigned**. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```



<!--HONumber=Jul16_HO1-->


