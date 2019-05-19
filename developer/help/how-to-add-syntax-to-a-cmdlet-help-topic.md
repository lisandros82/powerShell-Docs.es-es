---
title: Cómo agregar una sintaxis para un tema de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855130"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="6d806-102">Cómo agregar una sintaxis a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6d806-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="6d806-103">Antes de empezar a codificar el XML para el diagrama de sintaxis en el archivo de Ayuda de cmdlet, lea esta sección para obtener una visión clara del tipo de datos que necesita para proporcionar, como los atributos de parámetro y cómo esos datos se muestran en el diagrama de sintaxis...</span><span class="sxs-lookup"><span data-stu-id="6d806-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="6d806-104">Atributos de parámetro</span><span class="sxs-lookup"><span data-stu-id="6d806-104">Parameter Attributes</span></span>

- <span data-ttu-id="6d806-105">Requerido</span><span class="sxs-lookup"><span data-stu-id="6d806-105">Required</span></span>

  - <span data-ttu-id="6d806-106">Si es true, el parámetro debe aparecer en todos los comandos que utilizan el conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6d806-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="6d806-107">Si es false, el parámetro es opcional en todos los comandos que utilizan el conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6d806-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="6d806-108">Posición</span><span class="sxs-lookup"><span data-stu-id="6d806-108">Position</span></span>

  - <span data-ttu-id="6d806-109">Si el nombre, el nombre de parámetro es obligatorio.</span><span class="sxs-lookup"><span data-stu-id="6d806-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="6d806-110">Si es posicional, el nombre del parámetro es opcional.</span><span class="sxs-lookup"><span data-stu-id="6d806-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="6d806-111">Cuando se omite, el valor del parámetro debe estar en la posición especificada en el comando.</span><span class="sxs-lookup"><span data-stu-id="6d806-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="6d806-112">Por ejemplo, si el valor es la posición = "1", el valor del parámetro debe ser el primer o el único valor de parámetro en el comando sin nombre.</span><span class="sxs-lookup"><span data-stu-id="6d806-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="6d806-113">Entrada de la canalización</span><span class="sxs-lookup"><span data-stu-id="6d806-113">Pipeline Input</span></span>

  - <span data-ttu-id="6d806-114">Si es true (ByValue), puede canalizar la entrada para el parámetro.</span><span class="sxs-lookup"><span data-stu-id="6d806-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="6d806-115">La entrada se asocia con ("enlazado a") el parámetro incluso si el nombre de propiedad y el tipo de objeto no coincide con el tipo esperado.</span><span class="sxs-lookup"><span data-stu-id="6d806-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="6d806-116">¿Windows PowerShell? componentes de enlace de parámetro intentan convertir la entrada al tipo correcto y se producirá un error en el comando solo cuando no se puede convertir el tipo.</span><span class="sxs-lookup"><span data-stu-id="6d806-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="6d806-117">Puede asociar solo un parámetro en un conjunto de parámetros por valor.</span><span class="sxs-lookup"><span data-stu-id="6d806-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="6d806-118">Si es true (ByPropertyName), puede canalizar la entrada para el parámetro.</span><span class="sxs-lookup"><span data-stu-id="6d806-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="6d806-119">Sin embargo, la entrada está asociada con el parámetro solo cuando el nombre del parámetro coincide con el nombre de una propiedad del objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="6d806-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="6d806-120">Por ejemplo, si es el nombre del parámetro `Path`, objetos que canaliza al cmdlet están asociados con ese parámetro solo cuando el objeto tiene una propiedad con el nombre de ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="6d806-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="6d806-121">Si true (ByValue, ByPropertyName), puede canalizar la entrada para el parámetro de nombre de propiedad o valor.</span><span class="sxs-lookup"><span data-stu-id="6d806-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="6d806-122">Puede asociar solo un parámetro en un conjunto de parámetros por valor.</span><span class="sxs-lookup"><span data-stu-id="6d806-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="6d806-123">Si es false, no se puede canalizar la entrada a este parámetro.</span><span class="sxs-lookup"><span data-stu-id="6d806-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="6d806-124">Uso de comodines</span><span class="sxs-lookup"><span data-stu-id="6d806-124">Globbing</span></span>

  - <span data-ttu-id="6d806-125">Si es true, el texto que el usuario escribe el valor de parámetro puede incluir caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="6d806-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="6d806-126">Si es false, el texto que el usuario escribe el valor de parámetro no puede incluir caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="6d806-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="6d806-127">Atributos de valor de parámetro</span><span class="sxs-lookup"><span data-stu-id="6d806-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="6d806-128">Requerido</span><span class="sxs-lookup"><span data-stu-id="6d806-128">Required</span></span>

  - <span data-ttu-id="6d806-129">Si es true, el valor especificado debe usarse cada vez que usa el parámetro de un comando.</span><span class="sxs-lookup"><span data-stu-id="6d806-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="6d806-130">Si es false, el valor del parámetro es opcional.</span><span class="sxs-lookup"><span data-stu-id="6d806-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="6d806-131">Normalmente, un valor es opcional sólo cuando se encuentra uno de varios valores válidos para un parámetro, como en un tipo enumerado.</span><span class="sxs-lookup"><span data-stu-id="6d806-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="6d806-132">El atributo necesario del valor de parámetro es distinto del atributo de un parámetro necesario.</span><span class="sxs-lookup"><span data-stu-id="6d806-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="6d806-133">El atributo required de un parámetro indica si el parámetro (y su valor) deben incluirse al invocar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6d806-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="6d806-134">En cambio, el atributo necesario del valor de parámetro se usa solo cuando el parámetro se incluye en el comando.</span><span class="sxs-lookup"><span data-stu-id="6d806-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="6d806-135">Indica si se debe usar ese valor en particular con el parámetro.</span><span class="sxs-lookup"><span data-stu-id="6d806-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="6d806-136">Normalmente, los valores de parámetros que son marcadores de posición son necesarios y valores de parámetros que son literales no son necesarios, porque son uno de varios valores que se pueden usar con el parámetro.</span><span class="sxs-lookup"><span data-stu-id="6d806-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="6d806-137">Recopilando información sobre la sintaxis</span><span class="sxs-lookup"><span data-stu-id="6d806-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="6d806-138">Comience con el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6d806-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="6d806-139">Enumerar todos los parámetros del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6d806-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="6d806-140">Escriba un guión (también conocido como "dash" o "signo" (ASCII 45) delante de cada nombre de parámetro.</span><span class="sxs-lookup"><span data-stu-id="6d806-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="6d806-141">Separe los parámetros en conjuntos de parámetros (algunos cmdlets puede tener solo un parámetro establecido).</span><span class="sxs-lookup"><span data-stu-id="6d806-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="6d806-142">En este ejemplo, la tecnología Get cmdlet tiene dos conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6d806-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="6d806-143">Iniciar cada parámetro establecido con el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6d806-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="6d806-144">Se enumeran el parámetro predeterminado configurado en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="6d806-144">List the default parameter set first.</span></span> <span data-ttu-id="6d806-145">El parámetro predeterminado especificado por la clase del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6d806-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="6d806-146">Para cada conjunto de parámetros, enumere su único parámetro en primer lugar, a menos que existan los parámetros posicionales deben aparecer en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="6d806-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="6d806-147">En el ejemplo anterior, los parámetros de nombre e identificador son parámetros únicos para los dos conjuntos de parámetros (cada conjunto de parámetros debe tener un parámetro que es único para ese conjunto de parámetros).</span><span class="sxs-lookup"><span data-stu-id="6d806-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="6d806-148">Esto facilita a los usuarios a identificar qué parámetro debe proporcionar para el parámetro establecido.</span><span class="sxs-lookup"><span data-stu-id="6d806-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="6d806-149">Enumerar los parámetros en el orden en que aparecen en el comando.</span><span class="sxs-lookup"><span data-stu-id="6d806-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="6d806-150">Si el orden no importa, lista de parámetros relacionados entre sí o, en primer lugar se muestran los parámetros utilizados con más frecuencia.</span><span class="sxs-lookup"><span data-stu-id="6d806-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="6d806-151">No olvide si el cmdlet admite ShouldProcess, se muestran los parámetros WhatIf y Confirm.</span><span class="sxs-lookup"><span data-stu-id="6d806-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="6d806-152">No se enumeran los parámetros comunes (por ejemplo, Verbose, Debug y ErrorAction) en el diagrama de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="6d806-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="6d806-153">El `Get-Help` cmdlet agrega esa información cuando se muestre el tema de ayuda.</span><span class="sxs-lookup"><span data-stu-id="6d806-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="6d806-154">Agregue los valores de parámetro.</span><span class="sxs-lookup"><span data-stu-id="6d806-154">Add the parameter values.</span></span> <span data-ttu-id="6d806-155">En Windows PowerShell?, se representan los valores de parámetro por su tipo. NET.</span><span class="sxs-lookup"><span data-stu-id="6d806-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="6d806-156">Sin embargo, el nombre de tipo se puede abreviar, como "string" para System.String.</span><span class="sxs-lookup"><span data-stu-id="6d806-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="6d806-157">Abreviar como tipos, siempre está claro, como "string" para System.String y "int" para System.Int32 su significado.</span><span class="sxs-lookup"><span data-stu-id="6d806-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="6d806-158">Lista de todos los valores de enumeraciones, por ejemplo, el parámetro - type en el ejemplo anterior, que se puede establecer en "básico" o "avanzado".</span><span class="sxs-lookup"><span data-stu-id="6d806-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="6d806-159">Cambiar los parámetros, como - lista en el ejemplo anterior, no tienen valores.</span><span class="sxs-lookup"><span data-stu-id="6d806-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="6d806-160">Agregue los corchetes angulares a valores de parámetros que son el marcador de posición, en comparación con los valores de parámetros que son literales.</span><span class="sxs-lookup"><span data-stu-id="6d806-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="6d806-161">Incluya los parámetros opcionales y sus valores en corchetes.</span><span class="sxs-lookup"><span data-stu-id="6d806-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="6d806-162">Incluya los nombres de parámetros opcionales (para los parámetros posicionales) incluido entre corchetes.</span><span class="sxs-lookup"><span data-stu-id="6d806-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="6d806-163">El nombre de los parámetros posicionales, por ejemplo, el parámetro Name en el ejemplo siguiente, no es necesario que se incluirán en el comando.</span><span class="sxs-lookup"><span data-stu-id="6d806-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="6d806-164">Si un valor de parámetro puede contener varios valores, como una lista de nombres en el parámetro Name, agregue un par de corchetes después directamente el valor del parámetro.</span><span class="sxs-lookup"><span data-stu-id="6d806-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="6d806-165">Si el usuario puede elegir entre parámetros o valores de parámetro, como el parámetro de tipo, las opciones en entre llaves y sepárelos con el symbol(;) OR exclusivo.</span><span class="sxs-lookup"><span data-stu-id="6d806-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="6d806-166">Si el valor del parámetro debe usar un formato específico, como las comillas o paréntesis, muestran el formato en la sintaxis.</span><span class="sxs-lookup"><span data-stu-id="6d806-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="6d806-167">El diagrama de sintaxis XML de codificación</span><span class="sxs-lookup"><span data-stu-id="6d806-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="6d806-168">El nodo de sintaxis de XML comienza inmediatamente después del nodo de la descripción, que termina con la \</maml:description > etiqueta.</span><span class="sxs-lookup"><span data-stu-id="6d806-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="6d806-169">Para obtener información sobre la recopilación de los datos utilizados en el diagrama de sintaxis, vea [recopilar información sobre la sintaxis](#gathering-syntax-information).</span><span class="sxs-lookup"><span data-stu-id="6d806-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="6d806-170">Agregar un nodo de sintaxis</span><span class="sxs-lookup"><span data-stu-id="6d806-170">Adding a Syntax Node</span></span>

<span data-ttu-id="6d806-171">El diagrama de sintaxis que se muestra en el tema de ayuda se genera a partir de los datos en el nodo de sintaxis de XML.</span><span class="sxs-lookup"><span data-stu-id="6d806-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="6d806-172">El nodo de sintaxis está dentro de un par de \<: sintaxis de comando > etiquetas.</span><span class="sxs-lookup"><span data-stu-id="6d806-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="6d806-173">Con cada conjunto de parámetros del cmdlet entre un par de \<syntaxitem: comando > etiquetas.</span><span class="sxs-lookup"><span data-stu-id="6d806-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="6d806-174">No hay ningún límite al número de \<syntaxitem: comando > etiquetas que se pueden agregar.</span><span class="sxs-lookup"><span data-stu-id="6d806-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="6d806-175">El ejemplo siguiente muestra un nodo de sintaxis que tiene nodos de elemento de sintaxis de dos conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6d806-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="6d806-176">Agregar el nombre del Cmdlet para el parámetro de conjunto de datos</span><span class="sxs-lookup"><span data-stu-id="6d806-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="6d806-177">Cada conjunto de parámetros del cmdlet se especifica en un nodo de elemento de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="6d806-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="6d806-178">Cada nodo de elemento de sintaxis comienza con un par de \<maml:name > etiquetas que incluyan el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6d806-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="6d806-179">El ejemplo siguiente incluye un nodo de sintaxis que tiene nodos de elemento de sintaxis de dos conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6d806-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="6d806-180">Adición de parámetros</span><span class="sxs-lookup"><span data-stu-id="6d806-180">Adding Parameters</span></span>

<span data-ttu-id="6d806-181">Cada parámetro se agrega al nodo de elemento de sintaxis se especifica dentro de un par de \<: parámetro de comando > etiquetas.</span><span class="sxs-lookup"><span data-stu-id="6d806-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="6d806-182">Necesita un par de \<: parámetro de comando > etiquetas para cada parámetro incluido en el conjunto de parámetros, a excepción de los parámetros comunes proporcionadas por Windows PowerShell?.</span><span class="sxs-lookup"><span data-stu-id="6d806-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="6d806-183">Los atributos de la apertura \<: parámetro de comando > etiqueta determinar cómo el parámetro aparece en el diagrama de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="6d806-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="6d806-184">Para obtener información sobre los atributos de parámetro, vea [atributos de parámetro](#parameter-attributes).</span><span class="sxs-lookup"><span data-stu-id="6d806-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="6d806-185">El \<: parámetro de comando > etiqueta admite un elemento secundario \<maml:description > cuyo contenido nunca se muestra.</span><span class="sxs-lookup"><span data-stu-id="6d806-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="6d806-186">Las descripciones de parámetros se especifican en el nodo de parámetro de XML.</span><span class="sxs-lookup"><span data-stu-id="6d806-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="6d806-187">Para evitar incoherencias entre la información en el elemento de sintaxis intervención y el nodo de parámetro, omita el (\<maml:description > o déjela en blanco.</span><span class="sxs-lookup"><span data-stu-id="6d806-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="6d806-188">El ejemplo siguiente incluye un nodo de elemento de sintaxis para un parámetro de conjunto con dos parámetros.</span><span class="sxs-lookup"><span data-stu-id="6d806-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
