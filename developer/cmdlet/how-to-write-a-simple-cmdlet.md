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
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="fff9d-102">Cómo escribir un cmdlet</span><span class="sxs-lookup"><span data-stu-id="fff9d-102">How to write a cmdlet</span></span>

<span data-ttu-id="fff9d-103">En este artículo se muestra cómo escribir un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fff9d-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="fff9d-104">El `Send-Greeting` cmdlet toma un nombre de usuario único como entrada y, a continuación, escribe un saludo para ese usuario.</span><span class="sxs-lookup"><span data-stu-id="fff9d-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="fff9d-105">Aunque el cmdlet no hace mucho trabajo, este ejemplo muestra las secciones principales de un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fff9d-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="fff9d-106">Pasos para escribir un cmdlet</span><span class="sxs-lookup"><span data-stu-id="fff9d-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="fff9d-107">Para declarar la clase como un cmdlet, use el **Cmdlet** atributo.</span><span class="sxs-lookup"><span data-stu-id="fff9d-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="fff9d-108">El **Cmdlet** atributo especifica el verbo y el nombre para el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fff9d-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="fff9d-109">Para obtener más información sobre la **Cmdlet** atributo, vea [declaración CmdletAttribute](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="fff9d-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="fff9d-110">Especifique el nombre de la clase.</span><span class="sxs-lookup"><span data-stu-id="fff9d-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="fff9d-111">Especificar que el cmdlet se deriva de cualquiera de las clases siguientes:</span><span class="sxs-lookup"><span data-stu-id="fff9d-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="fff9d-112">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fff9d-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="fff9d-113">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="fff9d-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="fff9d-114">Para definir los parámetros del cmdlet, use el **parámetro** atributo.</span><span class="sxs-lookup"><span data-stu-id="fff9d-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="fff9d-115">En este caso, sólo uno obligatorio se especifican parámetros.</span><span class="sxs-lookup"><span data-stu-id="fff9d-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="fff9d-116">Para obtener más información sobre la **parámetro** atributo, vea [ParameterAttribute declaración](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="fff9d-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="fff9d-117">Invalide el método que procesa la entrada de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="fff9d-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="fff9d-118">En este caso, el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) se invalida el método.</span><span class="sxs-lookup"><span data-stu-id="fff9d-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="fff9d-119">Para escribir el saludo, use el método [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="fff9d-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="fff9d-120">El saludo se muestra en el siguiente formato:</span><span class="sxs-lookup"><span data-stu-id="fff9d-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="fff9d-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fff9d-121">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fff9d-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="fff9d-122">See also</span></span>

[<span data-ttu-id="fff9d-123">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fff9d-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="fff9d-124">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="fff9d-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="fff9d-125">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="fff9d-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="fff9d-126">System.Management.Automation.Cmdlet.WriteObject</span><span class="sxs-lookup"><span data-stu-id="fff9d-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="fff9d-127">Declaración CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="fff9d-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="fff9d-128">Declaración ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="fff9d-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="fff9d-129">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fff9d-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)