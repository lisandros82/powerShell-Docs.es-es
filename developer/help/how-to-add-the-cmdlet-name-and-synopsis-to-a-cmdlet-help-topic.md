---
title: Cómo agregar el nombre de Cmdlet y Sinopsis a un tema de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083347"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="977aa-102">Cómo agregar el nombre del cmdlet y la sinopsis a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="977aa-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="977aa-103">En esta sección se describe cómo agregar contenido que se muestra en las secciones de nombre y una sinopsis de la Ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="977aa-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="977aa-104">En el archivo de ayuda, este contenido se agrega al nodo de comando para cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="977aa-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="977aa-105">Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll Help.xml ubicado en el directorio de instalación de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="977aa-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="977aa-106">Por ejemplo, el archivo Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenido para varios de los cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="977aa-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="977aa-107">Para agregar el nombre del Cmdlet y una sinopsis</span><span class="sxs-lookup"><span data-stu-id="977aa-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="977aa-108">La Ayuda del cmdlet puede mostrar dos descripciones del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="977aa-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="977aa-109">La descripción de la primera es una breve descripción que se conoce como la sinopsis.</span><span class="sxs-lookup"><span data-stu-id="977aa-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="977aa-110">La descripción de la segunda es una descripción más detallada que se describe en [agregar la descripción detallada para un tema de Ayuda de Cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="977aa-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="977aa-111">Estas descripciones se deben escribir como un único párrafo.</span><span class="sxs-lookup"><span data-stu-id="977aa-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="977aa-112">En la sinopsis no repetir el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="977aa-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="977aa-113">Para informar al usuario que el cmdlet Get-Server obtiene un servidor es breve, pero no informativo.</span><span class="sxs-lookup"><span data-stu-id="977aa-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="977aa-114">En su lugar, utilizar sinónimos y agregar detalles a la descripción.</span><span class="sxs-lookup"><span data-stu-id="977aa-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="977aa-115">Ejemplo: "Obtiene un objeto que representa un equipo local o remoto."</span><span class="sxs-lookup"><span data-stu-id="977aa-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="977aa-116">Usar los verbos simple como "get", "crear" y "cambiar" en la sinopsis.</span><span class="sxs-lookup"><span data-stu-id="977aa-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="977aa-117">Evite el uso de "set" porque es imprecisa y elegantes palabras como "modificación".</span><span class="sxs-lookup"><span data-stu-id="977aa-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="977aa-118">Ejemplo: "Obtiene información sobre la firma Authenticode en un archivo".</span><span class="sxs-lookup"><span data-stu-id="977aa-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="977aa-119">Escribir en voz activa.</span><span class="sxs-lookup"><span data-stu-id="977aa-119">Write in active voice.</span></span> <span data-ttu-id="977aa-120">Por ejemplo, "usar el objeto TimeSpan..." es mucho más claro que "el objeto TimeSpan se puede usar para..."</span><span class="sxs-lookup"><span data-stu-id="977aa-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="977aa-121">Evite el verbo "display" al describir los cmdlets que se obtienen los objetos.</span><span class="sxs-lookup"><span data-stu-id="977aa-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="977aa-122">Aunque Windows PowerShell muestra los datos de cmdlet, es importante presentar el concepto de que el cmdlet devuelve objetos de .NET Framework cuyos datos no pueden mostrarse a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="977aa-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="977aa-123">Si hacer hincapié en la pantalla, el usuario podría no darse cuenta que el cmdlet devuelto muchas otras propiedades y métodos útiles que no se muestran.</span><span class="sxs-lookup"><span data-stu-id="977aa-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="977aa-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="977aa-124">See Also</span></span>

 [<span data-ttu-id="977aa-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="977aa-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)