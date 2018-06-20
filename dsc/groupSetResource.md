---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
description: Proporciona un mecanismo para administrar grupos locales en el nodo de destino.
title: Recurso GroupSet de DSC
ms.openlocfilehash: 3d6fdcaef6053964d3fb3b709a5263d291a7c840
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222360"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="e545b-104">Recurso GroupSet de DSC</span><span class="sxs-lookup"><span data-stu-id="e545b-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="e545b-105">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e545b-105">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="e545b-106">El recurso **GroupSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar grupos locales en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="e545b-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="e545b-107">Este es un [recurso compuesto](authoringResourceComposite.md) que llama el [recurso de grupo](groupResource.md) de cada uno de los grupos que se especifican en el parámetro `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="e545b-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="e545b-108">Utilice este recurso cuando desee agregar o quitar la misma lista de miembros de más de un grupo, quitar más de un grupo o agregar más de un grupo con la misma lista de miembros.</span><span class="sxs-lookup"><span data-stu-id="e545b-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

##<a name="syntax"></a><span data-ttu-id="e545b-109">Sintaxis##</span><span class="sxs-lookup"><span data-stu-id="e545b-109">Syntax##</span></span>
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

## <a name="properties"></a><span data-ttu-id="e545b-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="e545b-110">Properties</span></span>

|  <span data-ttu-id="e545b-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="e545b-111">Property</span></span>  |  <span data-ttu-id="e545b-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="e545b-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="e545b-113">NombreDeGrupo</span><span class="sxs-lookup"><span data-stu-id="e545b-113">GroupName</span></span>| <span data-ttu-id="e545b-114">Los nombres de los grupos para los que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="e545b-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="e545b-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="e545b-115">MembersToExclude</span></span>| <span data-ttu-id="e545b-116">Use esta propiedad para quitar a los miembros de la pertenencia existente de los grupos.</span><span class="sxs-lookup"><span data-stu-id="e545b-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="e545b-117">El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="e545b-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e545b-118">Si establece esta propiedad en una configuración, no use la propiedad **Members**.</span><span class="sxs-lookup"><span data-stu-id="e545b-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="e545b-119">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="e545b-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="e545b-120">Credential</span><span class="sxs-lookup"><span data-stu-id="e545b-120">Credential</span></span>| <span data-ttu-id="e545b-121">Las credenciales necesarias para acceder a los recursos remotos.</span><span class="sxs-lookup"><span data-stu-id="e545b-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="e545b-122">**Nota**: Esta cuenta debe tener los permisos adecuados de Active Directory para agregar todas las cuentas no locales al grupo; en caso contrario, se producirá un error.</span><span class="sxs-lookup"><span data-stu-id="e545b-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="e545b-123">Ensure</span><span class="sxs-lookup"><span data-stu-id="e545b-123">Ensure</span></span>| <span data-ttu-id="e545b-124">Indica si existen los grupos.</span><span class="sxs-lookup"><span data-stu-id="e545b-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="e545b-125">Establezca esta propiedad en "Absent" para asegurarse de que los grupos no existan.</span><span class="sxs-lookup"><span data-stu-id="e545b-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="e545b-126">Si se establece en "Present" (el valor predeterminado), se garantiza que los grupos existan.</span><span class="sxs-lookup"><span data-stu-id="e545b-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="e545b-127">Miembros</span><span class="sxs-lookup"><span data-stu-id="e545b-127">Members</span></span>| <span data-ttu-id="e545b-128">Use esta propiedad para reemplazar la pertenencia al grupo actual con los miembros especificados.</span><span class="sxs-lookup"><span data-stu-id="e545b-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="e545b-129">El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="e545b-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e545b-130">Si establece esta propiedad en una configuración, no use las propiedades **MembersToExclude** ni **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="e545b-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="e545b-131">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="e545b-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="e545b-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="e545b-132">MembersToInclude</span></span>| <span data-ttu-id="e545b-133">Use esta propiedad para agregar miembros a la pertenencia existente al grupo.</span><span class="sxs-lookup"><span data-stu-id="e545b-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="e545b-134">El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="e545b-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e545b-135">Si establece esta propiedad en una configuración, no use la propiedad **Members**.</span><span class="sxs-lookup"><span data-stu-id="e545b-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="e545b-136">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="e545b-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="e545b-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e545b-137">DependsOn</span></span> | <span data-ttu-id="e545b-138">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="e545b-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e545b-139">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es \`DependsOn = "[ResourceType]ResourceName"\`\`.</span><span class="sxs-lookup"><span data-stu-id="e545b-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="e545b-140">Ejemplo 1</span><span class="sxs-lookup"><span data-stu-id="e545b-140">Example 1</span></span>

<span data-ttu-id="e545b-141">En el ejemplo siguiente se muestra cómo asegurarse de que existen dos grupos denominados "myGroup" y "myOtherGroup".</span><span class="sxs-lookup"><span data-stu-id="e545b-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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

><span data-ttu-id="e545b-142">**Nota:** este ejemplo usa las credenciales de texto sin formato por su sencillez.</span><span class="sxs-lookup"><span data-stu-id="e545b-142">**Note:** This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="e545b-143">Para más información sobre el cifrado de credenciales en el archivo MOF de configuración, consulte [Proteger el archivo MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="e545b-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>