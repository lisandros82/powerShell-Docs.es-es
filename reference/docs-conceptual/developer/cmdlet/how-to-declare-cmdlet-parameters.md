---
title: Cómo declarar parámetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365684"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="1ac6f-102">Cómo declarar los parámetros del cmdlet</span><span class="sxs-lookup"><span data-stu-id="1ac6f-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="1ac6f-103">En estos ejemplos se muestra cómo declarar parámetros con nombre, posicionales, obligatorios, opcionales y modificadores.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="1ac6f-104">En estos ejemplos también se muestra cómo definir un alias de parámetro.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="1ac6f-105">Cómo declarar un parámetro con nombre</span><span class="sxs-lookup"><span data-stu-id="1ac6f-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="1ac6f-106">Defina una propiedad pública como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1ac6f-107">Al agregar el atributo Parameter, omita la palabra clave `Position` del atributo.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="1ac6f-108">Para obtener más información sobre el atributo Parameter, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1ac6f-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="1ac6f-109">Cómo declarar un parámetro posicional</span><span class="sxs-lookup"><span data-stu-id="1ac6f-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="1ac6f-110">Defina una propiedad pública como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1ac6f-111">Al agregar el atributo Parameter, establezca la palabra clave `Position` en la posición del argumento.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="1ac6f-112">Un valor de 0 indica la primera posición.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="1ac6f-113">Para obtener más información sobre el atributo Parameter, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1ac6f-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="1ac6f-114">Cómo declarar un parámetro obligatorio</span><span class="sxs-lookup"><span data-stu-id="1ac6f-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="1ac6f-115">Defina una propiedad pública como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1ac6f-116">Al agregar el atributo Parameter, establezca la palabra clave `Mandatory` en `true`.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="1ac6f-117">Para obtener más información sobre el atributo Parameter, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1ac6f-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="1ac6f-118">Cómo declarar un parámetro opcional</span><span class="sxs-lookup"><span data-stu-id="1ac6f-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="1ac6f-119">Defina una propiedad pública como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1ac6f-120">Al agregar el atributo Parameter, omita la palabra clave `Mandatory`.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="1ac6f-121">Cómo declarar un parámetro de modificador</span><span class="sxs-lookup"><span data-stu-id="1ac6f-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="1ac6f-122">Defina una propiedad pública como Type [System. Management. Automation. parámetrodemodificador](/dotnet/api/System.Management.Automation.SwitchParameter)y, a continuación, declare el atributo Parameter.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="1ac6f-123">Para obtener más información sobre el atributo Parameter, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1ac6f-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="1ac6f-124">Cómo declarar un parámetro con alias</span><span class="sxs-lookup"><span data-stu-id="1ac6f-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="1ac6f-125">Defina una propiedad pública como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1ac6f-126">Agregue un atributo de alias que Enumere los alias del parámetro.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="1ac6f-127">En este ejemplo, se definen tres alias para el mismo parámetro.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="1ac6f-128">El primer alias proporciona un acceso directo.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="1ac6f-129">El segundo y el tercer alias proporcionan nombres que se pueden utilizar para distintos escenarios.</span><span class="sxs-lookup"><span data-stu-id="1ac6f-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="1ac6f-130">Para obtener más información sobre el atributo alias, vea [alias Attribute declaration](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1ac6f-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ac6f-131">Véase también</span><span class="sxs-lookup"><span data-stu-id="1ac6f-131">See Also</span></span>

[<span data-ttu-id="1ac6f-132">System. Management. Automation. Parámetrodemodificador</span><span class="sxs-lookup"><span data-stu-id="1ac6f-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="1ac6f-133">Declaración de atributo de parámetro</span><span class="sxs-lookup"><span data-stu-id="1ac6f-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="1ac6f-134">Declaración de atributo de alias</span><span class="sxs-lookup"><span data-stu-id="1ac6f-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="1ac6f-135">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ac6f-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
