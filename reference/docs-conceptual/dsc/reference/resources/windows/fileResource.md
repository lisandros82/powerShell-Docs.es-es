---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC File
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954682"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="64adc-103">Recurso de DSC File</span><span class="sxs-lookup"><span data-stu-id="64adc-103">DSC File Resource</span></span>

> <span data-ttu-id="64adc-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="64adc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="64adc-105">El recurso **File** de Desired State Configuration (DSC) de Windows PowerShell ofrece un mecanismo para administrar archivos y carpetas en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="64adc-105">The **File** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="64adc-106">Las propiedades **DestinationPath** y **SourcePath** deben ser accesibles para el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="64adc-106">**DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="64adc-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="64adc-107">Syntax</span></span>

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="64adc-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="64adc-108">Properties</span></span>

|<span data-ttu-id="64adc-109">Propiedad</span><span class="sxs-lookup"><span data-stu-id="64adc-109">Property</span></span> |<span data-ttu-id="64adc-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="64adc-110">Description</span></span> |
|---|---|
|<span data-ttu-id="64adc-111">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="64adc-111">DestinationPath</span></span> |<span data-ttu-id="64adc-112">La ubicación, en el nodo de destino, que quiere comprobar es **Present** o **Absent** con **Ensure**.</span><span class="sxs-lookup"><span data-stu-id="64adc-112">The location, on the target node, you want to ensure is **Present** or **Absent** with **Ensure**.</span></span> |
|<span data-ttu-id="64adc-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="64adc-113">Attributes</span></span> |<span data-ttu-id="64adc-114">El estado deseado de los atributos del archivo o directorio de destino.</span><span class="sxs-lookup"><span data-stu-id="64adc-114">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="64adc-115">Los valores válidos son _Archive_, _Hidden_, _ReadOnly_ y _System_.</span><span class="sxs-lookup"><span data-stu-id="64adc-115">Valid values are _Archive_, _Hidden_, _ReadOnly_, and _System_.</span></span> |
|<span data-ttu-id="64adc-116">Checksum</span><span class="sxs-lookup"><span data-stu-id="64adc-116">Checksum</span></span> |<span data-ttu-id="64adc-117">El tipo de suma de comprobación para determinar si dos archivos son iguales.</span><span class="sxs-lookup"><span data-stu-id="64adc-117">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="64adc-118">Los valores válidos son: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="64adc-118">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> |
|<span data-ttu-id="64adc-119">Contenido</span><span class="sxs-lookup"><span data-stu-id="64adc-119">Contents</span></span> |<span data-ttu-id="64adc-120">Solo es válido cuando se usa con el tipo **Type** **File**.</span><span class="sxs-lookup"><span data-stu-id="64adc-120">Only valid when used with **Type** **File**.</span></span> <span data-ttu-id="64adc-121">Indica que los contenidos de **Ensure** son **Present** o **Absent** del archivo de destino.</span><span class="sxs-lookup"><span data-stu-id="64adc-121">Indicates the contents to **Ensure** are **Present** or **Absent** from the targeted file.</span></span> |
|<span data-ttu-id="64adc-122">Credential</span><span class="sxs-lookup"><span data-stu-id="64adc-122">Credential</span></span> |<span data-ttu-id="64adc-123">Las credenciales necesarias para acceder a recursos, como archivos de origen.</span><span class="sxs-lookup"><span data-stu-id="64adc-123">The credentials that are required to access resources, such as source files.</span></span> |
|<span data-ttu-id="64adc-124">Force</span><span class="sxs-lookup"><span data-stu-id="64adc-124">Force</span></span> |<span data-ttu-id="64adc-125">Anula las operaciones de acceso que provocarían un error (por ejemplo, sobrescribir un archivo o eliminar un directorio que no está vacío).</span><span class="sxs-lookup"><span data-stu-id="64adc-125">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span> <span data-ttu-id="64adc-126">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="64adc-126">Default value is `$false`.</span></span> |
|<span data-ttu-id="64adc-127">Recurse</span><span class="sxs-lookup"><span data-stu-id="64adc-127">Recurse</span></span> |<span data-ttu-id="64adc-128">Solo es válido cuando se usa con el tipo **Type** **Directory**.</span><span class="sxs-lookup"><span data-stu-id="64adc-128">Only valid when used with **Type** **Directory**.</span></span> <span data-ttu-id="64adc-129">Realiza la operación de estado forma recursiva en todos los subdirectorios.</span><span class="sxs-lookup"><span data-stu-id="64adc-129">Performs the state operation recursively to all subdirectories.</span></span> <span data-ttu-id="64adc-130">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="64adc-130">Default value is `$false`.</span></span> |
|<span data-ttu-id="64adc-131">SourcePath</span><span class="sxs-lookup"><span data-stu-id="64adc-131">SourcePath</span></span> |<span data-ttu-id="64adc-132">La ruta de acceso de la que se copiará el recurso de archivo o carpeta.</span><span class="sxs-lookup"><span data-stu-id="64adc-132">The path from which to copy the file or folder resource.</span></span> |
|<span data-ttu-id="64adc-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="64adc-133">Type</span></span> |<span data-ttu-id="64adc-134">El tipo de recurso que se está configurando.</span><span class="sxs-lookup"><span data-stu-id="64adc-134">The type of resource being configured.</span></span> <span data-ttu-id="64adc-135">Los valores válidos son **Directory** y **File**.</span><span class="sxs-lookup"><span data-stu-id="64adc-135">Valid values are **Directory** and **File**.</span></span> <span data-ttu-id="64adc-136">El valor predeterminado es **File**.</span><span class="sxs-lookup"><span data-stu-id="64adc-136">Default value is **File**.</span></span> |
|<span data-ttu-id="64adc-137">MatchSource</span><span class="sxs-lookup"><span data-stu-id="64adc-137">MatchSource</span></span> |<span data-ttu-id="64adc-138">Determina si el recurso debe supervisar los nuevos archivos agregados al directorio de origen después de la copia inicial.</span><span class="sxs-lookup"><span data-stu-id="64adc-138">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="64adc-139">Un valor de `$true` indica que, después de la copia inicial, los nuevos archivos de origen deben copiarse en el destino.</span><span class="sxs-lookup"><span data-stu-id="64adc-139">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="64adc-140">Si se establece en `$false`, el recurso almacena en caché el contenido del directorio de origen y omite los archivos agregados después de la copia inicial.</span><span class="sxs-lookup"><span data-stu-id="64adc-140">If set to `$false`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span> <span data-ttu-id="64adc-141">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="64adc-141">Default value is `$false`.</span></span> |

> [!WARNING]
> <span data-ttu-id="64adc-142">Si no especifica un valor para **Credential** o **PSRunAsCredential**, el recurso usará la cuenta de equipo del nodo de destino para tener acceso a **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="64adc-142">If you do not specify a value for **Credential** or **PSRunAsCredential**, the resource will use the computer account of the target node to access the **SourcePath**.</span></span> <span data-ttu-id="64adc-143">Cuando **SourcePath** es un recurso compartido de UNC, podría provocar un error de "Acceso denegado".</span><span class="sxs-lookup"><span data-stu-id="64adc-143">When the **SourcePath** is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="64adc-144">Asegúrese de los permisos se establecen en consecuencia, o use las propiedades **Credential** o **PSRunAsCredential** para especificar la cuenta que debe usarse.</span><span class="sxs-lookup"><span data-stu-id="64adc-144">Please ensure your permissions are set accordingly, or use the **Credential** or **PSRunAsCredential** properties to specify the account that should be used.</span></span>

## <a name="common-properties"></a><span data-ttu-id="64adc-145">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="64adc-145">Common properties</span></span>

|<span data-ttu-id="64adc-146">Propiedad</span><span class="sxs-lookup"><span data-stu-id="64adc-146">Property</span></span> |<span data-ttu-id="64adc-147">Descripción</span><span class="sxs-lookup"><span data-stu-id="64adc-147">Description</span></span> |
|---|---|
|<span data-ttu-id="64adc-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="64adc-148">DependsOn</span></span> |<span data-ttu-id="64adc-149">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="64adc-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="64adc-150">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="64adc-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="64adc-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="64adc-151">Ensure</span></span> |<span data-ttu-id="64adc-152">Determina si el archivo y **Contents** deben existir o no en **Destination**.</span><span class="sxs-lookup"><span data-stu-id="64adc-152">Determines whether the file and **Contents** at the **Destination** should exist or not.</span></span> <span data-ttu-id="64adc-153">Establezca esta propiedad en **Present** para asegurarse de que el archivo exista.</span><span class="sxs-lookup"><span data-stu-id="64adc-153">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="64adc-154">Establézcala en **Absent** para asegurarse de que no exista.</span><span class="sxs-lookup"><span data-stu-id="64adc-154">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="64adc-155">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="64adc-155">The default value is **Present**.</span></span> |
|<span data-ttu-id="64adc-156">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="64adc-156">PsDscRunAsCredential</span></span> |<span data-ttu-id="64adc-157">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="64adc-157">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="64adc-158">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="64adc-158">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="64adc-159">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="64adc-159">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="64adc-160">Información adicional</span><span class="sxs-lookup"><span data-stu-id="64adc-160">Additional information</span></span>

- <span data-ttu-id="64adc-161">Cuando se especifica solo un **DestinationPath**, el recurso comprueba que la ruta de acceso existe, si es **Present**, o no existe, si es **Absent**.</span><span class="sxs-lookup"><span data-stu-id="64adc-161">When you only specify a **DestinationPath**, the resource ensures that the path exists if **Present** or does not exist if **Absent**.</span></span>
- <span data-ttu-id="64adc-162">Cuando se especifica**SourcePath** y un **DestinationPath** con un valor **Type** de **Directory**, el recurso copia el directorio de origen en la ruta de acceso de destino.</span><span class="sxs-lookup"><span data-stu-id="64adc-162">When you specify a **SourcePath** and a **DestinationPath** with a **Type** value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="64adc-163">Las propiedades **Recurse**, **Force** y **MatchSource** cambian el tipo de operación de copia realizada, mientras que **Credential** determina qué cuenta se usa para tener acceso al directorio de origen.</span><span class="sxs-lookup"><span data-stu-id="64adc-163">The properties **Recurse**, **Force**, and **MatchSource** change the type of copy operation performed, while **Credential** determines which account to use to access the source directory.</span></span>
- <span data-ttu-id="64adc-164">Si especificó un valor de **ReadOnly** para la propiedad **Attributes** junto con un **DestinationPath**, **Ensure** **Present** crearía la ruta de acceso especificada, mientras que **Contents** establecería el contenido del archivo.</span><span class="sxs-lookup"><span data-stu-id="64adc-164">If you specified a value of **ReadOnly** for the **Attributes** property alongside a **DestinationPath**, **Ensure** **Present** would create the path specified, while **Contents** would set the contents of the file.</span></span> <span data-ttu-id="64adc-165">Un **Ensure** **Absent** omitiría la propiedad **Attributes** completamente y quitaría cualquier archivo en la ruta especificada.</span><span class="sxs-lookup"><span data-stu-id="64adc-165">An **Ensure** **Absent** setting would ignore the **Attributes** property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="64adc-166">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="64adc-166">Example</span></span>

<span data-ttu-id="64adc-167">En el ejemplo siguiente se copia un directorio y sus subdirectorios de un servidor de extracción a un nodo de destino utilizando el archivo de recursos.</span><span class="sxs-lookup"><span data-stu-id="64adc-167">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="64adc-168">Si la operación se realiza correctamente, el recurso de registro escribe un mensaje de confirmación en el registro de eventos.</span><span class="sxs-lookup"><span data-stu-id="64adc-168">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="64adc-169">El directorio de origen es una ruta de acceso UNC (`\\PullServer\DemoSource`) compartida desde el servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="64adc-169">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="64adc-170">La propiedad **Recurse** garantiza que también se copian todos los subdirectorios.</span><span class="sxs-lookup"><span data-stu-id="64adc-170">The **Recurse** property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64adc-171">El LCM en el nodo de destino se ejecuta en el contexto de la cuenta sistema local de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="64adc-171">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="64adc-172">Para conceder acceso a **SourcePath**, asigne los permisos adecuados a la cuenta de equipo del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="64adc-172">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="64adc-173">**Credential** y **PSDSCRunAsCredential** cambian el contexto que usa el LCM para tener acceso a **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="64adc-173">The **Credential** and **PSDSCRunAsCredential** both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="64adc-174">Aun será necesario que conceda acceso a la cuenta que se usará para tener acceso a **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="64adc-174">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

<span data-ttu-id="64adc-175">Para obtener más detalles sobre el uso de **credenciales** en DSC, consulte la información sobre [ejecutar como usuario](../../../configurations/runAsUser.md) o las [credenciales en datos de configuración](../../../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="64adc-175">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>