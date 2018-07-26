---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso nxGroup de DSC para Linux
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093609"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="edcf5-103">Recurso nxGroup de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="edcf5-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="edcf5-104">El recurso **nxGroup** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar grupos locales en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="edcf5-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="edcf5-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="edcf5-105">Syntax</span></span>

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="edcf5-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="edcf5-106">Properties</span></span>

|  <span data-ttu-id="edcf5-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="edcf5-107">Property</span></span> |  <span data-ttu-id="edcf5-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="edcf5-108">Description</span></span> |
|---|---|
| <span data-ttu-id="edcf5-109">NombreDeGrupo</span><span class="sxs-lookup"><span data-stu-id="edcf5-109">GroupName</span></span>| <span data-ttu-id="edcf5-110">Especifica el nombre del grupo para el que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="edcf5-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="edcf5-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="edcf5-111">Ensure</span></span>| <span data-ttu-id="edcf5-112">Determina si se debe comprobar si existe el grupo.</span><span class="sxs-lookup"><span data-stu-id="edcf5-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="edcf5-113">Establezca esta propiedad en "Present" para asegurarse de que el grupo exista.</span><span class="sxs-lookup"><span data-stu-id="edcf5-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="edcf5-114">Establézcala en "Absent" para asegurarse de que el grupo no exista.</span><span class="sxs-lookup"><span data-stu-id="edcf5-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="edcf5-115">El valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="edcf5-115">The default value is "Present".</span></span>|
| <span data-ttu-id="edcf5-116">Miembros</span><span class="sxs-lookup"><span data-stu-id="edcf5-116">Members</span></span>| <span data-ttu-id="edcf5-117">Especifica a los miembros que forman el grupo.</span><span class="sxs-lookup"><span data-stu-id="edcf5-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="edcf5-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="edcf5-118">MembersToInclude</span></span>| <span data-ttu-id="edcf5-119">Especifica los usuarios que quiera garantizar que sean miembros del grupo.</span><span class="sxs-lookup"><span data-stu-id="edcf5-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="edcf5-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="edcf5-120">MembersToExclude</span></span>| <span data-ttu-id="edcf5-121">Especifica los usuarios que quiera garantizar que no sean miembros del grupo.</span><span class="sxs-lookup"><span data-stu-id="edcf5-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="edcf5-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="edcf5-122">PreferredGroupID</span></span>| <span data-ttu-id="edcf5-123">Establece el identificador de grupo en el valor proporcionado, si es posible.</span><span class="sxs-lookup"><span data-stu-id="edcf5-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="edcf5-124">Si el identificador de grupo está actualmente en uso, se utiliza el siguiente identificador de grupo disponible.</span><span class="sxs-lookup"><span data-stu-id="edcf5-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="edcf5-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="edcf5-125">DependsOn</span></span> | <span data-ttu-id="edcf5-126">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="edcf5-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="edcf5-127">Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="edcf5-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="edcf5-128">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edcf5-128">Example</span></span>

<span data-ttu-id="edcf5-129">El ejemplo siguiente se asegura de que el usuario "monuser" exista y de que sea un miembro del grupo "DBusers".</span><span class="sxs-lookup"><span data-stu-id="edcf5-129">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```