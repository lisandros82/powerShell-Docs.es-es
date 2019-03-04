---
title: Escritura de ayuda para Cmdlets de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857861"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="cfe9c-102">Escribir ayuda para Cmdlets de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfe9c-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="cfe9c-103">Cmdlets de PowerShell puede ser útiles, pero a menos que los temas de ayuda explicar con claridad lo que hace el cmdlet y cómo usarlo, el cmdlet no puede obtener usa o, aún peor, puede frustrar a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="cfe9c-104">El formato de archivo de Ayuda de cmdlet basado en XML mejora la coherencia, pero muy útil requiere mucho más.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="cfe9c-105">Si nunca ha escrito ayuda del cmdlet, revise las siguientes directrices.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="cfe9c-106">El esquema XML necesario para crear el tema de ayuda se describe en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="cfe9c-107">Comience con [crear el archivo de Ayuda de Cmdlet](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="cfe9c-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="cfe9c-108">Ese tema incluye una descripción de los nodos XML de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="cfe9c-109">Directrices de estilo para obtener ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfe9c-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="cfe9c-110">Escriba</span><span class="sxs-lookup"><span data-stu-id="cfe9c-110">Write well</span></span>
<span data-ttu-id="cfe9c-111">Nada reemplaza un tema bien escrito.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="cfe9c-112">Si no es un escritor profesional, encontrar un sistema de escritura o el editor que le ayudarán a.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="cfe9c-113">Otra alternativa consiste en copiar el texto de ayuda en Microsoft Word y el uso de la gramática y ortografía comprueba para mejorar su trabajo.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="cfe9c-114">Basta con escribir</span><span class="sxs-lookup"><span data-stu-id="cfe9c-114">Write simply</span></span>
<span data-ttu-id="cfe9c-115">Use simple palabras y frases.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-115">Use simple words and phrases.</span></span>
<span data-ttu-id="cfe9c-116">Evitar los tecnicismos.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-116">Avoid jargon.</span></span>
<span data-ttu-id="cfe9c-117">Tenga en cuenta que muchos lectores están equipados solo con un diccionario de idioma extranjero y el tema de ayuda.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="cfe9c-118">Escribir de forma coherente</span><span class="sxs-lookup"><span data-stu-id="cfe9c-118">Write consistently</span></span>
<span data-ttu-id="cfe9c-119">Ayuda para cmdlets relacionados deben ser similares (por ejemplo, get-x y set-x).</span><span class="sxs-lookup"><span data-stu-id="cfe9c-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="cfe9c-120">Use las descripciones estándares para los parámetros estándares, como **Force** y **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="cfe9c-121">(Copiarlos de Ayuda de los cmdlets principales.) Utilice términos estándares.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="cfe9c-122">Por ejemplo, "uso del parámetro", no "argumento" y use "cmdlet" no "comando" o "command-let".</span><span class="sxs-lookup"><span data-stu-id="cfe9c-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="cfe9c-123">Comience la sinopsis de con un verbo</span><span class="sxs-lookup"><span data-stu-id="cfe9c-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="cfe9c-124">El campo Sinopsis, informa al usuario que hace que el cmdlet, no es así o su funcionamiento.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="cfe9c-125">Verbos creación una instrucción basado en tareas que informa a los usuarios si este cmdlet cumple sus requisitos.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="cfe9c-126">Usar los verbos simple como "get", "crear" y "cambiar".</span><span class="sxs-lookup"><span data-stu-id="cfe9c-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="cfe9c-127">Evite "set", que puede ser poco precisas y elegantes palabras como "modificar".</span><span class="sxs-lookup"><span data-stu-id="cfe9c-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="cfe9c-128">Centrarse en los objetos</span><span class="sxs-lookup"><span data-stu-id="cfe9c-128">Focus on objects</span></span>
<span data-ttu-id="cfe9c-129">La mayoría "get" para mostrar los cmdlets algo, pero su función principal es obtener un objeto.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="cfe9c-130">En la Ayuda, se centran en el objeto, por lo que los usuarios sepan que la visualización predeterminada es uno de ellos, y que pueden utilizar los métodos y propiedades del objeto que ha recuperado de ellas de maneras diferentes.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="cfe9c-131">Escribir una descripción detallada</span><span class="sxs-lookup"><span data-stu-id="cfe9c-131">Write detailed descriptions</span></span>
<span data-ttu-id="cfe9c-132">Enumere brevemente todo lo que el cmdlet puede hacer en la descripción detallada.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="cfe9c-133">Si la función principal consiste en cambiar una propiedad, pero el cmdlet puede cambiar todas las propiedades, esta lista en la descripción detallada.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="cfe9c-134">Utilice la sintaxis convencional</span><span class="sxs-lookup"><span data-stu-id="cfe9c-134">Use conventional syntax</span></span>
<span data-ttu-id="cfe9c-135">Use el formato de Backus-Naur estándar que es común para Windows y la Ayuda de línea de comandos de UNIX.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="cfe9c-136">Usar tipos de Microsoft .NET Framework para los valores de parámetro</span><span class="sxs-lookup"><span data-stu-id="cfe9c-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="cfe9c-137">Los marcadores de posición para los valores de parámetro (en las descripciones de sintaxis y parámetros) muestran los tipos de .NET Framework de los objetos que se va a aceptar el parámetro.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="cfe9c-138">El equipo de PowerShell desarrolló esta convención para ayudar a enseñar a los usuarios sobre .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="cfe9c-139">Escribir las descripciones de parámetros completo</span><span class="sxs-lookup"><span data-stu-id="cfe9c-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="cfe9c-140">Descripciones de parámetros deben informar a los usuarios de estas dos cosas: utiliza el parámetro realiza (su efecto) y lo que debe escribir los valores de parámetro.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="cfe9c-141">Escribir ejemplos prácticos</span><span class="sxs-lookup"><span data-stu-id="cfe9c-141">Write practical examples</span></span>
<span data-ttu-id="cfe9c-142">Los ejemplos deberían mostrar cómo usar todos los parámetros, pero lo más importante es mostrar cómo usar el cmdlet en tareas reales.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="cfe9c-143">Comience con un ejemplo sencillo y escribir los ejemplos de cada vez más complejos.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="cfe9c-144">En el último ejemplo, muestra cómo usar el cmdlet en una canalización.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="cfe9c-145">Utilice el campo Notas</span><span class="sxs-lookup"><span data-stu-id="cfe9c-145">Use the Notes field</span></span>
<span data-ttu-id="cfe9c-146">Utilice el campo Notas para explicar los conceptos que los usuarios necesitan conocer el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="cfe9c-147">También puede usar notas para ayudar a los usuarios a evitar errores comunes.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="cfe9c-148">Evite las direcciones URL cuando cambien.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="cfe9c-149">En su lugar, proporcione los términos de los usuarios a buscar.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="cfe9c-150">Probar la Ayuda</span><span class="sxs-lookup"><span data-stu-id="cfe9c-150">Test your Help</span></span>
<span data-ttu-id="cfe9c-151">Probar la Ayuda, al igual que probar el código.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="cfe9c-152">Tiene amigos y compañeros leen el contenido de ayuda y proporcionan comentarios.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="cfe9c-153">También puede solicitar comentarios de los grupos de noticias.</span><span class="sxs-lookup"><span data-stu-id="cfe9c-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfe9c-154">Véase también</span><span class="sxs-lookup"><span data-stu-id="cfe9c-154">See Also</span></span>

 [<span data-ttu-id="cfe9c-155">Cómo crear el archivo de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfe9c-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="cfe9c-156">Cómo agregar el nombre de Cmdlet y Sinopsis a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfe9c-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cfe9c-157">Cómo agregar la descripción detallada a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfe9c-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="cfe9c-158">Cómo agregar una sintaxis para un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfe9c-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cfe9c-159">Cómo agregar parámetros a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfe9c-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="cfe9c-160">Cómo agregar tipos de entrada a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfe9c-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cfe9c-161">Cómo agregar los valores devueltos a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfe9c-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cfe9c-162">Cómo agregar notas a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfe9c-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cfe9c-163">Cómo agregar ejemplos para un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfe9c-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cfe9c-164">Cómo agregar vínculos relacionados a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfe9c-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cfe9c-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cfe9c-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)