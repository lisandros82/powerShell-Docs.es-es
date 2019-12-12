---
title: Escribir ayuda para cmdlets de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361074"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="e8d9b-102">Escribir ayuda para cmdlets de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8d9b-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="e8d9b-103">Los cmdlets de PowerShell pueden ser útiles, pero a menos que los temas de ayuda expliquen claramente lo que hace el cmdlet y cómo usarlos, puede que el cmdlet no se use o, incluso peor, pueda frustrar a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="e8d9b-104">El formato de archivo de ayuda de cmdlet basado en XML mejora la coherencia, pero una gran ayuda requiere mucho más.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="e8d9b-105">Si nunca ha escrito la ayuda de los cmdlets, revise las siguientes directrices.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="e8d9b-106">El esquema XML necesario para crear el tema de ayuda del cmdlet se describe en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="e8d9b-107">Empiece por [crear el archivo de ayuda del cmdlet](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="e8d9b-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="e8d9b-108">En ese tema se incluye una descripción de los nodos XML de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="e8d9b-109">Instrucciones de escritura para la ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8d9b-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="e8d9b-110">Escribir bien</span><span class="sxs-lookup"><span data-stu-id="e8d9b-110">Write well</span></span>
<span data-ttu-id="e8d9b-111">Nada reemplaza un tema bien escrito.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="e8d9b-112">Si no es un redactor profesional, busque un escritor o editor que le ayude.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="e8d9b-113">Otra alternativa es copiar el texto de ayuda en Microsoft Word y usar la gramática y las comprobaciones ortográficas para mejorar el trabajo.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="e8d9b-114">Escribir simplemente</span><span class="sxs-lookup"><span data-stu-id="e8d9b-114">Write simply</span></span>
<span data-ttu-id="e8d9b-115">Usar palabras y frases simples.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-115">Use simple words and phrases.</span></span>
<span data-ttu-id="e8d9b-116">Evite jerga.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-116">Avoid jargon.</span></span>
<span data-ttu-id="e8d9b-117">Tenga en cuenta que muchos lectores están equipados solo con un diccionario de idioma externo y el tema de ayuda.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="e8d9b-118">Escribir de forma coherente</span><span class="sxs-lookup"><span data-stu-id="e8d9b-118">Write consistently</span></span>
<span data-ttu-id="e8d9b-119">La ayuda para los cmdlets relacionados debe ser similar (por ejemplo, Get-x y set-x).</span><span class="sxs-lookup"><span data-stu-id="e8d9b-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="e8d9b-120">Use las descripciones estándar para los parámetros estándar, como **Force** e **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="e8d9b-121">(Cópielos de la ayuda para los cmdlets principales). Usar términos estándar.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="e8d9b-122">Por ejemplo, use "parámetro", no "argument" y use "cmdlet" no "Command" o "Command-Let".</span><span class="sxs-lookup"><span data-stu-id="e8d9b-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="e8d9b-123">Iniciar el resumen con un verbo</span><span class="sxs-lookup"><span data-stu-id="e8d9b-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="e8d9b-124">El campo Sinopsis informa al usuario de lo que hace el cmdlet, no de lo que es o cómo funciona.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="e8d9b-125">Los verbos crean una instrucción basada en tareas que informa a los usuarios si este cmdlet cumple sus requisitos.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="e8d9b-126">Use verbos simples como "Get", "Create" y "Change".</span><span class="sxs-lookup"><span data-stu-id="e8d9b-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="e8d9b-127">Evite "SET", que puede ser una palabra vaga y decorativa como "modificar".</span><span class="sxs-lookup"><span data-stu-id="e8d9b-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="e8d9b-128">Centrarse en objetos</span><span class="sxs-lookup"><span data-stu-id="e8d9b-128">Focus on objects</span></span>
<span data-ttu-id="e8d9b-129">La mayoría de los cmdlets "Get" muestran algo, pero su función principal es obtener un objeto.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="e8d9b-130">En su ayuda, céntrese en el objeto para que los usuarios sepan que la presentación predeterminada es uno de muchos y que pueden usar los métodos y las propiedades del objeto que recuperó para ellos de maneras diferentes.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="e8d9b-131">Escribir descripciones detalladas</span><span class="sxs-lookup"><span data-stu-id="e8d9b-131">Write detailed descriptions</span></span>
<span data-ttu-id="e8d9b-132">Enumere brevemente todo lo que puede hacer el cmdlet en la descripción detallada.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="e8d9b-133">Si la función principal es cambiar una propiedad, pero el cmdlet puede cambiar todas las propiedades, se muestra en la descripción detallada.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="e8d9b-134">Usar sintaxis convencional</span><span class="sxs-lookup"><span data-stu-id="e8d9b-134">Use conventional syntax</span></span>
<span data-ttu-id="e8d9b-135">Use el formato de Backus-Naur estándar, que es común para la ayuda de la línea de comandos de Windows y UNIX.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="e8d9b-136">Usar tipos de Microsoft .NET Framework para los valores de parámetro</span><span class="sxs-lookup"><span data-stu-id="e8d9b-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="e8d9b-137">Los marcadores de posición para los valores de parámetro (en las descripciones de sintaxis y parámetros) muestran los tipos de .NET Framework de los objetos que aceptará el parámetro.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="e8d9b-138">El equipo de PowerShell desarrolló esta Convención para ayudar a enseñar a los usuarios sobre el .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="e8d9b-139">Escribir descripciones completas de parámetros</span><span class="sxs-lookup"><span data-stu-id="e8d9b-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="e8d9b-140">Las descripciones de los parámetros deben informar a los usuarios de dos cosas: Qué hace el parámetro (su efecto) y qué deben escribir para los valores de parámetro.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="e8d9b-141">Escribir ejemplos prácticos</span><span class="sxs-lookup"><span data-stu-id="e8d9b-141">Write practical examples</span></span>
<span data-ttu-id="e8d9b-142">En los ejemplos se debe mostrar cómo usar todos los parámetros, pero lo más importante es mostrar cómo usar el cmdlet en tareas del mundo real.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="e8d9b-143">Comience con un ejemplo sencillo y escriba ejemplos cada vez más complejos.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="e8d9b-144">En el ejemplo final, muestre cómo usar el cmdlet en una canalización.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="e8d9b-145">Usar el campo notas</span><span class="sxs-lookup"><span data-stu-id="e8d9b-145">Use the Notes field</span></span>
<span data-ttu-id="e8d9b-146">Use el campo notas para explicar los conceptos que los usuarios necesitan para comprender el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="e8d9b-147">También puede usar notas para ayudar a los usuarios a evitar errores comunes.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="e8d9b-148">Evite las direcciones URL a medida que cambien.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="e8d9b-149">En su lugar, proporcione a los usuarios los términos que desea buscar.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="e8d9b-150">Probar su ayuda</span><span class="sxs-lookup"><span data-stu-id="e8d9b-150">Test your Help</span></span>
<span data-ttu-id="e8d9b-151">Pruebe la ayuda del mismo modo que prueba el código.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="e8d9b-152">Haga que sus amigos y compañeros lean el contenido de la ayuda y proporcionen Comentarios.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="e8d9b-153">También puede solicitar comentarios de los grupos de noticias.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8d9b-154">Véase también</span><span class="sxs-lookup"><span data-stu-id="e8d9b-154">See Also</span></span>

 [<span data-ttu-id="e8d9b-155">Cómo crear el archivo de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8d9b-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="e8d9b-156">Cómo agregar el nombre y la Sinopsis del cmdlet a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8d9b-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8d9b-157">Cómo agregar la descripción detallada a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8d9b-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="e8d9b-158">Cómo agregar sintaxis a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8d9b-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8d9b-159">Cómo agregar parámetros a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8d9b-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="e8d9b-160">Cómo agregar tipos de entrada a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8d9b-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8d9b-161">Cómo agregar valores devueltos a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8d9b-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8d9b-162">Cómo agregar notas a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8d9b-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8d9b-163">Cómo agregar ejemplos a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8d9b-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8d9b-164">Cómo agregar vínculos relacionados a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8d9b-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8d9b-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e8d9b-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)