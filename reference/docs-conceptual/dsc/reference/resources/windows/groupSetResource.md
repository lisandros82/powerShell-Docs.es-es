---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
description: Proporciona un mecanismo para administrar grupos locales en el nodo de destino.
title: Recurso GroupSet de DSC
ms.openlocfilehash: d36274741b2c96a0852f384ccf5d187ac8d27131
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953182"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="00533-104">Recurso GroupSet de DSC</span><span class="sxs-lookup"><span data-stu-id="00533-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="00533-105">Se aplica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="00533-105">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="00533-106">El recurso **GroupSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar grupos locales en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="00533-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="00533-107">Este es un [recurso compuesto](../../../resources/authoringResourceComposite.md) que llama el [recurso de grupo](groupResource.md) de cada uno de los grupos que se especifican en el parámetro `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="00533-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="00533-108">Utilice este recurso cuando desee agregar o quitar la misma lista de miembros de más de un grupo, quitar más de un grupo o agregar más de un grupo con la misma lista de miembros.</span><span class="sxs-lookup"><span data-stu-id="00533-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="00533-109">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="00533-109">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="00533-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="00533-110">Properties</span></span>

|<span data-ttu-id="00533-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="00533-111">Property</span></span> |<span data-ttu-id="00533-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="00533-112">Description</span></span> |
|---|---|
|<span data-ttu-id="00533-113">NombreDeGrupo</span><span class="sxs-lookup"><span data-stu-id="00533-113">GroupName</span></span> |<span data-ttu-id="00533-114">Los nombres de los grupos para los que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="00533-114">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="00533-115">Miembros</span><span class="sxs-lookup"><span data-stu-id="00533-115">Members</span></span> |<span data-ttu-id="00533-116">Use esta propiedad para reemplazar la pertenencia al grupo actual con los miembros especificados.</span><span class="sxs-lookup"><span data-stu-id="00533-116">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="00533-117">El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="00533-117">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="00533-118">Si establece esta propiedad en una configuración, no use las propiedades **MembersToExclude** ni **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="00533-118">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="00533-119">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="00533-119">Doing so will generate an error.</span></span> |
|<span data-ttu-id="00533-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="00533-120">Description</span></span> |<span data-ttu-id="00533-121">La descripción del grupo.</span><span class="sxs-lookup"><span data-stu-id="00533-121">The description of the group.</span></span> |
|<span data-ttu-id="00533-122">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="00533-122">MembersToInclude</span></span> |<span data-ttu-id="00533-123">Use esta propiedad para agregar miembros a la pertenencia existente al grupo.</span><span class="sxs-lookup"><span data-stu-id="00533-123">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="00533-124">El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="00533-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="00533-125">Si establece esta propiedad en una configuración, no use la propiedad **Members**.</span><span class="sxs-lookup"><span data-stu-id="00533-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="00533-126">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="00533-126">Doing so will generate an error.</span></span> |
|<span data-ttu-id="00533-127">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="00533-127">MembersToExclude</span></span> |<span data-ttu-id="00533-128">Use esta propiedad para quitar a los miembros de la pertenencia existente de los grupos.</span><span class="sxs-lookup"><span data-stu-id="00533-128">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="00533-129">El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="00533-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="00533-130">Si establece esta propiedad en una configuración, no use la propiedad **Members**.</span><span class="sxs-lookup"><span data-stu-id="00533-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="00533-131">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="00533-131">Doing so will generate an error.</span></span> |
|<span data-ttu-id="00533-132">Credential</span><span class="sxs-lookup"><span data-stu-id="00533-132">Credential</span></span> |<span data-ttu-id="00533-133">Las credenciales necesarias para acceder a los recursos remotos.</span><span class="sxs-lookup"><span data-stu-id="00533-133">The credentials required to access remote resources.</span></span> <span data-ttu-id="00533-134">Esta cuenta debe tener los permisos adecuados de Active Directory para agregar todas las cuentas no locales al grupo; en caso contrario, se producirá un error.</span><span class="sxs-lookup"><span data-stu-id="00533-134">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="00533-135">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="00533-135">Common properties</span></span>

|<span data-ttu-id="00533-136">Propiedad</span><span class="sxs-lookup"><span data-stu-id="00533-136">Property</span></span> |<span data-ttu-id="00533-137">Descripción</span><span class="sxs-lookup"><span data-stu-id="00533-137">Description</span></span> |
|---|---|
|<span data-ttu-id="00533-138">DependsOn</span><span class="sxs-lookup"><span data-stu-id="00533-138">DependsOn</span></span> |<span data-ttu-id="00533-139">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="00533-139">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="00533-140">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="00533-140">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="00533-141">Ensure</span><span class="sxs-lookup"><span data-stu-id="00533-141">Ensure</span></span> |<span data-ttu-id="00533-142">Indica si existen los grupos.</span><span class="sxs-lookup"><span data-stu-id="00533-142">Indicates whether the groups exist.</span></span> <span data-ttu-id="00533-143">Establezca esta propiedad en **Absent** para asegurarse de que los grupos no existan.</span><span class="sxs-lookup"><span data-stu-id="00533-143">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="00533-144">Si se establece en **Present**, se garantiza que los grupos existan.</span><span class="sxs-lookup"><span data-stu-id="00533-144">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="00533-145">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="00533-145">The default value is **Present**.</span></span> |
|<span data-ttu-id="00533-146">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="00533-146">PsDscRunAsCredential</span></span> |<span data-ttu-id="00533-147">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="00533-147">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="00533-148">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="00533-148">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="00533-149">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="00533-149">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="00533-150">Ejemplo 1: Cómo asegurarse de que existen grupos</span><span class="sxs-lookup"><span data-stu-id="00533-150">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="00533-151">En el ejemplo siguiente se muestra cómo asegurarse de que existen dos grupos denominados "myGroup" y "myOtherGroup".</span><span class="sxs-lookup"><span data-stu-id="00533-151">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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
> <span data-ttu-id="00533-152">En este ejemplo se usan las credenciales de texto sin formato por su sencillez.</span><span class="sxs-lookup"><span data-stu-id="00533-152">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="00533-153">Para más información sobre el cifrado de credenciales en el archivo MOF de configuración, consulte [Proteger el archivo MOF](../../../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="00533-153">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>