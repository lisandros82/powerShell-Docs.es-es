---
title: Cómo agregar una descripción del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862601"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="56bc4-102">Cómo agregar una descripción del cmdlet</span><span class="sxs-lookup"><span data-stu-id="56bc4-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="56bc4-103">En esta sección se describe cómo agregar contenido que se muestra en la sección de descripción de la Ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56bc4-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="56bc4-104">En el archivo de ayuda, este contenido se agrega al nodo de comando para cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56bc4-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="56bc4-105">Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll Help.xml ubicado en el directorio de instalación de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56bc4-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="56bc4-106">Por ejemplo, el archivo Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenido para varios de los cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56bc4-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="56bc4-107">Para agregar una descripción</span><span class="sxs-lookup"><span data-stu-id="56bc4-107">To Add a Description</span></span>

- <span data-ttu-id="56bc4-108">Empiece por explicar las características básicas del cmdlet en más detalle.</span><span class="sxs-lookup"><span data-stu-id="56bc4-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="56bc4-109">En muchos casos, puede explicar los términos usados en el nombre del cmdlet e ilustrar conceptos familiarizados con un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="56bc4-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="56bc4-110">Por ejemplo, si el cmdlet anexa datos a un archivo, explique que agrega datos al final de un archivo existente.</span><span class="sxs-lookup"><span data-stu-id="56bc4-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="56bc4-111">Para buscar todas las características del cmdlet, revise la lista de parámetros.</span><span class="sxs-lookup"><span data-stu-id="56bc4-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="56bc4-112">Describir la función principal del cmdlet y, a continuación, incluir otras funciones y características.</span><span class="sxs-lookup"><span data-stu-id="56bc4-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="56bc4-113">Por ejemplo, si es la función principal del cmdlet cambiar una propiedad, pero el cmdlet puede cambiar todas las propiedades, indicarlo en la descripción detallada.</span><span class="sxs-lookup"><span data-stu-id="56bc4-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="56bc4-114">Si los parámetros de cmdlet permiten a los usuarios solicitan información de maneras diferentes, se explica.</span><span class="sxs-lookup"><span data-stu-id="56bc4-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="56bc4-115">Incluir información sobre la forma que los usuarios pueden usar el cmdlet, además de los usos obvios.</span><span class="sxs-lookup"><span data-stu-id="56bc4-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="56bc4-116">Por ejemplo, puede utilizar el objeto que el `Get-Host` cmdlet recupera para cambiar el color del texto en la ventana de comandos de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56bc4-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="56bc4-117">Ejemplo:  "El `Get-Acl` Obtiene objetos que representan el descriptor de seguridad de un archivo o recurso.</span><span class="sxs-lookup"><span data-stu-id="56bc4-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="56bc4-118">El descriptor de seguridad contiene las listas de control de acceso (ACL) del recurso.</span><span class="sxs-lookup"><span data-stu-id="56bc4-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="56bc4-119">La ACL especifica los permisos que los usuarios y grupos de usuarios tienen acceso al recurso."</span><span class="sxs-lookup"><span data-stu-id="56bc4-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="56bc4-120">La descripción detallada debe describir el cmdlet, pero deben describir conceptos que usa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56bc4-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="56bc4-121">Coloque las definiciones de concepto en notas adicionales.</span><span class="sxs-lookup"><span data-stu-id="56bc4-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="56bc4-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="56bc4-122">See Also</span></span>

[<span data-ttu-id="56bc4-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="56bc4-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
