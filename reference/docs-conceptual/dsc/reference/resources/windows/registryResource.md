---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Registry
ms.openlocfilehash: be2f9134368784ad2d208362104ce046c49492e0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953082"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="669bc-103">Recursos de DSC Registry</span><span class="sxs-lookup"><span data-stu-id="669bc-103">DSC Registry Resource</span></span>

> <span data-ttu-id="669bc-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="669bc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="669bc-105">El recurso **Registry** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar valores y claves del Registro en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="669bc-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="669bc-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="669bc-106">Syntax</span></span>

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="669bc-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="669bc-107">Properties</span></span>

|<span data-ttu-id="669bc-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="669bc-108">Property</span></span> |<span data-ttu-id="669bc-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="669bc-109">Description</span></span> |
|---|---|
|<span data-ttu-id="669bc-110">Clave</span><span class="sxs-lookup"><span data-stu-id="669bc-110">Key</span></span> |<span data-ttu-id="669bc-111">Indica la ruta de acceso de la clave del Registro para la que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="669bc-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="669bc-112">Esta ruta de acceso debe incluir el subárbol.</span><span class="sxs-lookup"><span data-stu-id="669bc-112">This path must include the hive.</span></span> |
|<span data-ttu-id="669bc-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="669bc-113">ValueName</span></span> |<span data-ttu-id="669bc-114">Indica el nombre del valor del Registro.</span><span class="sxs-lookup"><span data-stu-id="669bc-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="669bc-115">Para agregar o quitar una clave del Registro, especifique esta propiedad como una cadena vacía sin especificar **ValueType** ni **ValueData**.</span><span class="sxs-lookup"><span data-stu-id="669bc-115">To add or remove a registry key, specify this property as an empty string without specifying **ValueType** or **ValueData**.</span></span> <span data-ttu-id="669bc-116">Para modificar o quitar el valor predeterminado de una clave del Registro, especifique esta propiedad como una cadena vacía y especifique también **ValueType** o **ValueData**.</span><span class="sxs-lookup"><span data-stu-id="669bc-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying **ValueType** or **ValueData**.</span></span> |
|<span data-ttu-id="669bc-117">Force</span><span class="sxs-lookup"><span data-stu-id="669bc-117">Force</span></span> |<span data-ttu-id="669bc-118">Si la clave del Registro especificada existe, **Force** la sobrescribirá con el nuevo valor.</span><span class="sxs-lookup"><span data-stu-id="669bc-118">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="669bc-119">Si elimina una clave del Registro con subclaves, debe ser `$true`.</span><span class="sxs-lookup"><span data-stu-id="669bc-119">If deleting a registry key with subkeys, this needs to be `$true`.</span></span> |
|<span data-ttu-id="669bc-120">Hex</span><span class="sxs-lookup"><span data-stu-id="669bc-120">Hex</span></span> |<span data-ttu-id="669bc-121">Indica si los datos se expresarán en formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="669bc-121">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="669bc-122">Si se especifica, los datos de valores DWORD o QWORD se muestran en formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="669bc-122">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="669bc-123">No es válido para otros tipos.</span><span class="sxs-lookup"><span data-stu-id="669bc-123">Not valid for other types.</span></span> <span data-ttu-id="669bc-124">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="669bc-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="669bc-125">ValueData</span><span class="sxs-lookup"><span data-stu-id="669bc-125">ValueData</span></span> |<span data-ttu-id="669bc-126">Los datos para el valor del Registro.</span><span class="sxs-lookup"><span data-stu-id="669bc-126">The data for the registry value.</span></span> |
|<span data-ttu-id="669bc-127">ValueType</span><span class="sxs-lookup"><span data-stu-id="669bc-127">ValueType</span></span> |<span data-ttu-id="669bc-128">Indica el tipo del valor.</span><span class="sxs-lookup"><span data-stu-id="669bc-128">Indicates the type of the value.</span></span> <span data-ttu-id="669bc-129">Los tipos admitidos son: **cadena** (REG_SZ), **Binario** (REG-BINARY), **Dword** (REG_DWORD de 32 bits), **Qword** (REG_QWORD de 64 bits), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span><span class="sxs-lookup"><span data-stu-id="669bc-129">The supported types are: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (32-bit REG_DWORD), **Qword** (64-bit REG_QWORD), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span></span> |

## <a name="common-properties"></a><span data-ttu-id="669bc-130">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="669bc-130">Common properties</span></span>

|<span data-ttu-id="669bc-131">Propiedad</span><span class="sxs-lookup"><span data-stu-id="669bc-131">Property</span></span> |<span data-ttu-id="669bc-132">Descripción</span><span class="sxs-lookup"><span data-stu-id="669bc-132">Description</span></span> |
|---|---|
|<span data-ttu-id="669bc-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="669bc-133">DependsOn</span></span> |<span data-ttu-id="669bc-134">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="669bc-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="669bc-135">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="669bc-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="669bc-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="669bc-136">Ensure</span></span> |<span data-ttu-id="669bc-137">Indica si existen la clave y valor.</span><span class="sxs-lookup"><span data-stu-id="669bc-137">Indicates if the key and value exist.</span></span> <span data-ttu-id="669bc-138">Para asegurarse de que existan, establezca esta propiedad en **Present**.</span><span class="sxs-lookup"><span data-stu-id="669bc-138">To ensure that they do, set this property to **Present**.</span></span> <span data-ttu-id="669bc-139">Para asegurarse de que no existan, establezca esta propiedad en **Absent**.</span><span class="sxs-lookup"><span data-stu-id="669bc-139">To ensure that they do not exist, set the property to **Absent**.</span></span> <span data-ttu-id="669bc-140">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="669bc-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="669bc-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="669bc-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="669bc-142">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="669bc-142">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="669bc-143">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="669bc-143">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="669bc-144">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="669bc-144">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="669bc-145">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="669bc-145">Example</span></span>

<span data-ttu-id="669bc-146">Este ejemplo garantiza que una clave denominada "ExampleKey" está presente en el subárbol **HKEY\_LOCAL\_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="669bc-146">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> <span data-ttu-id="669bc-147">Cambiar una configuración de registro en el subárbol `HKEY_CURRENT_USER` requiere que la configuración se ejecute con las credenciales de usuario y no como el sistema.</span><span class="sxs-lookup"><span data-stu-id="669bc-147">Changing a registry setting in the `HKEY_CURRENT_USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="669bc-148">Puede usar la propiedad **PsDscRunAsCredential** para especificar las credenciales de usuario para la configuración.</span><span class="sxs-lookup"><span data-stu-id="669bc-148">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="669bc-149">Para obtener un ejemplo, consulte [DSC de ejecución con las credenciales de usuario](../../../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="669bc-149">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>