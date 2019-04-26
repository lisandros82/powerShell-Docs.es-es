---
title: Cómo crear el archivo de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083253"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="fda5e-102">Cómo crear el archivo de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="fda5e-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="fda5e-103">En esta sección se describe cómo crear un archivo XML válido que contiene el contenido de los temas de Ayuda de cmdlet de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fda5e-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="fda5e-104">Esta sección describe cómo asignar un nombre de archivo de ayuda, cómo agregar los encabezados adecuados de XML y cómo agregar nodos que va a contener las diferentes secciones del contenido de la Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="fda5e-105">Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll Help.xml ubicado en el directorio de instalación de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fda5e-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="fda5e-106">Por ejemplo, el archivo Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenido para varios de los cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fda5e-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="fda5e-107">Cómo crear un archivo de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fda5e-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="fda5e-108">Cree un archivo de texto y guárdelo con la codificación UTF8.</span><span class="sxs-lookup"><span data-stu-id="fda5e-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="fda5e-109">El nombre de archivo debe tener el formato siguiente para que Windows PowerShell lo detectará como un archivo de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="fda5e-110">Agregue los siguientes encabezados XML al archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="fda5e-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="fda5e-111">Tenga en cuenta que el archivo se validará con respecto al esquema de lenguaje de modelado Multiagente (MAML).</span><span class="sxs-lookup"><span data-stu-id="fda5e-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="fda5e-112">Actualmente, Windows PowerShell no proporciona ninguna herramienta para validar el archivo.</span><span class="sxs-lookup"><span data-stu-id="fda5e-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="fda5e-113">Agregar un nodo de comandos al archivo de Ayuda de cmdlet para cada cmdlet en el ensamblado.</span><span class="sxs-lookup"><span data-stu-id="fda5e-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="fda5e-114">Cada nodo dentro del nodo de comando se relaciona con las diferentes secciones del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="fda5e-115">La tabla siguiente muestra el elemento XML para cada nodo, seguido de una descripción de cada nodo.</span><span class="sxs-lookup"><span data-stu-id="fda5e-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="fda5e-116">nodo</span><span class="sxs-lookup"><span data-stu-id="fda5e-116">Node</span></span>|<span data-ttu-id="fda5e-117">Descripción</span><span class="sxs-lookup"><span data-stu-id="fda5e-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="fda5e-118">Agrega el contenido de las secciones de nombre y una sinopsis del tema de ayuda.</span><span class="sxs-lookup"><span data-stu-id="fda5e-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="fda5e-119">Para obtener más información, consulte [cómo agregar el nombre del Cmdlet y Sinopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="fda5e-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="fda5e-120">Agrega el contenido de la sección de descripción del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="fda5e-121">Para obtener más información, consulte [cómo agregar la descripción detallada para un tema de Ayuda de Cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="fda5e-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="fda5e-122">Agrega el contenido de la sección de sintaxis del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="fda5e-123">Para obtener más información, consulte [cómo agregar sintaxis para un tema de Ayuda de Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="fda5e-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="fda5e-124">Agrega el contenido de la sección de parámetros del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="fda5e-125">Para obtener más información, consulte [cómo agregar parámetros a un tema de Ayuda de Cmdlet](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="fda5e-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="fda5e-126">Agrega el contenido de la sección entradas de tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="fda5e-127">Para obtener más información, consulte [cómo agregar tipos de entrada a un tema de Ayuda de Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="fda5e-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="fda5e-128">Agrega el contenido de la sección de salidas del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="fda5e-129">Para obtener más información, consulte [cómo agregar los valores devueltos para un tema de Ayuda de Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="fda5e-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="fda5e-130">Agrega contenido a la sección Notas del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="fda5e-131">Para obtener más información, consulte [cómo agregar notas a un tema de Ayuda de Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="fda5e-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="fda5e-132">Agrega el contenido de la sección de ejemplos del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="fda5e-133">Para obtener más información, consulte [cómo agregar ejemplos para un tema de Ayuda de Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="fda5e-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="fda5e-134">Agrega el contenido de la sección vínculos relacionados del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="fda5e-135">Para obtener más información, consulte [cómo agregar vínculos relacionados a un tema de Ayuda de Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="fda5e-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="fda5e-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fda5e-136">Example</span></span>

 <span data-ttu-id="fda5e-137">Este es un ejemplo de un nodo de comandos que incluya los nodos para las distintas secciones del tema de Ayuda de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fda5e-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fda5e-138">Véase también</span><span class="sxs-lookup"><span data-stu-id="fda5e-138">See Also</span></span>

 [<span data-ttu-id="fda5e-139">Cómo agregar el nombre del Cmdlet y Sinopsis</span><span class="sxs-lookup"><span data-stu-id="fda5e-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="fda5e-140">Cómo agregar la descripción detallada a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fda5e-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="fda5e-141">Cómo agregar una sintaxis para un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fda5e-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="fda5e-142">Cómo agregar parámetros a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fda5e-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="fda5e-143">Cómo agregar tipos de entrada a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fda5e-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="fda5e-144">Cómo agregar los valores devueltos a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fda5e-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="fda5e-145">Cómo agregar notas a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fda5e-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="fda5e-146">Cómo agregar ejemplos para un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fda5e-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="fda5e-147">Cómo agregar vínculos relacionados a un tema de Ayuda de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fda5e-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="fda5e-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fda5e-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)