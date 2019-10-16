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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364424"
---
# <a name="how-to-declare-dynamic-parameters"></a>Cómo declarar los parámetros dinámicos

En este ejemplo se muestra cómo definir los parámetros dinámicos que se agregan al cmdlet en tiempo de ejecución. En este ejemplo, el parámetro `Department` se agrega al cmdlet siempre que el usuario especifica el parámetro de modificador `Employee`. Para obtener más información sobre los parámetros dinámicos, consulte [parámetros dinámicos de cmdlet](./cmdlet-dynamic-parameters.md).

## <a name="to-define-dynamic-parameters"></a>Para definir los parámetros dinámicos

1. En la declaración de clase de cmdlet, agregue la interfaz [System. Management. Automation. Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) como se muestra.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. Llame al método [System. Management. Automation. Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) , que devuelve el objeto en el que se definen los parámetros dinámicos. En este ejemplo, se llama al método cuando se especifica el parámetro `Employee`.

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

3. Declare una clase que defina los parámetros dinámicos que se van a agregar. Puede usar los atributos que usó para declarar los parámetros de cmdlet estáticos para declarar los parámetros dinámicos.

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

## <a name="example"></a>Ejemplo

En este ejemplo, se agrega el parámetro `Department` siempre que el usuario especifica el parámetro `Employee`. El parámetro `Department` es un parámetro opcional y el atributo ValidateSet se usa para especificar los argumentos permitidos.

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

## <a name="see-also"></a>Véase también

[System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System. Management. Automation. Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Parámetros dinámicos de cmdlet](./cmdlet-dynamic-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)