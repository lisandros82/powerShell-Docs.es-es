---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Group
ms.openlocfilehash: 6fb6c5f9593687d7204ff31fddd9bca978ed2707
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-group-resource"></a><span data-ttu-id="a91fe-103">Recurso de DSC Group</span><span class="sxs-lookup"><span data-stu-id="a91fe-103">DSC Group Resource</span></span>

> <span data-ttu-id="a91fe-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a91fe-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a91fe-105">El recurso Group de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar grupos locales en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="a91fe-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a91fe-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a91fe-106">Syntax</span></span>
```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="a91fe-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a91fe-107">Properties</span></span>

|  <span data-ttu-id="a91fe-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="a91fe-108">Property</span></span>  |  <span data-ttu-id="a91fe-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="a91fe-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="a91fe-110">NombreDeGrupo</span><span class="sxs-lookup"><span data-stu-id="a91fe-110">GroupName</span></span>| <span data-ttu-id="a91fe-111">El nombre del grupo para el que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="a91fe-111">The name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="a91fe-112">Credential</span><span class="sxs-lookup"><span data-stu-id="a91fe-112">Credential</span></span>| <span data-ttu-id="a91fe-113">Las credenciales necesarias para acceder a los recursos remotos.</span><span class="sxs-lookup"><span data-stu-id="a91fe-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="a91fe-114">**Nota**: Esta cuenta debe tener los permisos adecuados de Active Directory para agregar todas las cuentas no locales al grupo; en caso contrario, se produce un error cuando la configuración se ejecuta en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="a91fe-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>  
| <span data-ttu-id="a91fe-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="a91fe-115">Description</span></span>| <span data-ttu-id="a91fe-116">La descripción del grupo.</span><span class="sxs-lookup"><span data-stu-id="a91fe-116">The description of the group.</span></span>| 
| <span data-ttu-id="a91fe-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="a91fe-117">Ensure</span></span>| <span data-ttu-id="a91fe-118">Indica si existe el grupo.</span><span class="sxs-lookup"><span data-stu-id="a91fe-118">Indicates if the group exists.</span></span> <span data-ttu-id="a91fe-119">Establezca esta propiedad en "Absent" para asegurarse de que el grupo no exista.</span><span class="sxs-lookup"><span data-stu-id="a91fe-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="a91fe-120">Si se establece en "Present" (el valor predeterminado), se garantiza que el grupo exista.</span><span class="sxs-lookup"><span data-stu-id="a91fe-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>| 
| <span data-ttu-id="a91fe-121">Miembros</span><span class="sxs-lookup"><span data-stu-id="a91fe-121">Members</span></span>| <span data-ttu-id="a91fe-122">Use esta propiedad para reemplazar la pertenencia al grupo actual con los miembros especificados.</span><span class="sxs-lookup"><span data-stu-id="a91fe-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="a91fe-123">El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="a91fe-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="a91fe-124">Si establece esta propiedad en una configuración, no use las propiedades **MembersToExclude** ni **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="a91fe-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="a91fe-125">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="a91fe-125">Doing so generates an error.</span></span>| 
| <span data-ttu-id="a91fe-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="a91fe-126">MembersToExclude</span></span>| <span data-ttu-id="a91fe-127">Use esta propiedad para quitar a los miembros de la pertenencia existente del grupo.</span><span class="sxs-lookup"><span data-stu-id="a91fe-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="a91fe-128">El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="a91fe-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="a91fe-129">Si establece esta propiedad en una configuración, no use la propiedad **Members**.</span><span class="sxs-lookup"><span data-stu-id="a91fe-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="a91fe-130">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="a91fe-130">Doing so generates an error.</span></span>| 
| <span data-ttu-id="a91fe-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="a91fe-131">MembersToInclude</span></span>| <span data-ttu-id="a91fe-132">Use esta propiedad para agregar miembros a la pertenencia existente al grupo.</span><span class="sxs-lookup"><span data-stu-id="a91fe-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="a91fe-133">El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="a91fe-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="a91fe-134">Si establece esta propiedad en una configuración, no use la propiedad **Members**.</span><span class="sxs-lookup"><span data-stu-id="a91fe-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="a91fe-135">Si lo hace, se generará un error.</span><span class="sxs-lookup"><span data-stu-id="a91fe-135">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="a91fe-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a91fe-136">DependsOn</span></span> | <span data-ttu-id="a91fe-137">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="a91fe-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a91fe-138">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`\`.</span><span class="sxs-lookup"><span data-stu-id="a91fe-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example-1"></a><span data-ttu-id="a91fe-139">Ejemplo 1</span><span class="sxs-lookup"><span data-stu-id="a91fe-139">Example 1</span></span>

<span data-ttu-id="a91fe-140">En el ejemplo siguiente se muestra cómo asegurarse de que no existe un grupo denominado "TestGroup".</span><span class="sxs-lookup"><span data-stu-id="a91fe-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span> 

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## <a name="example-2"></a><span data-ttu-id="a91fe-141">Ejemplo 2</span><span class="sxs-lookup"><span data-stu-id="a91fe-141">Example 2</span></span>
<span data-ttu-id="a91fe-142">En el ejemplo siguiente se muestra cómo agregar un usuario de Active Directory al grupo de administradores local como parte de una compilación de prácticas en varias máquinas que ya usan un PSCredential para la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="a91fe-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span> <span data-ttu-id="a91fe-143">Puesto que también se usa para la cuenta de administrador del dominio (después de la promoción del dominio), necesitamos convertir este PSCredential existente en una credencial apta para dominio para poder agregar un usuario de dominio al grupo de administradores local en el servidor miembro.</span><span class="sxs-lookup"><span data-stu-id="a91fe-143">As this is also used for the Domain Admin Account (after Domain promotion) we then need to convert this existing PSCredential to a Domain Friendly credential to enable us to add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```

## <a name="example-3"></a><span data-ttu-id="a91fe-144">Ejemplo 3</span><span class="sxs-lookup"><span data-stu-id="a91fe-144">Example 3</span></span>
<span data-ttu-id="a91fe-145">En el ejemplo siguiente se muestra cómo asegurarse de un grupo local, TigerTeamAdmins, en el servidor TigerTeamSource.Contoso.Com no contiene una cuenta de dominio en particular, Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="a91fe-145">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>  

```powershell

Configuration SecureTigerTeamSrouce 
{
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'
  
  Node TigerTeamSource.Contoso.Com {
  Group TigerTeamAdmins
    {
       GroupName        = 'TigerTeamAdmins'   
       Ensure           = 'Absent'             
       MembersToInclude = "Contoso\JerryG"
    }
  }
}
```

