---
title: Cómo crear el archivo de ayuda de cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361204"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="8bbd9-102">Cómo crear el archivo de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bbd9-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="8bbd9-103">En esta sección se describe cómo crear un archivo XML válido que contenga contenido para los temas de ayuda de los cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="8bbd9-104">En esta sección se describe cómo asignar un nombre al archivo de ayuda, cómo agregar los encabezados XML adecuados y cómo agregar nodos que contendrán las diferentes secciones del contenido de la ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="8bbd9-105">Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll-Help. XML ubicados en el directorio de instalación de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="8bbd9-106">Por ejemplo, el archivo Microsoft. PowerShell. Commands. Management. dll-Help. xml contiene contenido para algunos de los cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="8bbd9-107">Cómo crear un archivo de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bbd9-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="8bbd9-108">Cree un archivo de texto y guárdelo con la codificación UTF8.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="8bbd9-109">El nombre de archivo debe tener el formato siguiente para que Windows PowerShell pueda detectarlo como un archivo de ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="8bbd9-110">Agregue los siguientes encabezados XML al archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="8bbd9-111">Tenga en cuenta que el archivo se validará con el esquema del lenguaje de modelado de varios agentes (MAML).</span><span class="sxs-lookup"><span data-stu-id="8bbd9-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="8bbd9-112">Actualmente, Windows PowerShell no proporciona ninguna herramienta para validar el archivo.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="8bbd9-113">Agregue un nodo de comando al archivo de ayuda de cmdlet para cada cmdlet en el ensamblado.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="8bbd9-114">Cada nodo dentro del nodo comando se relaciona con las distintas secciones del tema de ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="8bbd9-115">En la tabla siguiente se muestra el elemento XML para cada nodo, seguido de una descripción de cada nodo.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="8bbd9-116">Nodo</span><span class="sxs-lookup"><span data-stu-id="8bbd9-116">Node</span></span>|<span data-ttu-id="8bbd9-117">Descripción</span><span class="sxs-lookup"><span data-stu-id="8bbd9-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="8bbd9-118">Agrega contenido para las secciones nombre y Sinopsis del tema de ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="8bbd9-119">Para obtener más información, consulte [Agregar el nombre del cmdlet y la Sinopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="8bbd9-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="8bbd9-120">Agrega contenido para la sección Descripción del tema de ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="8bbd9-121">Para obtener más información, consulte [Cómo agregar la descripción detallada a un tema de ayuda de un cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="8bbd9-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="8bbd9-122">Agrega contenido para la sección de sintaxis del tema de ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="8bbd9-123">Para obtener más información, consulte [el tema de ayuda agregar sintaxis a un cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="8bbd9-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="8bbd9-124">Agrega contenido para la sección de parámetros del tema de ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8bbd9-125">Para obtener más información, vea [el tema de ayuda cómo agregar parámetros a un cmdlet](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="8bbd9-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="8bbd9-126">Agrega contenido para la sección de entradas del tema de ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8bbd9-127">Para obtener más información, vea [el tema de ayuda agregar tipos de entrada a un cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="8bbd9-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="8bbd9-128">Agrega contenido para la sección de resultados del tema de ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8bbd9-129">Para obtener más información, vea [el tema de ayuda cómo agregar valores devueltos a un cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="8bbd9-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="8bbd9-130">Agrega contenido a la sección Notas del tema de ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="8bbd9-131">Para obtener más información, consulte [el tema de ayuda agregar notas a un cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="8bbd9-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="8bbd9-132">Agrega contenido para la sección de ejemplos del tema de ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="8bbd9-133">Para obtener más información, consulte [el tema de ayuda agregar ejemplos a un cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="8bbd9-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="8bbd9-134">Agrega el contenido de la sección vínculos relacionados del tema de ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8bbd9-135">Para obtener más información, vea [Cómo agregar vínculos relacionados a un tema de ayuda de cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="8bbd9-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="8bbd9-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8bbd9-136">Example</span></span>

 <span data-ttu-id="8bbd9-137">Este es un ejemplo de un nodo de comando que incluye los nodos de las distintas secciones del tema de ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bbd9-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="8bbd9-138">Véase también</span><span class="sxs-lookup"><span data-stu-id="8bbd9-138">See Also</span></span>

 [<span data-ttu-id="8bbd9-139">Cómo agregar el nombre y la Sinopsis del cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bbd9-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8bbd9-140">Cómo agregar la descripción detallada a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bbd9-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="8bbd9-141">Cómo agregar sintaxis a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bbd9-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8bbd9-142">Cómo agregar parámetros a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bbd9-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="8bbd9-143">Cómo agregar tipos de entrada a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bbd9-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8bbd9-144">Cómo agregar valores devueltos a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bbd9-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8bbd9-145">Cómo agregar notas a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bbd9-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8bbd9-146">Cómo agregar ejemplos a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bbd9-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8bbd9-147">Cómo agregar vínculos relacionados a un tema de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bbd9-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8bbd9-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8bbd9-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)