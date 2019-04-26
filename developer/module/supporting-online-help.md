---
title: Compatibilidad con la Ayuda en línea | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082148"
---
# <a name="supporting-online-help"></a><span data-ttu-id="57703-102">Compatibilidad con la ayuda en línea</span><span class="sxs-lookup"><span data-stu-id="57703-102">Supporting Online Help</span></span>

<span data-ttu-id="57703-103">A partir de Windows PowerShell 3.0, hay dos maneras para admitir la `Get-Help` características en línea de comandos de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57703-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="57703-104">Este tema explica cómo implementar esta característica para los tipos de comandos diferente.</span><span class="sxs-lookup"><span data-stu-id="57703-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="57703-105">Acerca de la Ayuda en línea</span><span class="sxs-lookup"><span data-stu-id="57703-105">About Online Help</span></span>

<span data-ttu-id="57703-106">Ayuda en línea siempre ha sido una parte fundamental de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57703-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="57703-107">Aunque el `Get-Help` cmdlet muestra los temas de ayuda en el símbolo del sistema, muchos usuarios prefieren la experiencia de lectura en pantalla, como la codificación en colores, hipervínculos y para compartir ideas en el contenido de la Comunidad y documentos basados en la wiki.</span><span class="sxs-lookup"><span data-stu-id="57703-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="57703-108">Lo más importante, antes de la llegada de ayuda actualizable, ayuda en línea que proporciona la versión más actualizada de los archivos de ayuda.</span><span class="sxs-lookup"><span data-stu-id="57703-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="57703-109">Con la llegada de la Ayuda actualizable en Windows PowerShell 3.0, ayuda en línea sigue desempeñando un papel fundamental.</span><span class="sxs-lookup"><span data-stu-id="57703-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="57703-110">Además de la experiencia de usuario flexible, ayuda en línea proporciona ayuda a los usuarios que no lo hace o no se pueden usar la Ayuda actualizable para descargar los temas de ayuda.</span><span class="sxs-lookup"><span data-stu-id="57703-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="57703-111">Cómo Get-Help-Online Works</span><span class="sxs-lookup"><span data-stu-id="57703-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="57703-112">Para ayudar a los usuarios a encontrar los temas de ayuda en línea de comandos, el `Get-Help` comando tiene un parámetro en línea que se abre la versión en línea de tema de ayuda para un comando en el Explorador de Internet predeterminado del usuario.</span><span class="sxs-lookup"><span data-stu-id="57703-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="57703-113">Por ejemplo, el comando siguiente abre el tema de ayuda en línea el `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57703-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="57703-114">Para implementar `Get-Help` -en línea, el `Get-Help` cmdlet busca para un identificador uniforme de recursos (URI) para el tema de Ayuda de la versión en línea en las siguientes ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="57703-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="57703-115">El primer vínculo en la sección vínculos relacionados del tema de ayuda para el comando.</span><span class="sxs-lookup"><span data-stu-id="57703-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="57703-116">El tema de ayuda debe instalarse en el equipo del usuario.</span><span class="sxs-lookup"><span data-stu-id="57703-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="57703-117">Esta característica se introdujo en Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="57703-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="57703-118">La propiedad HelpUri de los comandos.</span><span class="sxs-lookup"><span data-stu-id="57703-118">The HelpUri property of any command.</span></span> <span data-ttu-id="57703-119">La propiedad HelpUri es accesible, incluso cuando el tema de ayuda para el comando no está instalado en el equipo del usuario.</span><span class="sxs-lookup"><span data-stu-id="57703-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="57703-120">Esta característica se introdujo en Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="57703-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="57703-121">`Get-Help` Busca un URI en la primera entrada en la sección vínculos relacionados antes de obtener el valor de la propiedad HelpUri.</span><span class="sxs-lookup"><span data-stu-id="57703-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="57703-122">Si el valor de propiedad no es correcto o ha cambiado, puede invalidarlo especificando un valor diferente en el primer vínculo relacionado.</span><span class="sxs-lookup"><span data-stu-id="57703-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="57703-123">Sin embargo, el primer vínculo relacionado sólo funciona si los temas de ayuda se instalan en el equipo del usuario.</span><span class="sxs-lookup"><span data-stu-id="57703-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="57703-124">Adición de un URI para el primer vínculo relacionado de un tema de Ayuda del comando</span><span class="sxs-lookup"><span data-stu-id="57703-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="57703-125">Puede admitir `Get-Help` -Online para cualquier comando mediante la adición de un URI válido para la primera entrada en la sección vínculos relacionados del tema de ayuda basado en XML para el comando.</span><span class="sxs-lookup"><span data-stu-id="57703-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="57703-126">Esta opción solo es válida en los temas de Ayuda basados en XML y solo funciona si el tema de ayuda está instalado en el equipo del usuario.</span><span class="sxs-lookup"><span data-stu-id="57703-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="57703-127">Cuando se instala el tema de ayuda y el URI se rellena, este valor tiene prioridad sobre la **HelpUri** propiedad del comando.</span><span class="sxs-lookup"><span data-stu-id="57703-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="57703-128">Para obtener información acerca de los temas de Ayuda basados en XML para los comandos, vea [Writing XML-Based temas de ayuda para los comandos](../help/writing-xml-based-help-topics-for-commands.md).</span><span class="sxs-lookup"><span data-stu-id="57703-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="57703-129">Para admitir esta característica, el URI debe aparecer en el `maml:uri` elemento debajo del primer `maml:relatedLinks/maml:navigationLink` elemento en el `maml:relatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="57703-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="57703-130">El siguiente XML muestra la posición correcta de la dirección URI.</span><span class="sxs-lookup"><span data-stu-id="57703-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="57703-131">La "versión en línea:" texto en el `maml:linkText` elemento es una práctica recomendada, pero no es necesario.</span><span class="sxs-lookup"><span data-stu-id="57703-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="57703-132">Adición de la propiedad HelpUri a un comando</span><span class="sxs-lookup"><span data-stu-id="57703-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="57703-133">En esta sección se muestra cómo agregar la propiedad HelpUri a los comandos de diferentes tipos.</span><span class="sxs-lookup"><span data-stu-id="57703-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="57703-134">Agregar una propiedad HelpUri a un Cmdlet</span><span class="sxs-lookup"><span data-stu-id="57703-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="57703-135">Para los cmdlets que se escriben C#, agregue un **HelpUri** a la clase de Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57703-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="57703-136">El valor del atributo debe ser un URI que empieza por "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="57703-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="57703-137">El código siguiente muestra el atributo HelpUri de los `Get-History` clase del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57703-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="57703-138">Agregar una propiedad HelpUri a una función avanzada</span><span class="sxs-lookup"><span data-stu-id="57703-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="57703-139">Para las funciones avanzadas, agregue un **HelpUri** propiedad a la **CmdletBinding** atributo.</span><span class="sxs-lookup"><span data-stu-id="57703-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="57703-140">El valor de la propiedad debe ser un URI que empieza por "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="57703-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="57703-141">El código siguiente muestra el atributo HelpUri de la función New-calendario</span><span class="sxs-lookup"><span data-stu-id="57703-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="57703-142">Agregar un atributo HelpUri a un comando CIM</span><span class="sxs-lookup"><span data-stu-id="57703-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="57703-143">Para los comandos CIM, agregue un **HelpUri** atributo a la **CmdletMetadata** elemento en el archivo CDXML.</span><span class="sxs-lookup"><span data-stu-id="57703-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="57703-144">El valor del atributo debe ser un URI que empieza por "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="57703-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="57703-145">El código siguiente muestra el atributo HelpUri del comando Start-Debug CIM</span><span class="sxs-lookup"><span data-stu-id="57703-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="57703-146">Agregar un atributo HelpUri a un flujo de trabajo</span><span class="sxs-lookup"><span data-stu-id="57703-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="57703-147">Para los flujos de trabajo que se escriben en el lenguaje de Windows PowerShell, agregue un **. ExternalHelp** comment (directiva) en el código de flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="57703-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="57703-148">El valor de la directiva debe ser un URI que empieza por "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="57703-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="57703-149">No se admite la propiedad HelpUri de los flujos de trabajo basados en XAML en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57703-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="57703-150">El código siguiente muestra el. Directiva ExternalHelp en un archivo de flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="57703-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```