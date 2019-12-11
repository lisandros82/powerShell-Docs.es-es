---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso nxUser de DSC para Linux
ms.openlocfilehash: 6d7b52809741813af7fa80b1c6372b267aff4777
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954802"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="47df1-103">Recurso nxUser de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="47df1-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="47df1-104">El recurso **nxUser** de Desired State Configuration (DSC) de PowerShell ofrece un mecanismo para administrar usuarios locales en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="47df1-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="47df1-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="47df1-105">Syntax</span></span>

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="47df1-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="47df1-106">Properties</span></span>

|<span data-ttu-id="47df1-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="47df1-107">Property</span></span> |<span data-ttu-id="47df1-108">Indica el nombre de la cuenta para la que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="47df1-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
|<span data-ttu-id="47df1-109">UserName</span><span class="sxs-lookup"><span data-stu-id="47df1-109">UserName</span></span> |<span data-ttu-id="47df1-110">Especifica la ubicación donde desea garantizar el estado de un archivo o directorio.</span><span class="sxs-lookup"><span data-stu-id="47df1-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="47df1-111">FullName</span><span class="sxs-lookup"><span data-stu-id="47df1-111">FullName</span></span> |<span data-ttu-id="47df1-112">Una cadena que contiene el nombre completo que se usará para la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="47df1-112">A string that contains the full name to use for the user account.</span></span> |
|<span data-ttu-id="47df1-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="47df1-113">Description</span></span> |<span data-ttu-id="47df1-114">La descripción de la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="47df1-114">The description for the user account.</span></span> |
|<span data-ttu-id="47df1-115">Contraseña</span><span class="sxs-lookup"><span data-stu-id="47df1-115">Password</span></span> |<span data-ttu-id="47df1-116">El hash de la contraseña de los usuarios en el formato adecuado para el equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="47df1-116">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="47df1-117">Normalmente, es un hash SHA-512 o SHA-256 con sal.</span><span class="sxs-lookup"><span data-stu-id="47df1-117">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="47df1-118">En Debian y Ubuntu Linux, este valor se puede generar con el comando `mkpasswd`.</span><span class="sxs-lookup"><span data-stu-id="47df1-118">On Debian and Ubuntu Linux, this value can be generated with the `mkpasswd` command.</span></span> <span data-ttu-id="47df1-119">Para otras distribuciones de Linux, puede utilizarse el método de cifrado de la biblioteca de cifrado de Python para generar el hash.</span><span class="sxs-lookup"><span data-stu-id="47df1-119">For other Linux distros, the crypt method of Python's Crypt library can be used to generate the hash.</span></span> |
|<span data-ttu-id="47df1-120">Deshabilitada</span><span class="sxs-lookup"><span data-stu-id="47df1-120">Disabled</span></span> |<span data-ttu-id="47df1-121">Indica si la cuenta se encuentra habilitada.</span><span class="sxs-lookup"><span data-stu-id="47df1-121">Indicates whether the account is enabled.</span></span> <span data-ttu-id="47df1-122">Establezca esta propiedad en `$true` para asegurarse de que esta cuenta esté deshabilitada y establézcala como `$false` para asegurarse de que esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="47df1-122">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="47df1-123">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="47df1-123">PasswordChangeRequired</span></span> |<span data-ttu-id="47df1-124">Indica si el usuario puede cambiar la contraseña.</span><span class="sxs-lookup"><span data-stu-id="47df1-124">Indicates whether the user can change the password.</span></span> <span data-ttu-id="47df1-125">Establezca esta propiedad en `$true` para asegurarse de que el usuario no pueda cambiar la contraseña y establézcala como `$false` para permitir al usuario cambiar la contraseña.</span><span class="sxs-lookup"><span data-stu-id="47df1-125">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="47df1-126">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="47df1-126">The default value is `$false`.</span></span> <span data-ttu-id="47df1-127">Esta propiedad solo se evalúa si la cuenta de usuario no existía anteriormente y se está creando.</span><span class="sxs-lookup"><span data-stu-id="47df1-127">This property is only evaluated if the user account did not exist previously and is being created.</span></span> |
|<span data-ttu-id="47df1-128">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="47df1-128">HomeDirectory</span></span> |<span data-ttu-id="47df1-129">El directorio principal del usuario.</span><span class="sxs-lookup"><span data-stu-id="47df1-129">The home directory for the user.</span></span> |
|<span data-ttu-id="47df1-130">GroupID</span><span class="sxs-lookup"><span data-stu-id="47df1-130">GroupID</span></span> |<span data-ttu-id="47df1-131">El identificador de grupo principal del usuario.</span><span class="sxs-lookup"><span data-stu-id="47df1-131">The primary group ID for the user.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="47df1-132">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="47df1-132">Common properties</span></span>

|<span data-ttu-id="47df1-133">Propiedad</span><span class="sxs-lookup"><span data-stu-id="47df1-133">Property</span></span> |<span data-ttu-id="47df1-134">Descripción</span><span class="sxs-lookup"><span data-stu-id="47df1-134">Description</span></span> |
|---|---|
|<span data-ttu-id="47df1-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="47df1-135">DependsOn</span></span> |<span data-ttu-id="47df1-136">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="47df1-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="47df1-137">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="47df1-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="47df1-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="47df1-138">Ensure</span></span> |<span data-ttu-id="47df1-139">Especifica si la cuenta existe.</span><span class="sxs-lookup"><span data-stu-id="47df1-139">Specifies whether the account exists.</span></span> <span data-ttu-id="47df1-140">Establezca esta propiedad en **Present** para asegurarse de que la cuenta exista y establézcala como **Absent** para asegurarse de que la cuenta no exista.</span><span class="sxs-lookup"><span data-stu-id="47df1-140">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> |

## <a name="example"></a><span data-ttu-id="47df1-141">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="47df1-141">Example</span></span>

<span data-ttu-id="47df1-142">En el ejemplo siguiente se asegura de que el usuario "monuser" exista y de que sea un miembro del grupo "DBusers".</span><span class="sxs-lookup"><span data-stu-id="47df1-142">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
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