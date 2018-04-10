---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC File
ms.openlocfilehash: 7964eabe5f4585600ae80f3e5ff7439c0d954769
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-file-resource"></a><span data-ttu-id="27605-103">Recurso de DSC File</span><span class="sxs-lookup"><span data-stu-id="27605-103">DSC File Resource</span></span>

> <span data-ttu-id="27605-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="27605-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="27605-105">El recurso File de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar archivos y carpetas en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="27605-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="27605-106">**Nota:** Si la propiedad **MatchSource** está establecida en **$false** (que es el valor predeterminado), los contenidos que desea copiar se almacenarán en caché la primera vez que se aplique la configuración.</span><span class="sxs-lookup"><span data-stu-id="27605-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="27605-107">Las aplicaciones subsiguientes de la configuración no buscarán archivos o carpetas actualizados en la ruta especificada por **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="27605-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="27605-108">Si desea buscar actualizaciones para los archivos y carpetas de **SourcePath** cada vez que se aplique la configuración, establezca **MatchSource** en **$true**.</span><span class="sxs-lookup"><span data-stu-id="27605-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="27605-109">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="27605-109">Syntax</span></span>
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="27605-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="27605-110">Properties</span></span>

|  <span data-ttu-id="27605-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="27605-111">Property</span></span>  |  <span data-ttu-id="27605-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="27605-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="27605-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="27605-113">DestinationPath</span></span>| <span data-ttu-id="27605-114">Indica la ubicación donde desea garantizar el estado de un archivo o directorio.</span><span class="sxs-lookup"><span data-stu-id="27605-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="27605-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="27605-115">Attributes</span></span>| <span data-ttu-id="27605-116">Especifica el estado deseado de los atributos del archivo o directorio de destino.</span><span class="sxs-lookup"><span data-stu-id="27605-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="27605-117">Checksum</span><span class="sxs-lookup"><span data-stu-id="27605-117">Checksum</span></span>| <span data-ttu-id="27605-118">Indica el tipo de suma de comprobación para determinar si dos archivos son iguales.</span><span class="sxs-lookup"><span data-stu-id="27605-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="27605-119">Si no se especifica __Checksum__, solo se usa el nombre del archivo o directorio para la comparación.</span><span class="sxs-lookup"><span data-stu-id="27605-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="27605-120">Los valores válidos son: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="27605-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="27605-121">Contenido</span><span class="sxs-lookup"><span data-stu-id="27605-121">Contents</span></span>| <span data-ttu-id="27605-122">Especifica el contenido de un archivo, como una cadena determinada.</span><span class="sxs-lookup"><span data-stu-id="27605-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="27605-123">Credential</span><span class="sxs-lookup"><span data-stu-id="27605-123">Credential</span></span>| <span data-ttu-id="27605-124">Indica las credenciales necesarias para acceder a recursos, como archivos de origen, si es necesario dicho acceso.</span><span class="sxs-lookup"><span data-stu-id="27605-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="27605-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="27605-125">Ensure</span></span>| <span data-ttu-id="27605-126">Indica si el archivo o directorio existe.</span><span class="sxs-lookup"><span data-stu-id="27605-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="27605-127">Establezca esta propiedad en "Absent" para asegurarse de que el archivo o directorio no exista.</span><span class="sxs-lookup"><span data-stu-id="27605-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="27605-128">Establézcala en "Present" para asegurarse de que el archivo o directorio exista.</span><span class="sxs-lookup"><span data-stu-id="27605-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="27605-129">El valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="27605-129">The default is "Present".</span></span>|
| <span data-ttu-id="27605-130">Force</span><span class="sxs-lookup"><span data-stu-id="27605-130">Force</span></span>| <span data-ttu-id="27605-131">Determinadas operaciones de archivos (por ejemplo, sobrescribir un archivo o eliminar un directorio que no está vacío) provocarán un error.</span><span class="sxs-lookup"><span data-stu-id="27605-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="27605-132">Si se usa la propiedad Force, se invalidan estos errores.</span><span class="sxs-lookup"><span data-stu-id="27605-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="27605-133">El valor predeterminado es __$false__.</span><span class="sxs-lookup"><span data-stu-id="27605-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="27605-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="27605-134">Recurse</span></span>| <span data-ttu-id="27605-135">Indica si se incluyen los subdirectorios.</span><span class="sxs-lookup"><span data-stu-id="27605-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="27605-136">Establezca esta propiedad en __$true__ para indicar que quiere que los subdirectorios se incluyan.</span><span class="sxs-lookup"><span data-stu-id="27605-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="27605-137">El valor predeterminado es __$false__.</span><span class="sxs-lookup"><span data-stu-id="27605-137">The default is __$false__.</span></span> <span data-ttu-id="27605-138">**Nota**: Esta propiedad solo es válida cuando la propiedad Type está establecida en Directory.</span><span class="sxs-lookup"><span data-stu-id="27605-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="27605-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="27605-139">DependsOn</span></span> | <span data-ttu-id="27605-140">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="27605-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="27605-141">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="27605-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="27605-142">SourcePath</span><span class="sxs-lookup"><span data-stu-id="27605-142">SourcePath</span></span>| <span data-ttu-id="27605-143">Indica la ruta de acceso de la que se copiará el recurso de archivo o carpeta.</span><span class="sxs-lookup"><span data-stu-id="27605-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="27605-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="27605-144">Type</span></span>| <span data-ttu-id="27605-145">Indica si el recurso que se está configurando es un directorio o un archivo.</span><span class="sxs-lookup"><span data-stu-id="27605-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="27605-146">Establezca esta propiedad en "Directory" para indicar que el recurso es un directorio.</span><span class="sxs-lookup"><span data-stu-id="27605-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="27605-147">Establézcala en "File" para indicar que el recurso es un archivo.</span><span class="sxs-lookup"><span data-stu-id="27605-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="27605-148">El valor predeterminado es "File".</span><span class="sxs-lookup"><span data-stu-id="27605-148">The default value is “File”.</span></span>|
| <span data-ttu-id="27605-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="27605-149">MatchSource</span></span>| <span data-ttu-id="27605-150">Si se establece en el valor predeterminado de __$false__, los archivos en el origen (por ejemplo, los archivos A, B y C) se agregarán al destino la primera vez que se aplique la configuración.</span><span class="sxs-lookup"><span data-stu-id="27605-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="27605-151">Si se agrega un nuevo archivo (D) al origen, no se agregará al destino, incluso aunque la configuración se vuelva a aplicar más adelante.</span><span class="sxs-lookup"><span data-stu-id="27605-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="27605-152">Si el valor es __$true__, cada vez que se aplique la configuración, se agregan los nuevos archivos encontrados posteriormente en el origen (como el archivo D de este ejemplo) al destino.</span><span class="sxs-lookup"><span data-stu-id="27605-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="27605-153">El valor predeterminado es **$false**.</span><span class="sxs-lookup"><span data-stu-id="27605-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="27605-154">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27605-154">Example</span></span>

<span data-ttu-id="27605-155">En el ejemplo siguiente se muestra cómo usar el recurso File para asegurarse de que un directorio con la ruta de acceso `C:\Users\Public\Documents\DSCDemo\DemoSource` en un equipo de origen (por ejemplo, el servidor "pull") también está presente (junto con todos los subdirectorios) en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="27605-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="27605-156">También escribe un mensaje de confirmación en el registro cuando se complete e incluye una instrucción para asegurarse de que se ejecuta la operación de comprobación de archivos antes de la operación de registro.</span><span class="sxs-lookup"><span data-stu-id="27605-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```