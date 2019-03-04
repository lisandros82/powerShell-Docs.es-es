---
title: Cómo declarar los parámetros de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: d6613889ebd2ba139ce0b3de1b8d24e4aec37d2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861401"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="999d3-102">Cómo declarar los parámetros del cmdlet</span><span class="sxs-lookup"><span data-stu-id="999d3-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="999d3-103">Estos ejemplos muestran cómo se declara con nombre, posición, requerido, opcional y parámetros de modificador.</span><span class="sxs-lookup"><span data-stu-id="999d3-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="999d3-104">Estos ejemplos también muestra cómo definir un alias de parámetro.</span><span class="sxs-lookup"><span data-stu-id="999d3-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="999d3-105">Cómo declarar un parámetro con nombre</span><span class="sxs-lookup"><span data-stu-id="999d3-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="999d3-106">Definir una propiedad pública como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="999d3-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="999d3-107">Al agregar el atributo Parameter, omita el `Position` palabra clave del atributo.</span><span class="sxs-lookup"><span data-stu-id="999d3-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="999d3-108">Para obtener más información sobre el atributo de parámetro, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="999d3-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="999d3-109">Cómo declarar un parámetro posicional</span><span class="sxs-lookup"><span data-stu-id="999d3-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="999d3-110">Definir una propiedad pública como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="999d3-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="999d3-111">Cuando agregue el atributo Parameter, establezca el `Position` palabra clave a la posición del argumento.</span><span class="sxs-lookup"><span data-stu-id="999d3-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="999d3-112">Un valor de 0 indica que la primera posición.</span><span class="sxs-lookup"><span data-stu-id="999d3-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="999d3-113">Para obtener más información sobre el atributo de parámetro, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="999d3-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="999d3-114">Cómo declarar un parámetro obligatorio</span><span class="sxs-lookup"><span data-stu-id="999d3-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="999d3-115">Definir una propiedad pública como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="999d3-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="999d3-116">Cuando agregue el atributo Parameter, establezca el `Mandatory` palabra clave para `true`.</span><span class="sxs-lookup"><span data-stu-id="999d3-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="999d3-117">Para obtener más información sobre el atributo de parámetro, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="999d3-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="999d3-118">Cómo declarar un parámetro opcional</span><span class="sxs-lookup"><span data-stu-id="999d3-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="999d3-119">Definir una propiedad pública como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="999d3-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="999d3-120">Al agregar el atributo Parameter, omita el `Mandatory` palabra clave.</span><span class="sxs-lookup"><span data-stu-id="999d3-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="999d3-121">Cómo declarar un parámetro de modificador</span><span class="sxs-lookup"><span data-stu-id="999d3-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="999d3-122">Defina una propiedad pública como tipo [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)y, a continuación, declare el atributo de parámetro.</span><span class="sxs-lookup"><span data-stu-id="999d3-122">Define a public property as type [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="999d3-123">Para obtener más información sobre el atributo de parámetro, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="999d3-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="999d3-124">Cómo declarar un parámetro con alias</span><span class="sxs-lookup"><span data-stu-id="999d3-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="999d3-125">Definir una propiedad pública como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="999d3-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="999d3-126">Agregue un Alias (atributo) que se enumera los alias para el parámetro.</span><span class="sxs-lookup"><span data-stu-id="999d3-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="999d3-127">En este ejemplo, se definen tres alias para el mismo parámetro.</span><span class="sxs-lookup"><span data-stu-id="999d3-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="999d3-128">El primer alias proporciona un acceso directo.</span><span class="sxs-lookup"><span data-stu-id="999d3-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="999d3-129">Los alias de la segundo y terceros proporcionan nombres que se puede usar para diferentes escenarios.</span><span class="sxs-lookup"><span data-stu-id="999d3-129">The second and third aliases provide names you can use for different scenarios.</span></span>

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="999d3-130">Para obtener más información sobre el atributo de Alias, vea [la declaración de atributo Alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="999d3-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="999d3-131">Véase también</span><span class="sxs-lookup"><span data-stu-id="999d3-131">See Also</span></span>

[<span data-ttu-id="999d3-132">System.Management.Automation.Switchparameter</span><span class="sxs-lookup"><span data-stu-id="999d3-132">System.Management.Automation.Switchparameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="999d3-133">Declaración de atributo de parámetro</span><span class="sxs-lookup"><span data-stu-id="999d3-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="999d3-134">Declaración de atributo de alias</span><span class="sxs-lookup"><span data-stu-id="999d3-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="999d3-135">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="999d3-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)