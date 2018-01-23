---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso nxGroup de DSC para Linux
ms.openlocfilehash: bc01f6ae5ed61aff63958fe55f30d82f9b81b2b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="94c85-103">Recurso nxGroup de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="94c85-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="94c85-104">El recurso **nxGroup** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar grupos locales en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="94c85-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="94c85-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="94c85-105">Syntax</span></span>

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a><span data-ttu-id="94c85-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="94c85-106">Properties</span></span>

|  <span data-ttu-id="94c85-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="94c85-107">Property</span></span> |  <span data-ttu-id="94c85-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="94c85-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="94c85-109">NombreDeGrupo</span><span class="sxs-lookup"><span data-stu-id="94c85-109">GroupName</span></span>| <span data-ttu-id="94c85-110">Especifica el nombre del grupo para el que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="94c85-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="94c85-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="94c85-111">Ensure</span></span>| <span data-ttu-id="94c85-112">Determina si se debe comprobar si existe el grupo.</span><span class="sxs-lookup"><span data-stu-id="94c85-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="94c85-113">Establezca esta propiedad en "Present" para asegurarse de que el grupo exista.</span><span class="sxs-lookup"><span data-stu-id="94c85-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="94c85-114">Establézcala en "Absent" para asegurarse de que el grupo no exista.</span><span class="sxs-lookup"><span data-stu-id="94c85-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="94c85-115">El valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="94c85-115">The default value is "Present".</span></span>| 
| <span data-ttu-id="94c85-116">Miembros</span><span class="sxs-lookup"><span data-stu-id="94c85-116">Members</span></span>| <span data-ttu-id="94c85-117">Especifica a los miembros que forman el grupo.</span><span class="sxs-lookup"><span data-stu-id="94c85-117">Specifies the members that form the group.</span></span>| 
| <span data-ttu-id="94c85-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="94c85-118">MembersToInclude</span></span>| <span data-ttu-id="94c85-119">Especifica los usuarios que quiera garantizar que sean miembros del grupo.</span><span class="sxs-lookup"><span data-stu-id="94c85-119">Specifies the users who you want to ensure are members of the group.</span></span>| 
| <span data-ttu-id="94c85-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="94c85-120">MembersToExclude</span></span>| <span data-ttu-id="94c85-121">Especifica los usuarios que quiera garantizar que no sean miembros del grupo.</span><span class="sxs-lookup"><span data-stu-id="94c85-121">Specifies the users who you want to ensure are not members of the group.</span></span>| 
| <span data-ttu-id="94c85-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="94c85-122">PreferredGroupID</span></span>| <span data-ttu-id="94c85-123">Establece el identificador de grupo en el valor proporcionado, si es posible.</span><span class="sxs-lookup"><span data-stu-id="94c85-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="94c85-124">Si el identificador de grupo está actualmente en uso, se utiliza el siguiente identificador de grupo disponible.</span><span class="sxs-lookup"><span data-stu-id="94c85-124">If the group id is currently in use, the next available group id is used.</span></span>| 
| <span data-ttu-id="94c85-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="94c85-125">DependsOn</span></span> | <span data-ttu-id="94c85-126">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="94c85-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="94c85-127">Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="94c85-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="94c85-128">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="94c85-128">Example</span></span>

<span data-ttu-id="94c85-129">El ejemplo siguiente se asegura de que el usuario "monuser" exista y de que sea un miembro del grupo "DBusers".</span><span class="sxs-lookup"><span data-stu-id="94c85-129">The following example ensures that the user “monuser” exists and is a member of the group "DBusers".</span></span>

```
Import-DSCResource -Module nx 

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```

