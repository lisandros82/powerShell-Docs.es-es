---
title: Mensajes de confirmación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365734"
---
# <a name="confirmation-messages"></a>Mensajes de confirmación

A continuación se muestran diferentes mensajes de confirmación que se pueden mostrar en función de las variantes de los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) a los que se llama.

> [!IMPORTANT]
> Para ver el código de ejemplo que muestra cómo solicitar las confirmaciones, vea [Cómo solicitar confirmaciones](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Especificar el recurso

Puede especificar el recurso que se va a cambiar mediante una llamada a [System. Management. Automation. cmdlet. ShouldProcess% 2A? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (método). En este caso, debe proporcionar el recurso mediante el parámetro `target` del método y Windows PowerShell agrega la operación. En el mensaje siguiente, el texto "perresource" es el recurso en el que se ha actuado y la operación es el nombre del comando que realiza la llamada.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Si el usuario selecciona **sí** o **sí para todo** en la solicitud de confirmación (como se muestra en el ejemplo siguiente), se realiza una llamada al método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , lo que hace que se muestre un segundo mensaje de confirmación.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Especificar la operación y el recurso

Puede especificar el recurso que se va a cambiar y la operación que va a realizar el comando mediante una llamada a [System. Management. Automation. cmdlet. ShouldProcess% 2A? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (método). En este caso, debe proporcionar el recurso mediante el parámetro `target` y la operación mediante el parámetro `target`. En el mensaje siguiente, el texto "perresource" es el recurso en el que se ha actuado y "OnAction" es la operación que se va a realizar.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Si el usuario selecciona **sí** o **sí para todo** en el mensaje anterior, se realiza una llamada al método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , lo que hace que se muestre un segundo mensaje de confirmación.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
