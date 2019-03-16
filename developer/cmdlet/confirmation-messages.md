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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059480"
---
# <a name="confirmation-messages"></a>Mensajes de confirmación

Estos son los mensajes de confirmación diferente que se pueden mostrar según las variantes de la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.ShouldContinue ](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos que se llaman.

> [!IMPORTANT]
> Ver código de ejemplo que se muestra cómo solicitar confirmaciones [cómo las confirmaciones de la solicitud](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Especifica el recurso

¿Puede especificar el recurso que se va a cambiarse mediante una llamada a la [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método. En este caso, proporcione el recurso mediante la `target` parámetro del método y la operación se agrega mediante Windows PowerShell. En el siguiente mensaje, el texto "MyResource" es el recurso ha actuado sobre y la operación es el nombre del comando que realiza la llamada.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Si el usuario selecciona **Sí** o **sí a todo** a la confirmación de solicitud (como se muestra en el ejemplo siguiente), una llamada a la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)se realiza el método, lo que hace que un segundo mensaje de confirmación que se mostrará.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Especifica la operación y el recurso

¿Puede especificar el recurso que se va a cambiar y la operación que el comando que se va a realizar mediante una llamada a la [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método. En este caso, proporcione el recurso mediante la `target` parámetro y la operación utilizando el `target` parámetro. En el siguiente mensaje, el texto "MyResource" es el recurso ha actuado sobre y "MyAction" es realizar la operación.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Si el usuario selecciona **Sí** o **sí a todo** al mensaje anterior, una llamada a la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método se realiza, lo que hace que un segundo mensaje de confirmación que se mostrará.

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
