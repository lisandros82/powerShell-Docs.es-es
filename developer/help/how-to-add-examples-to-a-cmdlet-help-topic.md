---
title: Cómo agregar ejemplos para un tema de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 5e8d1df6b423bfd2cd6b0a64a8875dea9c3fb4ef
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857321"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="f644f-102">Cómo agregar ejemplos a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="f644f-102">How to Add Examples to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="f644f-103">Cosas que saber acerca de los ejemplos en la Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f644f-103">Things to Know about Examples in Cmdlet Help</span></span>](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [<span data-ttu-id="f644f-104">Las vistas que se muestran ejemplos de ayuda</span><span class="sxs-lookup"><span data-stu-id="f644f-104">Help Views that Display Examples</span></span>](#Help-Views-that-Display-Examples)

- [<span data-ttu-id="f644f-105">Agregar un nodo de ejemplos</span><span class="sxs-lookup"><span data-stu-id="f644f-105">Adding an Examples Node</span></span>](#Adding-an-Examples-Node)

- [<span data-ttu-id="f644f-106">Agregar delante los caracteres adicionales.</span><span class="sxs-lookup"><span data-stu-id="f644f-106">Adding Preceding Characters</span></span>](#Adding-Preceding-Characters)

- [<span data-ttu-id="f644f-107">Agrega el comando</span><span class="sxs-lookup"><span data-stu-id="f644f-107">Adding the Command</span></span>](#Adding-the-Command)

- [<span data-ttu-id="f644f-108">Agregar una descripción</span><span class="sxs-lookup"><span data-stu-id="f644f-108">Adding a Description</span></span>](#Adding-a-Description)

- [<span data-ttu-id="f644f-109">Adición de salida de ejemplo</span><span class="sxs-lookup"><span data-stu-id="f644f-109">Adding Example Output</span></span>](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="f644f-110">Cosas que saber acerca de los ejemplos en la Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f644f-110">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="f644f-111">Enumera todos los nombres de parámetro en el comando, incluso cuando los nombres de parámetro son opcionales.</span><span class="sxs-lookup"><span data-stu-id="f644f-111">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="f644f-112">Esto ayuda al usuario a interpretar el comando fácilmente.</span><span class="sxs-lookup"><span data-stu-id="f644f-112">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="f644f-113">Evite los alias y nombres de parámetros parciales, incluso aunque funcionan en Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="f644f-113">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="f644f-114">En la descripción del ejemplo, explique el racional para la construcción del comando.</span><span class="sxs-lookup"><span data-stu-id="f644f-114">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="f644f-115">Explique por qué eligió determinados parámetros y valores, y cómo usar variables.</span><span class="sxs-lookup"><span data-stu-id="f644f-115">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="f644f-116">Si el comando usa las expresiones, explicaremos con detalle.</span><span class="sxs-lookup"><span data-stu-id="f644f-116">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="f644f-117">Si el comando usa las propiedades y métodos de objetos, especialmente las propiedades que no aparecen en la pantalla predeterminada, use el ejemplo como una oportunidad de indicar al usuario sobre el objeto.</span><span class="sxs-lookup"><span data-stu-id="f644f-117">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="f644f-118">Las vistas que se muestran ejemplos de ayuda</span><span class="sxs-lookup"><span data-stu-id="f644f-118">Help Views that Display Examples</span></span>

<span data-ttu-id="f644f-119">Ejemplos solo aparecen en las vistas completa y detallada de la Ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f644f-119">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="f644f-120">Agregar un nodo de ejemplos</span><span class="sxs-lookup"><span data-stu-id="f644f-120">Adding an Examples Node</span></span>

<span data-ttu-id="f644f-121">El siguiente XML muestra cómo agregar un nodo de ejemplos que contiene un único nodo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f644f-121">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="f644f-122">Agregar nodos de ejemplo adicional para cada ejemplos que van a incluir en el tema.</span><span class="sxs-lookup"><span data-stu-id="f644f-122">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="f644f-123">Agregar un título de ejemplo</span><span class="sxs-lookup"><span data-stu-id="f644f-123">Adding an Example Title</span></span>

<span data-ttu-id="f644f-124">El siguiente XML muestra cómo agregar un título para el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f644f-124">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="f644f-125">El título se usa para establecer el ejemplo además de otros ejemplos.</span><span class="sxs-lookup"><span data-stu-id="f644f-125">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="f644f-126">Windows PowerShell® utiliza un encabezado estándar que incluye una serie secuencial de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f644f-126">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="f644f-127">Agregar delante los caracteres adicionales.</span><span class="sxs-lookup"><span data-stu-id="f644f-127">Adding Preceding Characters</span></span>

<span data-ttu-id="f644f-128">El siguiente XML muestra cómo agregar caracteres, como el símbolo del sistema de Windows PowerShell, que se muestran inmediatamente antes del comando de ejemplo (sin espacios intermedios).</span><span class="sxs-lookup"><span data-stu-id="f644f-128">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="f644f-129">Windows PowerShell® usa el símbolo del sistema de Windows PowerShell: C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="f644f-129">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a><span data-ttu-id="f644f-130">Agrega el comando</span><span class="sxs-lookup"><span data-stu-id="f644f-130">Adding the Command</span></span>

<span data-ttu-id="f644f-131">El siguiente XML muestra cómo agregar el comando real del ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f644f-131">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="f644f-132">Al agregar el comando, escriba el nombre completo (no utilice alias) de los cmdlets y parámetros.</span><span class="sxs-lookup"><span data-stu-id="f644f-132">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="f644f-133">Además, usar caracteres en minúsculas siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="f644f-133">Also, use lowercase characters whenever possible.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a><span data-ttu-id="f644f-134">Agregar una descripción</span><span class="sxs-lookup"><span data-stu-id="f644f-134">Adding a Description</span></span>

<span data-ttu-id="f644f-135">El siguiente XML muestra cómo agregar una descripción para el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f644f-135">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="f644f-136">Windows PowerShell® utiliza un conjunto único de \<maml: para > etiquetas de la descripción, aunque varios \<maml: para > etiquetas se pueden usar.</span><span class="sxs-lookup"><span data-stu-id="f644f-136">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a><span data-ttu-id="f644f-137">Adición de salida de ejemplo</span><span class="sxs-lookup"><span data-stu-id="f644f-137">Adding Example Output</span></span>

<span data-ttu-id="f644f-138">El siguiente XML muestra cómo agregar la salida del comando.</span><span class="sxs-lookup"><span data-stu-id="f644f-138">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="f644f-139">La información de los resultados del comando es opcional, pero en algunos casos es útil mostrar el efecto del uso de parámetros específicos.</span><span class="sxs-lookup"><span data-stu-id="f644f-139">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="f644f-140">Windows PowerShell® usa dos conjuntos de espacio en blanco \<maml: para > etiquetas para separar la salida del comando del comando.</span><span class="sxs-lookup"><span data-stu-id="f644f-140">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```