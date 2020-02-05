---
title: Compatibilidad con la ayuda en línea | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: cf181e8f26ebd4b9c57b5b0191809211f2471f13
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995585"
---
# <a name="supporting-online-help"></a><span data-ttu-id="bc84d-102">Compatibilidad con la ayuda en línea</span><span class="sxs-lookup"><span data-stu-id="bc84d-102">Supporting Online Help</span></span>

<span data-ttu-id="bc84d-103">A partir de Windows PowerShell 3,0, hay dos maneras de admitir la característica `Get-Help` online para los comandos de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc84d-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="bc84d-104">En este tema se explica cómo implementar esta característica para distintos tipos de comandos.</span><span class="sxs-lookup"><span data-stu-id="bc84d-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="bc84d-105">Acerca de la ayuda en línea</span><span class="sxs-lookup"><span data-stu-id="bc84d-105">About Online Help</span></span>

<span data-ttu-id="bc84d-106">La ayuda en línea siempre ha sido una parte fundamental de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc84d-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="bc84d-107">Aunque el cmdlet `Get-Help` muestra temas de ayuda en el símbolo del sistema, muchos usuarios prefieren la experiencia de lectura en línea, como la codificación de colores, los hipervínculos y el uso compartido de ideas en el contenido de la comunidad y en los documentos basados en wiki.</span><span class="sxs-lookup"><span data-stu-id="bc84d-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="bc84d-108">Lo más importante, antes de la llegada de la ayuda actualizable, la ayuda en línea proporcionó la versión más actualizada de los archivos de ayuda.</span><span class="sxs-lookup"><span data-stu-id="bc84d-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="bc84d-109">Con la llegada de la ayuda actualizable en Windows PowerShell 3,0, la ayuda en línea sigue desempeñando un papel fundamental.</span><span class="sxs-lookup"><span data-stu-id="bc84d-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="bc84d-110">Además de la experiencia de usuario flexible, la ayuda en línea proporciona ayuda a los usuarios que no pueden usar la ayuda actualizable para descargar temas de ayuda.</span><span class="sxs-lookup"><span data-stu-id="bc84d-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="bc84d-111">Funcionamiento de Get-Help-online</span><span class="sxs-lookup"><span data-stu-id="bc84d-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="bc84d-112">Para ayudar a los usuarios a encontrar los temas de ayuda en línea para los comandos, el comando `Get-Help` tiene un parámetro en línea que abre la versión en línea del tema de ayuda para un comando en el explorador de Internet predeterminado del usuario.</span><span class="sxs-lookup"><span data-stu-id="bc84d-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="bc84d-113">Por ejemplo, el siguiente comando abre el tema de ayuda en pantalla para el cmdlet `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="bc84d-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="bc84d-114">Para implementar `Get-Help` en línea, el cmdlet `Get-Help` busca un identificador uniforme de recursos (URI) para el tema de ayuda de la versión en línea en las siguientes ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="bc84d-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="bc84d-115">El primer vínculo de la sección vínculos relacionados del tema de ayuda para el comando.</span><span class="sxs-lookup"><span data-stu-id="bc84d-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="bc84d-116">El tema de ayuda debe instalarse en el equipo del usuario.</span><span class="sxs-lookup"><span data-stu-id="bc84d-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="bc84d-117">Esta característica se presentó en Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="bc84d-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="bc84d-118">La propiedad HelpUri de cualquier comando.</span><span class="sxs-lookup"><span data-stu-id="bc84d-118">The HelpUri property of any command.</span></span> <span data-ttu-id="bc84d-119">La propiedad HelpUri es accesible incluso cuando el tema de ayuda para el comando no está instalado en el equipo del usuario.</span><span class="sxs-lookup"><span data-stu-id="bc84d-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="bc84d-120">Esta característica se presentó en Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bc84d-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="bc84d-121">`Get-Help` busca un URI en la primera entrada de la sección vínculos relacionados antes de obtener el valor de la propiedad HelpUri.</span><span class="sxs-lookup"><span data-stu-id="bc84d-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="bc84d-122">Si el valor de la propiedad es incorrecto o ha cambiado, puede invalidarlo escribiendo un valor diferente en el primer vínculo relacionado.</span><span class="sxs-lookup"><span data-stu-id="bc84d-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="bc84d-123">Sin embargo, el primer vínculo relacionado solo funciona cuando los temas de ayuda se instalan en el equipo del usuario.</span><span class="sxs-lookup"><span data-stu-id="bc84d-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="bc84d-124">Agregar un URI al primer vínculo relacionado de un tema de ayuda de comando</span><span class="sxs-lookup"><span data-stu-id="bc84d-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="bc84d-125">Puede admitir `Get-Help`-online para cualquier comando agregando un URI válido a la primera entrada de la sección vínculos relacionados del tema de ayuda basado en XML para el comando.</span><span class="sxs-lookup"><span data-stu-id="bc84d-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="bc84d-126">Esta opción solo es válida en los temas de ayuda basados en XML y solo funciona cuando el tema de ayuda está instalado en el equipo del usuario.</span><span class="sxs-lookup"><span data-stu-id="bc84d-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="bc84d-127">Cuando se instala el tema de ayuda y se rellena el URI, este valor tiene prioridad sobre la propiedad **HelpUri** del comando.</span><span class="sxs-lookup"><span data-stu-id="bc84d-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="bc84d-128">Para admitir esta característica, el URI debe aparecer en el elemento `maml:uri` bajo el primer elemento `maml:relatedLinks/maml:navigationLink` del elemento `maml:relatedLinks`.</span><span class="sxs-lookup"><span data-stu-id="bc84d-128">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="bc84d-129">El siguiente XML muestra la ubicación correcta del URI.</span><span class="sxs-lookup"><span data-stu-id="bc84d-129">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="bc84d-130">Se recomienda el texto "versión en línea:" del elemento `maml:linkText`, pero no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bc84d-130">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="bc84d-131">Agregar la propiedad HelpUri a un comando</span><span class="sxs-lookup"><span data-stu-id="bc84d-131">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="bc84d-132">En esta sección se muestra cómo agregar la propiedad HelpUri a los comandos de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="bc84d-132">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="bc84d-133">Agregar una propiedad HelpUri a un cmdlet</span><span class="sxs-lookup"><span data-stu-id="bc84d-133">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="bc84d-134">En el caso de los C#cmdlets escritos en, agregue un atributo **HelpUri** a la clase de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bc84d-134">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="bc84d-135">El valor del atributo debe ser un URI que comience por "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="bc84d-135">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="bc84d-136">En el código siguiente se muestra el atributo HelpUri de la clase de cmdlet `Get-History`.</span><span class="sxs-lookup"><span data-stu-id="bc84d-136">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="bc84d-137">Agregar una propiedad HelpUri a una función avanzada</span><span class="sxs-lookup"><span data-stu-id="bc84d-137">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="bc84d-138">En el caso de las funciones avanzadas, agregue una propiedad **HelpUri** al atributo **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="bc84d-138">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="bc84d-139">El valor de la propiedad debe ser un URI que comience por "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="bc84d-139">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="bc84d-140">En el código siguiente se muestra el atributo HelpUri de la función New-Calendar.</span><span class="sxs-lookup"><span data-stu-id="bc84d-140">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="bc84d-141">Agregar un atributo HelpUri a un comando CIM</span><span class="sxs-lookup"><span data-stu-id="bc84d-141">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="bc84d-142">En el caso de los comandos CIM, agregue un atributo **HelpUri** al elemento **CmdletMetadata** en el archivo CDXML.</span><span class="sxs-lookup"><span data-stu-id="bc84d-142">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="bc84d-143">El valor del atributo debe ser un URI que comience por "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="bc84d-143">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="bc84d-144">En el código siguiente se muestra el atributo HelpUri del comando CIM Start-Debug</span><span class="sxs-lookup"><span data-stu-id="bc84d-144">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="bc84d-145">Agregar un atributo HelpUri a un flujo de trabajo</span><span class="sxs-lookup"><span data-stu-id="bc84d-145">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="bc84d-146">En el caso de los flujos de trabajo que se escriben en el lenguaje de Windows PowerShell, agregue un **. ExternalHelp** : Directiva de comentario al código del flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="bc84d-146">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="bc84d-147">El valor de la Directiva debe ser un URI que comience por "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="bc84d-147">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="bc84d-148">La propiedad HelpUri no es compatible con los flujos de trabajo basados en XAML en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc84d-148">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="bc84d-149">En el código siguiente se muestra el. Directiva ExternalHelp en un archivo de flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="bc84d-149">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```