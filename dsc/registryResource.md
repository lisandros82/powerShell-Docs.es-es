---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Registry
ms.openlocfilehash: 98e9a6251cb4e55443498bd770b4c563c25c7509
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="83121-103">Recursos de DSC Registry</span><span class="sxs-lookup"><span data-stu-id="83121-103">DSC Registry Resource</span></span>

> <span data-ttu-id="83121-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="83121-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="83121-105">El recurso **Registry** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar valores y claves del Registro en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="83121-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="83121-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="83121-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="83121-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="83121-107">Properties</span></span>
|  <span data-ttu-id="83121-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="83121-108">Property</span></span>  |  <span data-ttu-id="83121-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="83121-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="83121-110">Clave</span><span class="sxs-lookup"><span data-stu-id="83121-110">Key</span></span>| <span data-ttu-id="83121-111">Indica la ruta de acceso de la clave del Registro para la que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="83121-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="83121-112">Esta ruta de acceso debe incluir el subárbol.</span><span class="sxs-lookup"><span data-stu-id="83121-112">This path must include the hive.</span></span>|
| <span data-ttu-id="83121-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="83121-113">ValueName</span></span>| <span data-ttu-id="83121-114">Indica el nombre del valor del Registro.</span><span class="sxs-lookup"><span data-stu-id="83121-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="83121-115">Para agregar o quitar una clave del Registro, especifique esta propiedad como una cadena vacía sin especificar ValueType ni ValueData.</span><span class="sxs-lookup"><span data-stu-id="83121-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="83121-116">Para modificar o quitar el valor predeterminado de una clave del Registro, especifique esta propiedad como una cadena vacía y especifique también ValueType o ValueData.</span><span class="sxs-lookup"><span data-stu-id="83121-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="83121-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="83121-117">Ensure</span></span>| <span data-ttu-id="83121-118">Indica si existen la clave y valor.</span><span class="sxs-lookup"><span data-stu-id="83121-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="83121-119">Para asegurarse de que existan, establezca esta propiedad en "Present".</span><span class="sxs-lookup"><span data-stu-id="83121-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="83121-120">Para asegurarse de que no existan, establezca esta propiedad en "Absent".</span><span class="sxs-lookup"><span data-stu-id="83121-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="83121-121">El valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="83121-121">The default value is "Present".</span></span>|
| <span data-ttu-id="83121-122">Force</span><span class="sxs-lookup"><span data-stu-id="83121-122">Force</span></span>| <span data-ttu-id="83121-123">Si la clave del Registro especificada existe, __Force__ la sobrescribirá con el nuevo valor.</span><span class="sxs-lookup"><span data-stu-id="83121-123">If the specified registry key is present, __Force__ overwrites it with the new value.</span></span> <span data-ttu-id="83121-124">Si elimina una clave del Registro con subclaves, debe ser __$true__</span><span class="sxs-lookup"><span data-stu-id="83121-124">If deleting a registry key with subkeys, this needs to be __$true__</span></span>|
| <span data-ttu-id="83121-125">Hex</span><span class="sxs-lookup"><span data-stu-id="83121-125">Hex</span></span>| <span data-ttu-id="83121-126">Indica si los datos se expresarán en formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="83121-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="83121-127">Si se especifica, los datos de valores DWORD o QWORD se muestran en formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="83121-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="83121-128">No es válido para otros tipos.</span><span class="sxs-lookup"><span data-stu-id="83121-128">Not valid for other types.</span></span> <span data-ttu-id="83121-129">El valor predeterminado es __$false__.</span><span class="sxs-lookup"><span data-stu-id="83121-129">The default value is __$false__.</span></span>|
| <span data-ttu-id="83121-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="83121-130">DependsOn</span></span>| <span data-ttu-id="83121-131">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="83121-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="83121-132">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="83121-132">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="83121-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="83121-133">ValueData</span></span>| <span data-ttu-id="83121-134">Los datos para el valor del Registro.</span><span class="sxs-lookup"><span data-stu-id="83121-134">The data for the registry value.</span></span>|
| <span data-ttu-id="83121-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="83121-135">ValueType</span></span>| <span data-ttu-id="83121-136">Indica el tipo del valor.</span><span class="sxs-lookup"><span data-stu-id="83121-136">Indicates the type of the value.</span></span> <span data-ttu-id="83121-137">Los tipos admitidos son:</span><span class="sxs-lookup"><span data-stu-id="83121-137">The supported types are:</span></span>
<ul><li><span data-ttu-id="83121-138">Cadena (REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="83121-138">String (REG_SZ)</span></span></li>


<li><span data-ttu-id="83121-139">Binario (REG-BINARY)</span><span class="sxs-lookup"><span data-stu-id="83121-139">Binary (REG-BINARY)</span></span></li>


<li><span data-ttu-id="83121-140">Dword de 32 bits (REG_DWORD)</span><span class="sxs-lookup"><span data-stu-id="83121-140">Dword 32-bit (REG_DWORD)</span></span></li>


<li><span data-ttu-id="83121-141">Qword de 64 bits (REG_QWORD)</span><span class="sxs-lookup"><span data-stu-id="83121-141">Qword 64-bit (REG_QWORD)</span></span></li>


<li><span data-ttu-id="83121-142">Cadena múltiple (REG_MULTI_SZ)</span><span class="sxs-lookup"><span data-stu-id="83121-142">Multi-string (REG_MULTI_SZ)</span></span></li>


<li><span data-ttu-id="83121-143">Cadena expandible (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="83121-143">Expandable string (REG_EXPAND_SZ)</span></span></li></ul>

## <a name="example"></a><span data-ttu-id="83121-144">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="83121-144">Example</span></span>
<span data-ttu-id="83121-145">Este ejemplo garantiza que una clave denominada "ExampleKey" está presente en el subárbol **HKEY\_LOCAL\_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="83121-145">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>
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

><span data-ttu-id="83121-146">**Nota:** Cambiar una configuración de registro en el subárbol **HKEY\_CURRENT\_USER** requiere que la configuración se ejecute con las credenciales de usuario y no como el sistema.</span><span class="sxs-lookup"><span data-stu-id="83121-146">**Note:** Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span>
><span data-ttu-id="83121-147">Puede usar la propiedad **PsDscRunAsCredential** para especificar las credenciales de usuario para la configuración.</span><span class="sxs-lookup"><span data-stu-id="83121-147">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="83121-148">Para obtener un ejemplo, vea [DSC de ejecución con las credenciales de usuario](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="83121-148">For an example, see [Running DSC with user credentials](runAsUser.md)</span></span>
