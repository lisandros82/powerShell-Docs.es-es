---
title: Cómo agregar información de parámetros | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863331"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="cc5f2-102">Cómo agregar información de parámetros</span><span class="sxs-lookup"><span data-stu-id="cc5f2-102">How to Add Parameter Information</span></span>

<span data-ttu-id="cc5f2-103">En esta sección se describe cómo agregar contenido que se muestra en la sección de parámetros del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="cc5f2-104">La sección de parámetros del tema de ayuda enumera cada uno de los parámetros del cmdlet y proporciona una descripción detallada de cada parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="cc5f2-105">El contenido de la sección de parámetros debe ser coherente con el contenido de la sección de sintaxis del tema de ayuda.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="cc5f2-106">Es responsabilidad del autor de ayuda para asegurarse de que el nodo de la sintaxis y los parámetros contiene elementos XML similar.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="cc5f2-107">Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll Help.xml ubicado en el directorio de instalación de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="cc5f2-108">Por ejemplo, el archivo Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenido para varios de los cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="cc5f2-109">Para agregar parámetros</span><span class="sxs-lookup"><span data-stu-id="cc5f2-109">To Add Parameters</span></span>

1. <span data-ttu-id="cc5f2-110">Abra el archivo de Ayuda de cmdlet y busque el nodo de comando para el cmdlet que está documentando.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="cc5f2-111">Si va a agregar un nuevo cmdlet, que deberá crear un nuevo nodo de comando.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="cc5f2-112">El archivo de Ayuda contiene un nodo de comando para cada cmdlet que se va a proporcionar contenido de ayuda.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="cc5f2-113">Este es un ejemplo de un nodo en blanco del comando.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="cc5f2-114">Dentro del nodo de comandos, busque el nodo de la descripción y agregar un nodo de parámetros como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="cc5f2-115">Se permite un único nodo de parámetros y debe seguir inmediatamente el nodo de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="cc5f2-116">Dentro del nodo de parámetros, agregue un nodo de parámetro para cada parámetro del cmdlet tal como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="cc5f2-117">En este ejemplo, se agrega un nodo de parámetro para tres parámetros.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="cc5f2-118">Dado que son las mismas etiquetas XML que se usan en el nodo de sintaxis y dado que los parámetros se especifican aquí deben coincidir con los parámetros especificados por el nodo de sintaxis, puede copiar los nodos de parámetro desde el nodo de sintaxis y péguelos en el nodo de parámetros.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="cc5f2-119">Sin embargo, no olvide copiar solo una instancia de un nodo de parámetro, incluso si se especifica el parámetro en múltiples conjuntos de parámetros en la sintaxis.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="cc5f2-120">Para cada parámetro de conjunto de nodos, los valores de atributo que definen las características de cada parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="cc5f2-121">Estos atributos incluyen lo siguiente: era necesario, uso de comodines, pipelineinput y posición.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. <span data-ttu-id="cc5f2-122">Para cada nodo de parámetro, agregue el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="cc5f2-123">Este es un ejemplo del nombre de parámetro que se agrega al nodo de parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="cc5f2-124">Para cada nodo de parámetro, agregue la descripción del parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="cc5f2-125">Este es un ejemplo de la descripción del parámetro que se agrega al nodo de parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-125">Here is an example of the parameter description added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. <span data-ttu-id="cc5f2-126">Para cada nodo de parámetro, agregue el tipo de .NET Framework del parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="cc5f2-127">El tipo de parámetro se muestra junto con el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="cc5f2-128">Este es un ejemplo del tipo de .NET Framework parámetro agregado al nodo de parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. <span data-ttu-id="cc5f2-129">Para cada nodo de parámetro, agregue el valor predeterminado del parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="cc5f2-130">La siguiente frase se agrega a la descripción del parámetro cuando se muestra el contenido: "DefaultValue" es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="cc5f2-131">Este es un ejemplo del valor de parámetro predeterminado se agrega al nodo de parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. <span data-ttu-id="cc5f2-132">Para cada parámetro que tenga varios valores, agregar un nodo de los valores posibles.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="cc5f2-133">Este es un ejemplo de la de un nodo de los valores posibles que se define dos valores posibles para el parámetro</span><span class="sxs-lookup"><span data-stu-id="cc5f2-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

<span data-ttu-id="cc5f2-134">Estas son algunas cosas que recordar cuando se agregan parámetros.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="cc5f2-135">No se muestran los atributos del parámetro en todas las vistas del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="cc5f2-136">Sin embargo, se muestran en una tabla siguiendo la descripción del parámetro cuando el usuario pide para la versión completa (Get-Help \<cmdletname >-completa) o un parámetro (Get-Help \<cmdletname >-parámetro) del tema de la vista.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="cc5f2-137">La descripción del parámetro es una de las partes más importantes de un tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="cc5f2-138">La descripción debe ser breve, así como completa.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="cc5f2-139">Además, recuerde que, si la descripción del parámetro es demasiado larga, por ejemplo, cuando dos parámetros interactúan entre sí, puede agregar más contenido en la sección Notas del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="cc5f2-140">La descripción del parámetro proporciona dos tipos de información.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="cc5f2-141">¿Qué hace el cmdlet cuando se usa el parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="cc5f2-142">Es lo que un valor válido para el parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="cc5f2-143">Dado que los valores de parámetros se expresan como objetos de .NET Framework, los usuarios necesitan obtener más información acerca de estos valores de la que tendrían en la Ayuda de línea de comandos tradicionales.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="cc5f2-144">Indicar al usuario qué tipo de datos del parámetro está diseñado para aceptar e incluyen ejemplos.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="cc5f2-145">El valor predeterminado del parámetro es el valor que se usa si el parámetro no se especifica en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="cc5f2-146">Tenga en cuenta que el valor predeterminado es opcional y no es necesario para algunos parámetros, como los parámetros necesarios.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="cc5f2-147">Sin embargo, debe especificar un valor predeterminado para la mayoría de los parámetros opcional.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="cc5f2-148">El valor predeterminado ayuda al usuario a entender el efecto de no usar el parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="cc5f2-149">Describe el valor predeterminado muy concreto, como la "Current directory" o "Windows PowerShell directorio de instalación ($pshome)" para una ruta de acceso opcional.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="cc5f2-150">También puede escribir una frase que describe el valor predeterminado, por ejemplo, la siguiente frase usada para el `PassThru` parámetro: "Si no se especifica PassThru, el cmdlet no pasar objetos a través de la canalización."</span><span class="sxs-lookup"><span data-stu-id="cc5f2-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="cc5f2-151">Además, dado que se muestra el valor contrario el nombre del campo "**valor predeterminado**", no es necesario incluir el término "default value" en la entrada.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="cc5f2-152">El valor predeterminado del parámetro no se muestra en todas las vistas del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="cc5f2-153">Sin embargo, se muestra en una tabla (junto con los atributos de parámetro) siguiendo la descripción del parámetro cuando el usuario pide para la versión completa (Get-Help \<cmdletname >-full) o un parámetro (Get-Help \<cmdletname >-parámetro) vista del tema.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="cc5f2-154">El siguiente XML muestra un par de `<dev:defaultValue>` etiquetas agregadas a la `<command:parameter>` nodo.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="cc5f2-155">Tenga en cuenta que el valor predeterminado sigue inmediatamente después del cierre `</command:parameterValue>` etiqueta (cuando se especifica el valor del parámetro) o el cierre `</maml:description>` etiqueta de la descripción del parámetro.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="cc5f2-156">Nombre.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-156">name.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

<span data-ttu-id="cc5f2-157">Agregue valores para los tipos enumerados</span><span class="sxs-lookup"><span data-stu-id="cc5f2-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="cc5f2-158">Si el parámetro tiene varios valores o un tipo enumerado, puede usar un elemento opcional \<dev:possibleValues > nodo.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="cc5f2-159">Este nodo permite especificar un nombre y una descripción de varios valores.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="cc5f2-160">Tenga en cuenta que las descripciones de los valores enumerados no aparecen en cualquiera de las predeterminadas vistas de ayuda mostradas por el `Get-Help` cmdlet, pero otros visores de ayuda pueden mostrar este contenido en sus vistas.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="cc5f2-161">El siguiente XML muestra un `<dev:possibleValues>` nodo con dos valores especificados.</span><span class="sxs-lookup"><span data-stu-id="cc5f2-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```