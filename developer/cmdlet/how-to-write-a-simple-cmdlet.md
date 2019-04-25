---
title: Cómo escribir un Cmdlet sencillo | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067746"
---
# <a name="how-to-write-a-cmdlet"></a>Cómo escribir un cmdlet

En este artículo se muestra cómo escribir un cmdlet. El `Send-Greeting` cmdlet toma un nombre de usuario único como entrada y, a continuación, escribe un saludo para ese usuario. Aunque el cmdlet no hace mucho trabajo, este ejemplo muestra las secciones principales de un cmdlet.

## <a name="steps-to-write-a-cmdlet"></a>Pasos para escribir un cmdlet

1. Para declarar la clase como un cmdlet, use el **Cmdlet** atributo. El **Cmdlet** atributo especifica el verbo y el nombre para el nombre del cmdlet.

   Para obtener más información sobre la **Cmdlet** atributo, vea [declaración CmdletAttribute](cmdlet-attribute-declaration.md).

2. Especifique el nombre de la clase.

3. Especificar que el cmdlet se deriva de cualquiera de las clases siguientes:

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Para definir los parámetros del cmdlet, use el **parámetro** atributo. En este caso, sólo uno obligatorio se especifican parámetros.

   Para obtener más información sobre la **parámetro** atributo, vea [ParameterAttribute declaración](parameter-attribute-declaration.md).

5. Invalide el método que procesa la entrada de procesamiento de entrada. En este caso, el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) se invalida el método.

6. Para escribir el saludo, use el método [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   El saludo se muestra en el siguiente formato:

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>Ejemplo

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>Vea también

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[Declaración CmdletAttribute](cmdlet-attribute-declaration.md)

[Declaración ParameterAttribute](parameter-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](writing-a-windows-powershell-cmdlet.md)