---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Registry
ms.openlocfilehash: b77710d7a6fc599949e78c17af309ad88a1a0872
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093592"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="79263-103">Recursos de DSC Registry</span><span class="sxs-lookup"><span data-stu-id="79263-103">DSC Registry Resource</span></span>

> <span data-ttu-id="79263-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="79263-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="79263-105">El recurso **Registry** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar valores y claves del Registro en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="79263-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="79263-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="79263-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="79263-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="79263-107">Properties</span></span>

|  <span data-ttu-id="79263-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="79263-108">Property</span></span>  |  <span data-ttu-id="79263-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="79263-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="79263-110">Clave</span><span class="sxs-lookup"><span data-stu-id="79263-110">Key</span></span>| <span data-ttu-id="79263-111">Indica la ruta de acceso de la clave del Registro para la que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="79263-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="79263-112">Esta ruta de acceso debe incluir el subárbol.</span><span class="sxs-lookup"><span data-stu-id="79263-112">This path must include the hive.</span></span>|
| <span data-ttu-id="79263-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="79263-113">ValueName</span></span>| <span data-ttu-id="79263-114">Indica el nombre del valor del Registro.</span><span class="sxs-lookup"><span data-stu-id="79263-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="79263-115">Para agregar o quitar una clave del Registro, especifique esta propiedad como una cadena vacía sin especificar ValueType ni ValueData.</span><span class="sxs-lookup"><span data-stu-id="79263-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="79263-116">Para modificar o quitar el valor predeterminado de una clave del Registro, especifique esta propiedad como una cadena vacía y especifique también ValueType o ValueData.</span><span class="sxs-lookup"><span data-stu-id="79263-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="79263-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="79263-117">Ensure</span></span>| <span data-ttu-id="79263-118">Indica si existen la clave y valor.</span><span class="sxs-lookup"><span data-stu-id="79263-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="79263-119">Para asegurarse de que existan, establezca esta propiedad en "Present".</span><span class="sxs-lookup"><span data-stu-id="79263-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="79263-120">Para asegurarse de que no existan, establezca esta propiedad en "Absent".</span><span class="sxs-lookup"><span data-stu-id="79263-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="79263-121">El valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="79263-121">The default value is "Present".</span></span>|
| <span data-ttu-id="79263-122">Force</span><span class="sxs-lookup"><span data-stu-id="79263-122">Force</span></span>| <span data-ttu-id="79263-123">Si la clave del Registro especificada existe, **Force** la sobrescribirá con el nuevo valor.</span><span class="sxs-lookup"><span data-stu-id="79263-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="79263-124">Si elimina una clave del Registro con subclaves, debe ser **$true**</span><span class="sxs-lookup"><span data-stu-id="79263-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="79263-125">Hex</span><span class="sxs-lookup"><span data-stu-id="79263-125">Hex</span></span>| <span data-ttu-id="79263-126">Indica si los datos se expresarán en formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="79263-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="79263-127">Si se especifica, los datos de valores DWORD o QWORD se muestran en formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="79263-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="79263-128">No es válido para otros tipos.</span><span class="sxs-lookup"><span data-stu-id="79263-128">Not valid for other types.</span></span> <span data-ttu-id="79263-129">El valor predeterminado es **$false**.</span><span class="sxs-lookup"><span data-stu-id="79263-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="79263-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="79263-130">DependsOn</span></span>| <span data-ttu-id="79263-131">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="79263-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="79263-132">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="79263-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="79263-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="79263-133">ValueData</span></span>| <span data-ttu-id="79263-134">Los datos para el valor del Registro.</span><span class="sxs-lookup"><span data-stu-id="79263-134">The data for the registry value.</span></span>|
| <span data-ttu-id="79263-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="79263-135">ValueType</span></span>| <span data-ttu-id="79263-136">Indica el tipo del valor.</span><span class="sxs-lookup"><span data-stu-id="79263-136">Indicates the type of the value.</span></span> <span data-ttu-id="79263-137">Los tipos admitidos son: cadena (REG_SZ), binario (REG-BINARY), Dword de 32 bits (REG_DWORD), Qword de 64 bits (REG_QWORD), cadena múltiple (REG_MULTI_SZ), cadena expandible (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="79263-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="79263-138">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="79263-138">Example</span></span>

<span data-ttu-id="79263-139">Este ejemplo garantiza que una clave denominada "ExampleKey" está presente en el subárbol **HKEY\_LOCAL\_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="79263-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

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
> <span data-ttu-id="79263-140">Cambiar una configuración de registro en el subárbol **HKEY\_CURRENT\_USER** requiere que la configuración se ejecute con las credenciales de usuario y no como el sistema.</span><span class="sxs-lookup"><span data-stu-id="79263-140">Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="79263-141">Puede usar la propiedad **PsDscRunAsCredential** para especificar las credenciales de usuario para la configuración.</span><span class="sxs-lookup"><span data-stu-id="79263-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="79263-142">Para obtener un ejemplo, consulte [DSC de ejecución con las credenciales de usuario](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="79263-142">For an example, see [Running DSC with user credentials](runAsUser.md).</span></span>