---
title: Cómo agregar el nombre y la Sinopsis del cmdlet a un tema de ayuda de cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361194"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="066cb-102">Cómo agregar el nombre del cmdlet y la sinopsis a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="066cb-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="066cb-103">En esta sección se describe cómo agregar el contenido que se muestra en las secciones nombre y Sinopsis de la ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="066cb-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="066cb-104">En el archivo de ayuda, este contenido se agrega al nodo comando para cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="066cb-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="066cb-105">Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll-Help. XML ubicados en el directorio de instalación de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="066cb-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="066cb-106">Por ejemplo, el archivo Microsoft. PowerShell. Commands. Management. dll-Help. xml contiene contenido para algunos de los cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="066cb-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="066cb-107">Para agregar el nombre del cmdlet y un resumen</span><span class="sxs-lookup"><span data-stu-id="066cb-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="066cb-108">La ayuda del cmdlet puede mostrar dos descripciones para el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="066cb-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="066cb-109">La primera descripción es una breve descripción a la que se hace referencia como Sinopsis.</span><span class="sxs-lookup"><span data-stu-id="066cb-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="066cb-110">La segunda Descripción es una descripción más detallada que se describe en [Agregar la descripción detallada a un tema de ayuda de cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="066cb-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="066cb-111">Ambas descripciones deben escribirse en un solo párrafo.</span><span class="sxs-lookup"><span data-stu-id="066cb-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="066cb-112">En el Resumen, no repita el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="066cb-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="066cb-113">Informar al usuario de que el cmdlet Get-Server obtiene un servidor es breve, pero no es informativo.</span><span class="sxs-lookup"><span data-stu-id="066cb-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="066cb-114">En su lugar, use sinónimos y agregue detalles a la descripción.</span><span class="sxs-lookup"><span data-stu-id="066cb-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="066cb-115">Ejemplo: "obtiene un objeto que representa un equipo local o remoto".</span><span class="sxs-lookup"><span data-stu-id="066cb-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="066cb-116">Use verbos simples como "Get", "Create" y "Change" en el resumen.</span><span class="sxs-lookup"><span data-stu-id="066cb-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="066cb-117">Evite el uso de "SET" porque es impreciso y se decoran palabras como "Modify".</span><span class="sxs-lookup"><span data-stu-id="066cb-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="066cb-118">Ejemplo: "obtiene información sobre la firma Authenticode en un archivo".</span><span class="sxs-lookup"><span data-stu-id="066cb-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="066cb-119">Escriba en voz activa.</span><span class="sxs-lookup"><span data-stu-id="066cb-119">Write in active voice.</span></span> <span data-ttu-id="066cb-120">Por ejemplo, "usar el objeto TimeSpan..." es mucho más claro que "el objeto TimeSpan se puede usar para..."</span><span class="sxs-lookup"><span data-stu-id="066cb-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="066cb-121">Evite el verbo "Mostrar" al describir los cmdlets que obtienen objetos.</span><span class="sxs-lookup"><span data-stu-id="066cb-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="066cb-122">Aunque Windows PowerShell muestra los datos de los cmdlets, es importante introducir a los usuarios en el concepto de que el cmdlet devuelva .NET Framework objetos cuyos datos no se puedan mostrar.</span><span class="sxs-lookup"><span data-stu-id="066cb-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="066cb-123">Si resalta la pantalla, es posible que el usuario no tenga en cuenta que el cmdlet puede haber devuelto muchas otras propiedades y métodos útiles que no se muestran.</span><span class="sxs-lookup"><span data-stu-id="066cb-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="066cb-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="066cb-124">See Also</span></span>

 [<span data-ttu-id="066cb-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="066cb-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)