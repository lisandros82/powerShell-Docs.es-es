---
title: Cómo agregar sintaxis a un tema de ayuda de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361214"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="6cdf9-102">Cómo agregar una sintaxis a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6cdf9-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="6cdf9-103">Antes de empezar a codificar el XML para el diagrama de sintaxis en el archivo de ayuda del cmdlet, lea esta sección para obtener una visión clara del tipo de datos que necesita proporcionar, como los atributos de parámetro y cómo se muestran los datos en el diagrama de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="6cdf9-104">Atributos de parámetro</span><span class="sxs-lookup"><span data-stu-id="6cdf9-104">Parameter Attributes</span></span>

- <span data-ttu-id="6cdf9-105">Requerido</span><span class="sxs-lookup"><span data-stu-id="6cdf9-105">Required</span></span>

  - <span data-ttu-id="6cdf9-106">Si es true, el parámetro debe aparecer en todos los comandos que usan el conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="6cdf9-107">Si es false, el parámetro es opcional en todos los comandos que usan el conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="6cdf9-108">Posición</span><span class="sxs-lookup"><span data-stu-id="6cdf9-108">Position</span></span>

  - <span data-ttu-id="6cdf9-109">Si se denomina, el nombre del parámetro es obligatorio.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="6cdf9-110">Si es posicional, el nombre del parámetro es opcional.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="6cdf9-111">Cuando se omite, el valor del parámetro debe estar en la posición especificada en el comando.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="6cdf9-112">Por ejemplo, si el valor es position = "1", el valor del parámetro debe ser el primero o el único valor de parámetro sin nombre del comando.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="6cdf9-113">Entrada de canalización</span><span class="sxs-lookup"><span data-stu-id="6cdf9-113">Pipeline Input</span></span>

  - <span data-ttu-id="6cdf9-114">Si es true (ByValue), puede canalizar la entrada al parámetro.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="6cdf9-115">La entrada está asociada a ("enlazada a") el parámetro aunque el nombre de la propiedad y el tipo de objeto no coincidan con el tipo esperado.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="6cdf9-116">¿Windows PowerShell? los componentes de enlace de parámetros intentan convertir la entrada al tipo correcto y no se puede realizar el comando solo cuando no se puede convertir el tipo.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="6cdf9-117">Solo se puede asociar un parámetro de un conjunto de parámetros por valor.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="6cdf9-118">Si es true (ByPropertyName), puede canalizar la entrada al parámetro.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="6cdf9-119">Sin embargo, la entrada se asocia al parámetro solo cuando el nombre del parámetro coincide con el nombre de una propiedad del objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="6cdf9-120">Por ejemplo, si el nombre del parámetro es `Path`, los objetos que se canalizan al cmdlet se asocian a ese parámetro solo cuando el objeto tiene una propiedad denominada path.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="6cdf9-121">Si es true (ByValue, ByPropertyName), se puede canalizar la entrada al parámetro por nombre de propiedad o por valor.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="6cdf9-122">Solo se puede asociar un parámetro de un conjunto de parámetros por valor.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="6cdf9-123">Si es false, no se puede canalizar la entrada a este parámetro.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="6cdf9-124">Comodines</span><span class="sxs-lookup"><span data-stu-id="6cdf9-124">Globbing</span></span>

  - <span data-ttu-id="6cdf9-125">Si es true, el texto que el usuario escribe para el valor del parámetro puede incluir caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="6cdf9-126">Si es false, el texto que el usuario escribe para el valor del parámetro no puede incluir caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="6cdf9-127">Atributos de valor de parámetro</span><span class="sxs-lookup"><span data-stu-id="6cdf9-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="6cdf9-128">Requerido</span><span class="sxs-lookup"><span data-stu-id="6cdf9-128">Required</span></span>

  - <span data-ttu-id="6cdf9-129">Si es true, se debe usar el valor especificado siempre que se use el parámetro en un comando.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="6cdf9-130">Si es false, el valor del parámetro es opcional.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="6cdf9-131">Normalmente, un valor es opcional solo cuando es uno de varios valores válidos para un parámetro, como en un tipo enumerado.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="6cdf9-132">El atributo required de un valor de parámetro es distinto del atributo required de un parámetro.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="6cdf9-133">El atributo required de un parámetro indica si se debe incluir el parámetro (y su valor) al invocar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="6cdf9-134">En cambio, el atributo required de un valor de parámetro solo se usa cuando el parámetro se incluye en el comando.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="6cdf9-135">Indica si se debe usar ese valor concreto con el parámetro.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="6cdf9-136">Normalmente, los valores de parámetro que son marcadores de posición son obligatorios y los valores de parámetro que son literales no son necesarios, ya que se trata de uno de varios valores que se pueden usar con el parámetro.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="6cdf9-137">Recopilar información de sintaxis</span><span class="sxs-lookup"><span data-stu-id="6cdf9-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="6cdf9-138">Comience con el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="6cdf9-139">Enumera todos los parámetros del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="6cdf9-140">Escriba un guion (también conocido como "guion" o "signo menos" (ASCII 45) antes de cada nombre de parámetro.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="6cdf9-141">Separe los parámetros en conjuntos de parámetros (algunos cmdlets pueden tener solo un conjunto de parámetros).</span><span class="sxs-lookup"><span data-stu-id="6cdf9-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="6cdf9-142">En este ejemplo, el cmdlet Get-Tech tiene dos conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="6cdf9-143">Inicie cada conjunto de parámetros con el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="6cdf9-144">Enumere primero el conjunto de parámetros predeterminado.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-144">List the default parameter set first.</span></span> <span data-ttu-id="6cdf9-145">La clase de cmdlet especifica el parámetro predeterminado.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="6cdf9-146">Para cada conjunto de parámetros, enumere primero su parámetro único, a menos que haya parámetros posicionales que deban aparecer en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="6cdf9-147">En el ejemplo anterior, los parámetros Name e ID son únicos para los dos conjuntos de parámetros (cada conjunto de parámetros debe tener un parámetro que sea único para ese conjunto de parámetros).</span><span class="sxs-lookup"><span data-stu-id="6cdf9-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="6cdf9-148">Esto facilita a los usuarios identificar qué parámetro deben proporcionar para el conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="6cdf9-149">Enumere los parámetros en el orden en que deberían aparecer en el comando.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="6cdf9-150">Si el orden no importa, enumere los parámetros relacionados o Enumere primero los parámetros que se usan con más frecuencia.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="6cdf9-151">Asegúrese de enumerar los parámetros WhatIf y CONFIRM si el cmdlet admite ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="6cdf9-152">No enumere los parámetros comunes (como verbose, Debug y ErrorAction) en el diagrama de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="6cdf9-153">El cmdlet `Get-Help` agrega esa información cuando se muestra el tema de ayuda.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="6cdf9-154">Agregue los valores de parámetro.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-154">Add the parameter values.</span></span> <span data-ttu-id="6cdf9-155">En Windows PowerShell, los valores de parámetro se representan mediante su tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="6cdf9-156">Sin embargo, el nombre de tipo se puede abreviar como, por ejemplo, "String" para System. String.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="6cdf9-157">Abrevie los tipos siempre que su significado sea claro, como "String" para System. String e "int" para System. Int32.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="6cdf9-158">Enumera todos los valores de enumeraciones, como el parámetro-type en el ejemplo anterior, que se puede establecer en "Basic" o "Advanced".</span><span class="sxs-lookup"><span data-stu-id="6cdf9-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="6cdf9-159">Los parámetros de modificador, como-List en el ejemplo anterior, no tienen valores.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="6cdf9-160">Agregue corchetes angulares a los valores de los parámetros que son marcadores de posición, en comparación con los valores de parámetro que son literales.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="6cdf9-161">Incluya los parámetros opcionales y sus valores entre corchetes.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="6cdf9-162">Incluya los nombres de parámetros opcionales (para los parámetros posicionales) entre corchetes.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="6cdf9-163">El nombre de los parámetros que son posicionales, como el parámetro name en el ejemplo siguiente, no tienen que incluirse en el comando.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="6cdf9-164">Si un valor de parámetro puede contener varios valores, como una lista de nombres en el parámetro name, agregue un par de corchetes directamente después del valor del parámetro.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="6cdf9-165">Si el usuario puede elegir entre parámetros o valores de parámetros, como el parámetro de tipo, incluya las opciones entre llaves y sepárelas con el símbolo OR exclusivo (;).</span><span class="sxs-lookup"><span data-stu-id="6cdf9-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="6cdf9-166">Si el valor del parámetro debe usar un formato específico, como comillas o paréntesis, muestre el formato en la sintaxis.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="6cdf9-167">Codificar el XML del diagrama de sintaxis</span><span class="sxs-lookup"><span data-stu-id="6cdf9-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="6cdf9-168">El nodo de sintaxis del XML comienza inmediatamente después del nodo de descripción, que finaliza con la etiqueta \</maml: Description >.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="6cdf9-169">Para obtener información sobre cómo recopilar los datos que se usan en el diagrama de sintaxis, vea [recopilar información de sintaxis](#gathering-syntax-information).</span><span class="sxs-lookup"><span data-stu-id="6cdf9-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="6cdf9-170">Agregar un nodo de sintaxis</span><span class="sxs-lookup"><span data-stu-id="6cdf9-170">Adding a Syntax Node</span></span>

<span data-ttu-id="6cdf9-171">El diagrama de sintaxis que se muestra en el tema de ayuda del cmdlet se genera a partir de los datos del nodo sintaxis del XML.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="6cdf9-172">El nodo de sintaxis se incluye en un par si \<comando: sintaxis > etiquetas.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="6cdf9-173">Con cada conjunto de parámetros del cmdlet incluido en un par de \<comando: syntaxitem > etiquetas.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="6cdf9-174">No hay ningún límite en el número de \<comando: syntaxitem > etiquetas que puede Agregar.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="6cdf9-175">En el ejemplo siguiente se muestra un nodo de sintaxis que tiene nodos de elemento de sintaxis para dos conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="6cdf9-176">Agregar el nombre del cmdlet a los datos del conjunto de parámetros</span><span class="sxs-lookup"><span data-stu-id="6cdf9-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="6cdf9-177">Cada conjunto de parámetros del cmdlet se especifica en un nodo de elemento de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="6cdf9-178">Cada nodo de elemento de sintaxis comienza con un par de \<maml: nombre > etiquetas que incluyen el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="6cdf9-179">En el ejemplo siguiente se incluye un nodo de sintaxis que tiene nodos de elemento de sintaxis para dos conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a><span data-ttu-id="6cdf9-180">Agregar parámetros</span><span class="sxs-lookup"><span data-stu-id="6cdf9-180">Adding Parameters</span></span>

<span data-ttu-id="6cdf9-181">Cada parámetro agregado al nodo elemento de sintaxis se especifica dentro de un par de \<comando: Parameter > Tags.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="6cdf9-182">Necesita un par de \<comando: Parameter > Etiquetas para cada parámetro incluido en el conjunto de parámetros, con la excepción de los parámetros comunes proporcionados por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="6cdf9-183">Los atributos de la etiqueta de apertura \<comando: parámetro > determinan cómo aparece el parámetro en el diagrama de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="6cdf9-184">Para obtener información sobre los atributos de parámetro, vea [atributos de parámetro](#parameter-attributes).</span><span class="sxs-lookup"><span data-stu-id="6cdf9-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="6cdf9-185">La etiqueta del comando \<: Parameter > admite un elemento secundario \<maml: Description > cuyo contenido nunca se muestra.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="6cdf9-186">Las descripciones de los parámetros se especifican en el nodo de parámetro de XML.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="6cdf9-187">Para evitar incoherencias entre la información del elemento de sintaxis Bodes y el nodo de parámetro, omita (\<maml: Description > o déjelo vacío.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="6cdf9-188">En el ejemplo siguiente se incluye un nodo elemento de sintaxis para un conjunto de parámetros con dos parámetros.</span><span class="sxs-lookup"><span data-stu-id="6cdf9-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
