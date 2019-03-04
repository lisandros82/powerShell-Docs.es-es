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
ms.openlocfilehash: 75214a3fe4bc019836f75db19fb873bd081f200f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861421"
---
# <a name="confirmation-messages"></a><span data-ttu-id="84290-102">Mensajes de confirmación</span><span class="sxs-lookup"><span data-stu-id="84290-102">Confirmation Messages</span></span>

<span data-ttu-id="84290-103">Estos son los mensajes de confirmación diferente que se pueden mostrar según las variantes de la [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [ System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos que se llaman.</span><span class="sxs-lookup"><span data-stu-id="84290-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84290-104">Ver código de ejemplo que se muestra cómo solicitar confirmaciones [cómo las confirmaciones de la solicitud](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="84290-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="84290-105">Especifica el recurso</span><span class="sxs-lookup"><span data-stu-id="84290-105">Specifying the Resource</span></span>

<span data-ttu-id="84290-106">¿Puede especificar el recurso que se va a cambiarse mediante una llamada a la [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="84290-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="84290-107">En este caso, proporcione el recurso mediante la `target` parámetro del método y la operación se agrega mediante Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84290-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="84290-108">En el siguiente mensaje, el texto "MyResource" es el recurso ha actuado sobre y la operación es el nombre del comando que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="84290-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="84290-109">Si el usuario selecciona **Sí** o **sí a todo** a la confirmación de solicitud (como se muestra en el ejemplo siguiente), una llamada a la [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) se realiza el método, lo que hace que un segundo mensaje de confirmación que se mostrará.</span><span class="sxs-lookup"><span data-stu-id="84290-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="84290-110">Especifica la operación y el recurso</span><span class="sxs-lookup"><span data-stu-id="84290-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="84290-111">¿Puede especificar el recurso que se va a cambiar y la operación que el comando que se va a realizar mediante una llamada a la [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="84290-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="84290-112">En este caso, proporcione el recurso mediante la `target` parámetro y la operación utilizando el `target` parámetro.</span><span class="sxs-lookup"><span data-stu-id="84290-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="84290-113">En el siguiente mensaje, el texto "MyResource" es el recurso ha actuado sobre y "MyAction" es realizar la operación.</span><span class="sxs-lookup"><span data-stu-id="84290-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="84290-114">Si el usuario selecciona **Sí** o **sí a todo** al mensaje anterior, una llamada a la [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método se realiza, lo que hace que un segundo mensaje de confirmación que se mostrará.</span><span class="sxs-lookup"><span data-stu-id="84290-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="84290-115">Véase también</span><span class="sxs-lookup"><span data-stu-id="84290-115">See Also</span></span>

[<span data-ttu-id="84290-116">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="84290-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
