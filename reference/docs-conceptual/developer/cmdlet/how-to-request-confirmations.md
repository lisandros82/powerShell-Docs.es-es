---
title: Cómo solicitar confirmaciones | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369684"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="25078-102">Cómo solicitar confirmaciones</span><span class="sxs-lookup"><span data-stu-id="25078-102">How to Request Confirmations</span></span>

<span data-ttu-id="25078-103">En este ejemplo se muestra cómo llamar a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) para solicitar las confirmaciones del usuario antes de que se realice una acción.</span><span class="sxs-lookup"><span data-stu-id="25078-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25078-104">Para obtener más información sobre cómo Windows PowerShell controla estas solicitudes, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="25078-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="25078-105">Para solicitar confirmación</span><span class="sxs-lookup"><span data-stu-id="25078-105">To request confirmation</span></span>

1. <span data-ttu-id="25078-106">Asegúrese de que el parámetro `SupportsShouldProcess` del atributo cmdlet esté establecido en `true`.</span><span class="sxs-lookup"><span data-stu-id="25078-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="25078-107">(En el caso de las funciones, es un parámetro del atributo CmdletBinding).</span><span class="sxs-lookup"><span data-stu-id="25078-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="25078-108">Agregue un parámetro `Force` a su cmdlet para que el usuario pueda invalidar una solicitud de confirmación.</span><span class="sxs-lookup"><span data-stu-id="25078-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="25078-109">Agregue una instrucción `if` que use el valor devuelto del método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) para determinar si se llama al método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) .</span><span class="sxs-lookup"><span data-stu-id="25078-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="25078-110">Agregue una segunda instrucción `if` que use el valor devuelto del método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) y el valor del parámetro `Force` para determinar si se debe realizar la operación.</span><span class="sxs-lookup"><span data-stu-id="25078-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="25078-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="25078-111">Example</span></span>

<span data-ttu-id="25078-112">En el ejemplo de código siguiente, se llama a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) desde la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="25078-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="25078-113">Sin embargo, también puede llamar a estos métodos desde los otros métodos de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="25078-113">However, you can also call these methods from the other input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="25078-114">Véase también</span><span class="sxs-lookup"><span data-stu-id="25078-114">See Also</span></span>

[<span data-ttu-id="25078-115">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="25078-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
