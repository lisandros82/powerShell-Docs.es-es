---
title: Cómo declarar parámetros dinámicos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364424"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="aa93f-102">Cómo declarar los parámetros dinámicos</span><span class="sxs-lookup"><span data-stu-id="aa93f-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="aa93f-103">En este ejemplo se muestra cómo definir los parámetros dinámicos que se agregan al cmdlet en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="aa93f-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="aa93f-104">En este ejemplo, el parámetro `Department` se agrega al cmdlet siempre que el usuario especifica el parámetro de modificador `Employee`.</span><span class="sxs-lookup"><span data-stu-id="aa93f-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="aa93f-105">Para obtener más información sobre los parámetros dinámicos, consulte [parámetros dinámicos de cmdlet](./cmdlet-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="aa93f-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="aa93f-106">Para definir los parámetros dinámicos</span><span class="sxs-lookup"><span data-stu-id="aa93f-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="aa93f-107">En la declaración de clase de cmdlet, agregue la interfaz [System. Management. Automation. Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) como se muestra.</span><span class="sxs-lookup"><span data-stu-id="aa93f-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="aa93f-108">Llame al método [System. Management. Automation. Idynamicparameters. Getdynamicparameters \*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) , que devuelve el objeto en el que se definen los parámetros dinámicos.</span><span class="sxs-lookup"><span data-stu-id="aa93f-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="aa93f-109">En este ejemplo, se llama al método cuando se especifica el parámetro `Employee`.</span><span class="sxs-lookup"><span data-stu-id="aa93f-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

   ```csharp
   public object GetDynamicParameters()
   {
       if (employee)
       {
         context= new SendGreetingCommandDynamicParameters();
         return context;
       }
       return null;
   }
   private SendGreetingCommandDynamicParameters context;
   ```

3. <span data-ttu-id="aa93f-110">Declare una clase que defina los parámetros dinámicos que se van a agregar.</span><span class="sxs-lookup"><span data-stu-id="aa93f-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="aa93f-111">Puede usar los atributos que usó para declarar los parámetros de cmdlet estáticos para declarar los parámetros dinámicos.</span><span class="sxs-lookup"><span data-stu-id="aa93f-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

   ```csharp
   public class SendGreetingCommandDynamicParameters
   {
     [Parameter]
     [ValidateSet ("Marketing", "Sales", "Development")]
     public string Department
     {
       get { return department; }
       set { department = value; }
     }
     private string department;
   }
   ```

## <a name="example"></a><span data-ttu-id="aa93f-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="aa93f-112">Example</span></span>

<span data-ttu-id="aa93f-113">En este ejemplo, se agrega el parámetro `Department` cada vez que el usuario especifica el parámetro `Employee`.</span><span class="sxs-lookup"><span data-stu-id="aa93f-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="aa93f-114">El parámetro `Department` es un parámetro opcional y el atributo ValidateSet se usa para especificar los argumentos permitidos.</span><span class="sxs-lookup"><span data-stu-id="aa93f-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
    public object GetDynamicParameters()
    {
      if (employee)
      {
        context= new SendGreetingCommandDynamicParameters();
        return context;
      }
      return null;
   }
   private SendGreetingCommandDynamicParameters context;

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
  public class SendGreetingCommandDynamicParameters
  {
    [Parameter]
    [ValidateSet ("Marketing", "Sales", "Development")]
    public string Department
    {
      get { return department; }
      set { department = value; }
    }
    private string department;
  }
}
```

## <a name="see-also"></a><span data-ttu-id="aa93f-115">Véase también</span><span class="sxs-lookup"><span data-stu-id="aa93f-115">See Also</span></span>

[<span data-ttu-id="aa93f-116">System. Management. Automation. Runtimedefinedparameterdictionary</span><span class="sxs-lookup"><span data-stu-id="aa93f-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="aa93f-117">System. Management. Automation. Idynamicparameters. Getdynamicparameters \*</span><span class="sxs-lookup"><span data-stu-id="aa93f-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="aa93f-118">Parámetros dinámicos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="aa93f-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="aa93f-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="aa93f-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)