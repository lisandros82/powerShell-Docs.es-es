---
title: Tipos de parámetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369314"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="7777b-102">Tipos de parámetros del cmdlet</span><span class="sxs-lookup"><span data-stu-id="7777b-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="7777b-103">En este tema se describen los diferentes tipos de parámetros que se pueden declarar en los cmdlets de.</span><span class="sxs-lookup"><span data-stu-id="7777b-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="7777b-104">Los parámetros de cmdlet pueden ser posicionales, con nombre, obligatorios, opcionales o modificadores.</span><span class="sxs-lookup"><span data-stu-id="7777b-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="7777b-105">Parámetros posicionales y con nombre</span><span class="sxs-lookup"><span data-stu-id="7777b-105">Positional and Named Parameters</span></span>

<span data-ttu-id="7777b-106">Todos los parámetros de cmdlet son parámetros con nombre o posicionales.</span><span class="sxs-lookup"><span data-stu-id="7777b-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="7777b-107">Un parámetro con nombre requiere que escriba el nombre y el argumento del parámetro al llamar al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7777b-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="7777b-108">Un parámetro posicional solo requiere que se escriban los argumentos en orden relativo.</span><span class="sxs-lookup"><span data-stu-id="7777b-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="7777b-109">A continuación, el sistema asigna el primer argumento sin nombre al primer parámetro posicional.</span><span class="sxs-lookup"><span data-stu-id="7777b-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="7777b-110">El sistema asigna el segundo argumento sin nombre al segundo parámetro sin nombre, y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="7777b-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="7777b-111">De forma predeterminada, todos los parámetros de cmdlet son parámetros con nombre.</span><span class="sxs-lookup"><span data-stu-id="7777b-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="7777b-112">Para definir un parámetro con nombre, omita la palabra clave `Position` en la declaración de atributo de **parámetro** , tal y como se muestra en la siguiente declaración de parámetro.</span><span class="sxs-lookup"><span data-stu-id="7777b-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="7777b-113">Para definir un parámetro posicional, agregue la palabra clave `Position` en la declaración de atributo de parámetro y, a continuación, especifique una posición.</span><span class="sxs-lookup"><span data-stu-id="7777b-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="7777b-114">En el ejemplo siguiente, el parámetro `UserName` se declara como un parámetro posicional con la posición 0.</span><span class="sxs-lookup"><span data-stu-id="7777b-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="7777b-115">Esto significa que el primer argumento de la llamada se enlazará automáticamente a este parámetro.</span><span class="sxs-lookup"><span data-stu-id="7777b-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="7777b-116">Un buen diseño de cmdlet recomienda que los parámetros más usados se declaren como parámetros posicionales para que el usuario no tenga que escribir el nombre del parámetro cuando se ejecute el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7777b-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="7777b-117">Los parámetros con nombre y posicionales aceptan argumentos únicos o varios argumentos separados por comas.</span><span class="sxs-lookup"><span data-stu-id="7777b-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="7777b-118">Solo se permiten varios argumentos si el parámetro acepta una colección como una matriz de cadenas.</span><span class="sxs-lookup"><span data-stu-id="7777b-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="7777b-119">Puede mezclar parámetros posicionales y con nombre en el mismo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7777b-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="7777b-120">En este caso, el sistema recupera primero los argumentos con nombre y, a continuación, intenta asignar los argumentos sin nombre restantes a los parámetros posicionales.</span><span class="sxs-lookup"><span data-stu-id="7777b-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="7777b-121">Los siguientes comandos muestran las distintas formas en las que puede especificar argumentos únicos y varios para los parámetros del cmdlet `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="7777b-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="7777b-122">Observe que en los dos últimos ejemplos, no es necesario especificar **-Name** porque el parámetro `Name` se define como un parámetro posicional.</span><span class="sxs-lookup"><span data-stu-id="7777b-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="7777b-123">Parámetros obligatorios y opcionales</span><span class="sxs-lookup"><span data-stu-id="7777b-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="7777b-124">También puede definir parámetros de cmdlet como parámetros obligatorios u opcionales.</span><span class="sxs-lookup"><span data-stu-id="7777b-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="7777b-125">(Debe especificarse un parámetro obligatorio antes de que el tiempo de ejecución de Windows PowerShell invoque el cmdlet).  De forma predeterminada, los parámetros se definen como opcionales.</span><span class="sxs-lookup"><span data-stu-id="7777b-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="7777b-126">Para definir un parámetro obligatorio, agregue la palabra clave `Mandatory` en la declaración de atributo de parámetro y establézcala en `true`, tal como se muestra en la siguiente declaración de parámetro.</span><span class="sxs-lookup"><span data-stu-id="7777b-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="7777b-127">Para definir un parámetro opcional, omita la palabra clave `Mandatory` en la declaración de atributo de **parámetro** , tal y como se muestra en la siguiente declaración de parámetro.</span><span class="sxs-lookup"><span data-stu-id="7777b-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="7777b-128">Parámetros de modificador</span><span class="sxs-lookup"><span data-stu-id="7777b-128">Switch Parameters</span></span>

<span data-ttu-id="7777b-129">Windows PowerShell proporciona un tipo [System. Management. Automation. parámetrodemodificador](/dotnet/api/System.Management.Automation.SwitchParameter) que permite definir un parámetro cuyo valor se establece automáticamente en `false` si no se especifica el parámetro cuando se llama al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7777b-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="7777b-130">Siempre que sea posible, use parámetros de modificador en lugar de parámetros booleanos.</span><span class="sxs-lookup"><span data-stu-id="7777b-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="7777b-131">Considere el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="7777b-131">Consider the following sample.</span></span> <span data-ttu-id="7777b-132">De forma predeterminada, varios cmdlets de Windows PowerShell no pasan un objeto de salida a la canalización.</span><span class="sxs-lookup"><span data-stu-id="7777b-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="7777b-133">Sin embargo, estos cmdlets tienen un parámetro de modificador `PassThru` que invalida el comportamiento predeterminado.</span><span class="sxs-lookup"><span data-stu-id="7777b-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="7777b-134">Si se especifica el parámetro `PassThru` cuando se llama a estos cmdlets, el cmdlet devuelve un objeto de salida a la canalización.</span><span class="sxs-lookup"><span data-stu-id="7777b-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="7777b-135">Si necesita que el parámetro tenga un valor predeterminado de `true` cuando no se especifica el parámetro en la llamada, considere la posibilidad de invertir el sentido del parámetro.</span><span class="sxs-lookup"><span data-stu-id="7777b-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="7777b-136">Por ejemplo, en lugar de establecer el atributo Parameter en un valor booleano de `true`, declare la propiedad como el tipo [System. Management. Automation. parámetrodemodificador](/dotnet/api/System.Management.Automation.SwitchParameter) y, a continuación, establezca el valor predeterminado del parámetro en `false`.</span><span class="sxs-lookup"><span data-stu-id="7777b-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="7777b-137">Para definir un parámetro de modificador, declare la propiedad como el tipo [System. Management. Automation. parámetrodemodificador](/dotnet/api/System.Management.Automation.SwitchParameter) , como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="7777b-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="7777b-138">Para hacer que el cmdlet actúe sobre el parámetro cuando se especifica, utilice la siguiente estructura dentro de uno de los métodos de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="7777b-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="7777b-139">Véase también</span><span class="sxs-lookup"><span data-stu-id="7777b-139">See Also</span></span>

[<span data-ttu-id="7777b-140">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7777b-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
