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
# <a name="confirmation-messages"></a><span data-ttu-id="76773-102">Mensajes de confirmación</span><span class="sxs-lookup"><span data-stu-id="76773-102">Confirmation Messages</span></span>

<span data-ttu-id="76773-103">A continuación se muestran diferentes mensajes de confirmación que se pueden mostrar en función de las variantes de los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) a los que se llama.</span><span class="sxs-lookup"><span data-stu-id="76773-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="76773-104">Para ver el código de ejemplo que muestra cómo solicitar las confirmaciones, vea [Cómo solicitar confirmaciones](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="76773-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="76773-105">Especificar el recurso</span><span class="sxs-lookup"><span data-stu-id="76773-105">Specifying the Resource</span></span>

<span data-ttu-id="76773-106">Puede especificar el recurso que se va a cambiar mediante una llamada a [System. Management. Automation. cmdlet. ShouldProcess% 2A? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (método).</span><span class="sxs-lookup"><span data-stu-id="76773-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="76773-107">En este caso, debe proporcionar el recurso mediante el parámetro `target` del método y Windows PowerShell agrega la operación.</span><span class="sxs-lookup"><span data-stu-id="76773-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="76773-108">En el mensaje siguiente, el texto "perresource" es el recurso en el que se ha actuado y la operación es el nombre del comando que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="76773-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="76773-109">Si el usuario selecciona **sí** o **sí para todo** en la solicitud de confirmación (como se muestra en el ejemplo siguiente), se realiza una llamada al método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , lo que hace que se muestre un segundo mensaje de confirmación.</span><span class="sxs-lookup"><span data-stu-id="76773-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="76773-110">Especificar la operación y el recurso</span><span class="sxs-lookup"><span data-stu-id="76773-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="76773-111">Puede especificar el recurso que se va a cambiar y la operación que va a realizar el comando mediante una llamada a [System. Management. Automation. cmdlet. ShouldProcess% 2A? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (método).</span><span class="sxs-lookup"><span data-stu-id="76773-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="76773-112">En este caso, debe proporcionar el recurso mediante el parámetro `target` y la operación mediante el parámetro `target`.</span><span class="sxs-lookup"><span data-stu-id="76773-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="76773-113">En el mensaje siguiente, el texto "perresource" es el recurso en el que se ha actuado y "OnAction" es la operación que se va a realizar.</span><span class="sxs-lookup"><span data-stu-id="76773-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="76773-114">Si el usuario selecciona **sí** o **sí para todo** en el mensaje anterior, se realiza una llamada al método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , lo que hace que se muestre un segundo mensaje de confirmación.</span><span class="sxs-lookup"><span data-stu-id="76773-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="76773-115">Véase también</span><span class="sxs-lookup"><span data-stu-id="76773-115">See Also</span></span>

[<span data-ttu-id="76773-116">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="76773-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
