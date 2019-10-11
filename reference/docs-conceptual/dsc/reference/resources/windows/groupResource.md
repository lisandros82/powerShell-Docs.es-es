---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Group
ms.openlocfilehash: 695a914683c6daff44dd2a6c94b6353acf881030
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954662"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="7f17b-103">Recurso de DSC Group</span><span class="sxs-lookup"><span data-stu-id="7f17b-103">DSC Group Resource</span></span>

> <span data-ttu-id="7f17b-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="7f17b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="7f17b-105">El recurso **Group** de Desired State Configuration (DSC) de Windows PowerShell ofrece un mecanismo para administrar grupos locales en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="7f17b-105">The **Group** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7f17b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7f17b-106">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="7f17b-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="7f17b-107">Properties</span></span>

|<span data-ttu-id="7f17b-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="7f17b-108">Property</span></span> |<span data-ttu-id="7f17b-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="7f17b-109">Description</span></span> |
|---|---|
|<span data-ttu-id="7f17b-110">NombreDeGrupo</span><span class="sxs-lookup"><span data-stu-id="7f17b-110">GroupName</span></span> |<span data-ttu-id="7f17b-111">El nombre del grupo para el que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="7f17b-111">The name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="7f17b-112">Credential</span><span class="sxs-lookup"><span data-stu-id="7f17b-112">Credential</span></span> |<span data-ttu-id="7f17b-113">Las credenciales necesarias para acceder a los recursos remotos.</span><span class="sxs-lookup"><span data-stu-id="7f17b-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="7f17b-114">Esta cuenta debe tener los permisos adecuados de Active Directory para agregar todas las cuentas no locales al grupo; en caso contrario, se producirá un error al ejecutar la configuración en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="7f17b-114">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
|<span data-ttu-id="7f17b-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="7f17b-115">Description</span></span> |<span data-ttu-id="7f17b-116">La descripción del grupo.</span><span class="sxs-lookup"><span data-stu-id="7f17b-116">The description of the group.</span></span> |
|<span data-ttu-id="7f17b-117">Miembros</span><span class="sxs-lookup"><span data-stu-id="7f17b-117">Members</span></span> |<span data-ttu-id="7f17b-118">Use esta propiedad para reemplazar la pertenencia al grupo actual con los miembros especificados.</span><span class="sxs-lookup"><span data-stu-id="7f17b-118">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="7f17b-119">El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="7f17b-119">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="7f17b-120">Si establece esta propiedad en una configuración, no use las propiedades **MembersToExclude** ni **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="7f17b-120">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="7f17b-121">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="7f17b-121">Doing so generates an error.</span></span> |
|<span data-ttu-id="7f17b-122">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="7f17b-122">MembersToExclude</span></span> |<span data-ttu-id="7f17b-123">Use esta propiedad para quitar a los miembros de la pertenencia existente del grupo.</span><span class="sxs-lookup"><span data-stu-id="7f17b-123">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="7f17b-124">El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="7f17b-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="7f17b-125">Si establece esta propiedad en una configuración, no use la propiedad **Members**.</span><span class="sxs-lookup"><span data-stu-id="7f17b-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="7f17b-126">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="7f17b-126">Doing so generates an error.</span></span> |
|<span data-ttu-id="7f17b-127">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="7f17b-127">MembersToInclude</span></span> |<span data-ttu-id="7f17b-128">Use esta propiedad para agregar miembros a la pertenencia existente al grupo.</span><span class="sxs-lookup"><span data-stu-id="7f17b-128">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="7f17b-129">El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="7f17b-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="7f17b-130">Si establece esta propiedad en una configuración, no use la propiedad **Members**.</span><span class="sxs-lookup"><span data-stu-id="7f17b-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="7f17b-131">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="7f17b-131">Doing so will generate an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7f17b-132">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="7f17b-132">Common properties</span></span>

|<span data-ttu-id="7f17b-133">Propiedad</span><span class="sxs-lookup"><span data-stu-id="7f17b-133">Property</span></span> |<span data-ttu-id="7f17b-134">Descripción</span><span class="sxs-lookup"><span data-stu-id="7f17b-134">Description</span></span> |
|---|---|
|<span data-ttu-id="7f17b-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7f17b-135">DependsOn</span></span> |<span data-ttu-id="7f17b-136">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="7f17b-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7f17b-137">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7f17b-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7f17b-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="7f17b-138">Ensure</span></span> |<span data-ttu-id="7f17b-139">Indica si existe el grupo.</span><span class="sxs-lookup"><span data-stu-id="7f17b-139">Indicates if the group exists.</span></span> <span data-ttu-id="7f17b-140">Establezca esta propiedad en **Absent** para asegurarse de que el grupo no exista.</span><span class="sxs-lookup"><span data-stu-id="7f17b-140">Set this property to **Absent** to ensure that the group does not exist.</span></span> <span data-ttu-id="7f17b-141">Si se establece en **Present**, se garantiza que el grupo exista.</span><span class="sxs-lookup"><span data-stu-id="7f17b-141">Setting it to **Present** ensures that the group exists.</span></span> <span data-ttu-id="7f17b-142">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="7f17b-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="7f17b-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7f17b-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="7f17b-144">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="7f17b-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7f17b-145">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="7f17b-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7f17b-146">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="7f17b-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensure-group-is-not-present"></a><span data-ttu-id="7f17b-147">Ejemplo 1: Asegurarse de que el grupo no está presente</span><span class="sxs-lookup"><span data-stu-id="7f17b-147">Example 1: Ensure group is not present</span></span>

<span data-ttu-id="7f17b-148">En el ejemplo siguiente se muestra cómo asegurarse de que no existe un grupo denominado "TestGroup".</span><span class="sxs-lookup"><span data-stu-id="7f17b-148">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a><span data-ttu-id="7f17b-149">Ejemplo 2: Agregar un usuario de dominio a un grupo local</span><span class="sxs-lookup"><span data-stu-id="7f17b-149">Example 2: Add domain user to local group</span></span>

<span data-ttu-id="7f17b-150">En el ejemplo siguiente se muestra cómo agregar un usuario de Active Directory al grupo de administradores local como parte de una compilación de prácticas en varias máquinas que ya usan un PSCredential para la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="7f17b-150">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Administrator account.</span></span> <span data-ttu-id="7f17b-151">Puesto que también se usa para la cuenta de administrador del dominio (después de la promoción del dominio), necesitamos convertir este PSCredential existente en una credencial apta para dominio.</span><span class="sxs-lookup"><span data-stu-id="7f17b-151">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span> <span data-ttu-id="7f17b-152">Luego podemos agregar un usuario de dominio al grupo de administradores local en el servidor miembro.</span><span class="sxs-lookup"><span data-stu-id="7f17b-152">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="7f17b-153">Ejemplo 3</span><span class="sxs-lookup"><span data-stu-id="7f17b-153">Example 3</span></span>

<span data-ttu-id="7f17b-154">En el ejemplo siguiente se muestra cómo asegurarse de un grupo local, TigerTeamAdmins, en el servidor TigerTeamSource.Contoso.Com no contiene una cuenta de dominio en particular, Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="7f17b-154">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```