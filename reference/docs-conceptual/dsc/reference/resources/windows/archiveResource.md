---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Archive
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954772"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="ab360-103">Recursos de DSC Archive</span><span class="sxs-lookup"><span data-stu-id="ab360-103">DSC Archive Resource</span></span>

> <span data-ttu-id="ab360-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="ab360-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="ab360-105">El recurso Archive de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para desempaquetar archivos de almacenamiento (.zip) en una ruta de acceso específica.</span><span class="sxs-lookup"><span data-stu-id="ab360-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="ab360-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ab360-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="ab360-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ab360-107">Properties</span></span>

|<span data-ttu-id="ab360-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ab360-108">Property</span></span> |<span data-ttu-id="ab360-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="ab360-109">Description</span></span> |
|---|---|
|<span data-ttu-id="ab360-110">Destination</span><span class="sxs-lookup"><span data-stu-id="ab360-110">Destination</span></span> |<span data-ttu-id="ab360-111">Especifica la ubicación donde quiere garantizar que se extraiga el contenido del archivo.</span><span class="sxs-lookup"><span data-stu-id="ab360-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="ab360-112">Ruta</span><span class="sxs-lookup"><span data-stu-id="ab360-112">Path</span></span> |<span data-ttu-id="ab360-113">Especifica la ruta de acceso de origen del archivo.</span><span class="sxs-lookup"><span data-stu-id="ab360-113">Specifies the source path of the archive file.</span></span> |
|<span data-ttu-id="ab360-114">Checksum</span><span class="sxs-lookup"><span data-stu-id="ab360-114">Checksum</span></span> |<span data-ttu-id="ab360-115">Define el tipo que se usará cuando se determine si dos archivos son iguales.</span><span class="sxs-lookup"><span data-stu-id="ab360-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="ab360-116">Si no se especifica **Checksum**, solo se usa el nombre del archivo o directorio para la comparación.</span><span class="sxs-lookup"><span data-stu-id="ab360-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="ab360-117">Los valores válidos son: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="ab360-117">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> <span data-ttu-id="ab360-118">Si especifica **Checksum** sin **Validate**, se producirá un error de configuración.</span><span class="sxs-lookup"><span data-stu-id="ab360-118">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> |
|<span data-ttu-id="ab360-119">Force</span><span class="sxs-lookup"><span data-stu-id="ab360-119">Force</span></span> |<span data-ttu-id="ab360-120">Determinadas operaciones de archivos (por ejemplo, sobrescribir un archivo o eliminar un directorio que no está vacío) provocarán un error.</span><span class="sxs-lookup"><span data-stu-id="ab360-120">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="ab360-121">Si se usa la propiedad **Force**, se invalidan estos errores.</span><span class="sxs-lookup"><span data-stu-id="ab360-121">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="ab360-122">El valor predeterminado es **False**.</span><span class="sxs-lookup"><span data-stu-id="ab360-122">The default value is **False**.</span></span> |
|<span data-ttu-id="ab360-123">Validar</span><span class="sxs-lookup"><span data-stu-id="ab360-123">Validate</span></span>| <span data-ttu-id="ab360-124">Utiliza la propiedad **Checksum** para determinar si el archivo coincide con la firma.</span><span class="sxs-lookup"><span data-stu-id="ab360-124">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="ab360-125">Si especifica **Checksum** sin **Validate**, se producirá un error de configuración.</span><span class="sxs-lookup"><span data-stu-id="ab360-125">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> <span data-ttu-id="ab360-126">Si especifica **Validate** sin **Checksum**, se usará una suma de comprobación _SHA-256_ **Checksum** de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="ab360-126">If you specify **Validate** without **Checksum**, a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ab360-127">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="ab360-127">Common properties</span></span>

|<span data-ttu-id="ab360-128">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ab360-128">Property</span></span> |<span data-ttu-id="ab360-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="ab360-129">Description</span></span> |
|---|---|
|<span data-ttu-id="ab360-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ab360-130">DependsOn</span></span> |<span data-ttu-id="ab360-131">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="ab360-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ab360-132">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ab360-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ab360-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="ab360-133">Ensure</span></span> |<span data-ttu-id="ab360-134">Determina si se debe comprobar si existe el contenido del archivo en **Destination**.</span><span class="sxs-lookup"><span data-stu-id="ab360-134">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="ab360-135">Establezca esta propiedad en **Present** para asegurarse de que el contenido exista.</span><span class="sxs-lookup"><span data-stu-id="ab360-135">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="ab360-136">Establézcala en **Absent** para asegurarse de que no exista.</span><span class="sxs-lookup"><span data-stu-id="ab360-136">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="ab360-137">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="ab360-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="ab360-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ab360-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="ab360-139">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="ab360-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="ab360-140">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="ab360-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="ab360-141">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="ab360-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="ab360-142">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ab360-142">Example</span></span>

<span data-ttu-id="ab360-143">En el ejemplo siguiente se muestra cómo usar el recurso Archive para asegurarse de que el contenido de un archivo llamado `Test.zip` exista y se extraiga en un destino determinado.</span><span class="sxs-lookup"><span data-stu-id="ab360-143">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```