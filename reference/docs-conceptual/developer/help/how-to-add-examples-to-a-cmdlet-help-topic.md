---
title: Cómo agregar ejemplos a un tema de ayuda de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368114"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="019ad-102">Cómo agregar ejemplos a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="019ad-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="019ad-103">Aspectos que se deben conocer sobre los ejemplos de la ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="019ad-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="019ad-104">Enumera todos los nombres de parámetro del comando, incluso cuando los nombres de parámetro son opcionales.</span><span class="sxs-lookup"><span data-stu-id="019ad-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="019ad-105">Esto ayuda al usuario a interpretar el comando fácilmente.</span><span class="sxs-lookup"><span data-stu-id="019ad-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="019ad-106">Evite los alias y los nombres de parámetros parciales, aunque funcionan en Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="019ad-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="019ad-107">En la descripción del ejemplo, explique el razonamiento de la construcción del comando.</span><span class="sxs-lookup"><span data-stu-id="019ad-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="019ad-108">Explique por qué se eligen determinados parámetros y valores, y cómo se usan las variables.</span><span class="sxs-lookup"><span data-stu-id="019ad-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="019ad-109">Si el comando usa expresiones, explíqueles en detalle.</span><span class="sxs-lookup"><span data-stu-id="019ad-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="019ad-110">Si el comando usa las propiedades y los métodos de los objetos, especialmente las propiedades que no aparecen en la pantalla predeterminada, use el ejemplo como una oportunidad para informar al usuario sobre el objeto.</span><span class="sxs-lookup"><span data-stu-id="019ad-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="019ad-111">Vistas de ayuda que muestran ejemplos</span><span class="sxs-lookup"><span data-stu-id="019ad-111">Help Views that Display Examples</span></span>

<span data-ttu-id="019ad-112">Los ejemplos solo aparecen en las vistas detalladas y completas de la ayuda de los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="019ad-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="019ad-113">Agregar un nodo examples</span><span class="sxs-lookup"><span data-stu-id="019ad-113">Adding an Examples Node</span></span>

<span data-ttu-id="019ad-114">El siguiente XML muestra cómo agregar un nodo examples que contiene un solo nodo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="019ad-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="019ad-115">Agregue nodos de ejemplo adicionales para cada uno de los ejemplos que desee incluir en el tema.</span><span class="sxs-lookup"><span data-stu-id="019ad-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="019ad-116">Agregar un título de ejemplo</span><span class="sxs-lookup"><span data-stu-id="019ad-116">Adding an Example Title</span></span>

<span data-ttu-id="019ad-117">En el código XML siguiente se muestra cómo agregar un título para el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="019ad-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="019ad-118">El título se usa para establecer el ejemplo, además de otros ejemplos.</span><span class="sxs-lookup"><span data-stu-id="019ad-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="019ad-119">Windows PowerShell® usa un encabezado estándar que incluye un número de ejemplo secuencial.</span><span class="sxs-lookup"><span data-stu-id="019ad-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="019ad-120">Agregar caracteres anteriores</span><span class="sxs-lookup"><span data-stu-id="019ad-120">Adding Preceding Characters</span></span>

<span data-ttu-id="019ad-121">El siguiente XML muestra cómo agregar caracteres, como el símbolo del sistema de Windows PowerShell, que se muestran inmediatamente antes del comando de ejemplo (sin espacios intermedios).</span><span class="sxs-lookup"><span data-stu-id="019ad-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="019ad-122">Windows PowerShell® usa el símbolo del sistema de Windows PowerShell: C:\PS >.</span><span class="sxs-lookup"><span data-stu-id="019ad-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="019ad-123">Agregar el comando</span><span class="sxs-lookup"><span data-stu-id="019ad-123">Adding the Command</span></span>

<span data-ttu-id="019ad-124">El siguiente XML muestra cómo agregar el comando real del ejemplo.</span><span class="sxs-lookup"><span data-stu-id="019ad-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="019ad-125">Al agregar el comando, escriba el nombre completo (no usar alias) de los cmdlets y parámetros.</span><span class="sxs-lookup"><span data-stu-id="019ad-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="019ad-126">Además, use caracteres en minúsculas siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="019ad-126">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="019ad-127">Agregar una descripción</span><span class="sxs-lookup"><span data-stu-id="019ad-127">Adding a Description</span></span>

<span data-ttu-id="019ad-128">El siguiente XML muestra cómo agregar una descripción para el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="019ad-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="019ad-129">Windows PowerShell® usa un único conjunto de etiquetas \<maml: para > para la descripción, aunque se pueden usar varias etiquetas \<maml: para >.</span><span class="sxs-lookup"><span data-stu-id="019ad-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="019ad-130">Agregar salida de ejemplo</span><span class="sxs-lookup"><span data-stu-id="019ad-130">Adding Example Output</span></span>

<span data-ttu-id="019ad-131">En el código XML siguiente se muestra cómo agregar el resultado del comando.</span><span class="sxs-lookup"><span data-stu-id="019ad-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="019ad-132">La información de los resultados del comando es opcional, pero en algunos casos resulta útil mostrar el efecto de usar parámetros específicos.</span><span class="sxs-lookup"><span data-stu-id="019ad-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="019ad-133">Windows PowerShell® usa dos conjuntos de etiquetas \<maml: para > para separar el resultado del comando del comando.</span><span class="sxs-lookup"><span data-stu-id="019ad-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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