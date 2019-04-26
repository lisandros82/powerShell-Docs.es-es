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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067848"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="c2d6a-102">Cómo solicitar confirmaciones</span><span class="sxs-lookup"><span data-stu-id="c2d6a-102">How to Request Confirmations</span></span>

<span data-ttu-id="c2d6a-103">En este ejemplo se muestra cómo llamar a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para solicitar confirmaciones desde el usuario antes de que se realiza una acción.</span><span class="sxs-lookup"><span data-stu-id="c2d6a-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2d6a-104">Para obtener más información acerca de cómo Windows PowerShell trata estas solicitudes, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="c2d6a-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="c2d6a-105">Para solicitar confirmación</span><span class="sxs-lookup"><span data-stu-id="c2d6a-105">To request confirmation</span></span>

1. <span data-ttu-id="c2d6a-106">Asegúrese de que el `SupportsShouldProcess` parámetro del atributo de Cmdlet se establece en `true`.</span><span class="sxs-lookup"><span data-stu-id="c2d6a-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="c2d6a-107">(Para las funciones de esto es un parámetro del atributo CmdletBinding).</span><span class="sxs-lookup"><span data-stu-id="c2d6a-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="c2d6a-108">Agregar un `Force` parámetro al cmdlet para que el usuario puede invalidar una solicitud de confirmación.</span><span class="sxs-lookup"><span data-stu-id="c2d6a-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="c2d6a-109">Agregar un `if` instrucción que usa el valor devuelto de la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para determinar si el [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) se llama al método.</span><span class="sxs-lookup"><span data-stu-id="c2d6a-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="c2d6a-110">Agregue un segundo `if` instrucción que usa el valor devuelto de la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método y el valor de la `Force` parámetro para determinar si la operación debe ser puede realizar.</span><span class="sxs-lookup"><span data-stu-id="c2d6a-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="c2d6a-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c2d6a-111">Example</span></span>

<span data-ttu-id="c2d6a-112">En el ejemplo de código siguiente, la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos se llaman desde dentro de la invalidación de la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="c2d6a-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="c2d6a-113">Sin embargo, también puede llamar a estos métodos de la entrada de otra métodos de procesamiento.</span><span class="sxs-lookup"><span data-stu-id="c2d6a-113">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c2d6a-114">Véase también</span><span class="sxs-lookup"><span data-stu-id="c2d6a-114">See Also</span></span>

[<span data-ttu-id="c2d6a-115">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2d6a-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
