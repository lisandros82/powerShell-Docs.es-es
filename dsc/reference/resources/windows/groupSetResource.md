---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
description: Proporciona un mecanismo para administrar grupos locales en el nodo de destino.
title: Recurso GroupSet de DSC
ms.openlocfilehash: afe4c4d33ac5620c411481e93d76a1f90c26deb9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048046"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="75856-104">Recurso GroupSet de DSC</span><span class="sxs-lookup"><span data-stu-id="75856-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="75856-105">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="75856-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="75856-106">El recurso **GroupSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar grupos locales en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="75856-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="75856-107">Este es un [recurso compuesto](../../../resources/authoringResourceComposite.md) que llama el [recurso de grupo](groupResource.md) de cada uno de los grupos que se especifican en el parámetro `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="75856-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="75856-108">Utilice este recurso cuando desee agregar o quitar la misma lista de miembros de más de un grupo, quitar más de un grupo o agregar más de un grupo con la misma lista de miembros.</span><span class="sxs-lookup"><span data-stu-id="75856-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="75856-109">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="75856-109">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="75856-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="75856-110">Properties</span></span>

|  <span data-ttu-id="75856-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="75856-111">Property</span></span>  |  <span data-ttu-id="75856-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="75856-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="75856-113">NombreDeGrupo</span><span class="sxs-lookup"><span data-stu-id="75856-113">GroupName</span></span>| <span data-ttu-id="75856-114">Los nombres de los grupos para los que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="75856-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="75856-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="75856-115">MembersToExclude</span></span>| <span data-ttu-id="75856-116">Use esta propiedad para quitar a los miembros de la pertenencia existente de los grupos.</span><span class="sxs-lookup"><span data-stu-id="75856-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="75856-117">El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="75856-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="75856-118">Si establece esta propiedad en una configuración, no use la propiedad **Members**.</span><span class="sxs-lookup"><span data-stu-id="75856-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="75856-119">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="75856-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="75856-120">Credential</span><span class="sxs-lookup"><span data-stu-id="75856-120">Credential</span></span>| <span data-ttu-id="75856-121">Las credenciales necesarias para acceder a los recursos remotos.</span><span class="sxs-lookup"><span data-stu-id="75856-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="75856-122">**Nota**: Esta cuenta debe tener los permisos adecuados de Active Directory para agregar todas las cuentas no locales al grupo; en caso contrario, se producirá un error.</span><span class="sxs-lookup"><span data-stu-id="75856-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="75856-123">Ensure</span><span class="sxs-lookup"><span data-stu-id="75856-123">Ensure</span></span>| <span data-ttu-id="75856-124">Indica si existen los grupos.</span><span class="sxs-lookup"><span data-stu-id="75856-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="75856-125">Establezca esta propiedad en "Absent" para asegurarse de que los grupos no existan.</span><span class="sxs-lookup"><span data-stu-id="75856-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="75856-126">Si se establece en "Present" (el valor predeterminado), se garantiza que los grupos existan.</span><span class="sxs-lookup"><span data-stu-id="75856-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="75856-127">Miembros</span><span class="sxs-lookup"><span data-stu-id="75856-127">Members</span></span>| <span data-ttu-id="75856-128">Use esta propiedad para reemplazar la pertenencia al grupo actual con los miembros especificados.</span><span class="sxs-lookup"><span data-stu-id="75856-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="75856-129">El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="75856-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="75856-130">Si establece esta propiedad en una configuración, no use las propiedades **MembersToExclude** ni **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="75856-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="75856-131">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="75856-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="75856-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="75856-132">MembersToInclude</span></span>| <span data-ttu-id="75856-133">Use esta propiedad para agregar miembros a la pertenencia existente al grupo.</span><span class="sxs-lookup"><span data-stu-id="75856-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="75856-134">El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="75856-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="75856-135">Si establece esta propiedad en una configuración, no use la propiedad **Members**.</span><span class="sxs-lookup"><span data-stu-id="75856-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="75856-136">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="75856-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="75856-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="75856-137">DependsOn</span></span> | <span data-ttu-id="75856-138">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="75856-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="75856-139">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es \`DependsOn = "[ResourceType]ResourceName"\`\`.</span><span class="sxs-lookup"><span data-stu-id="75856-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="75856-140">Ejemplo 1: Grupos de seguridad de que están presentes</span><span class="sxs-lookup"><span data-stu-id="75856-140">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="75856-141">En el ejemplo siguiente se muestra cómo asegurarse de que existen dos grupos denominados "myGroup" y "myOtherGroup".</span><span class="sxs-lookup"><span data-stu-id="75856-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="75856-142">En este ejemplo se usan las credenciales de texto sin formato por su sencillez.</span><span class="sxs-lookup"><span data-stu-id="75856-142">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="75856-143">Para más información sobre el cifrado de credenciales en el archivo MOF de configuración, consulte [Proteger el archivo MOF](../../../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="75856-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
