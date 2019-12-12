---
title: Cómo agregar una sección Vea también a un tema de ayuda del proveedor | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367844"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="0dcdc-102">Cómo agregar una sección Consulte también a un tema de Ayuda de proveedor</span><span class="sxs-lookup"><span data-stu-id="0dcdc-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="0dcdc-103">En esta sección se explica cómo rellenar la sección **vea también** de un tema de ayuda del proveedor.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="0dcdc-104">La sección **vea también** contiene una lista de temas relacionados con el proveedor o puede ayudar al usuario a entender mejor y usar el proveedor.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="0dcdc-105">La lista de temas puede incluir la ayuda de los cmdlets, la ayuda del proveedor y los temas de ayuda conceptual ("About") en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="0dcdc-106">También puede incluir referencias a los libros, el papel y los temas en línea, incluida una versión en línea del tema de ayuda del proveedor actual.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="0dcdc-107">Cuando haga referencia a los temas en línea, proporcione el URI o un término de búsqueda en texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="0dcdc-108">El cmdlet `Get-Help` no vincula ni redirige a ninguno de los temas de la lista.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="0dcdc-109">Además, el parámetro `Online` del cmdlet `Get-Help` no funciona con la ayuda del proveedor.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="0dcdc-110">La sección Vea también se crea a partir del elemento `RelatedLinks` y las etiquetas que contiene.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="0dcdc-111">El siguiente XML muestra cómo agregar las etiquetas.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="0dcdc-112">Para agregar temas "vea también"</span><span class="sxs-lookup"><span data-stu-id="0dcdc-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="0dcdc-113">En el archivo *AssemblyName*. dll-help. XML, dentro del elemento `providerHelp`, agregue un elemento `RelatedLinks`.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="0dcdc-114">El elemento `RelatedLinks` debe ser el último elemento del elemento `providerHelp`.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="0dcdc-115">Solo se permite un elemento `RelatedLinks` en el tema de ayuda de cada proveedor.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="0dcdc-116">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="0dcdc-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="0dcdc-117">Para cada tema de la sección **vea también** , dentro del elemento `RelatedLinks`, agregue un elemento `navigationLink`.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="0dcdc-118">Después, dentro de cada elemento `navigationLink`, agregue un elemento `linkText` y un elemento `uri`.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="0dcdc-119">Si no está utilizando el elemento `uri`, puede agregarlo como un elemento vacío (\<URI/>).</span><span class="sxs-lookup"><span data-stu-id="0dcdc-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="0dcdc-120">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="0dcdc-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="0dcdc-121">Escriba el nombre del tema entre las etiquetas de `linkText`.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="0dcdc-122">Si va a proporcionar un URI, escríbalo entre las etiquetas de `uri`.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="0dcdc-123">Para indicar la versión en línea del tema de ayuda del proveedor actual, entre las etiquetas de `linkText`, escriba "versión en línea:" en lugar del nombre del tema.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="0dcdc-124">Normalmente, el vínculo "versión en línea:" es el primer tema de la lista de temas vea también.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="0dcdc-125">En el ejemplo siguiente se incluyen tres temas, vea también.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="0dcdc-126">El primero hace referencia a la versión en línea del tema actual.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="0dcdc-127">El segundo hace referencia a un tema de ayuda de cmdlet de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="0dcdc-128">El tercero hace referencia a otro tema en línea.</span><span class="sxs-lookup"><span data-stu-id="0dcdc-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```