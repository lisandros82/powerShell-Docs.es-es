---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso nxFile de DSC para Linux
ms.openlocfilehash: be5f098d2fe1c8b354c07e6a8f882b8fdf00e1db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954832"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="ac87f-103">Recurso nxFile de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="ac87f-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="ac87f-104">El recurso **nxFile** de Desired State Configuration (DSC) de PowerShell ofrece un mecanismo para administrar archivos y directorios en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="ac87f-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ac87f-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ac87f-105">Syntax</span></span>

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="ac87f-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ac87f-106">Properties</span></span>

|<span data-ttu-id="ac87f-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ac87f-107">Property</span></span> |<span data-ttu-id="ac87f-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="ac87f-108">Description</span></span> |
|---|---|
|<span data-ttu-id="ac87f-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="ac87f-109">DestinationPath</span></span> |<span data-ttu-id="ac87f-110">Especifica la ubicación donde desea garantizar el estado de un archivo o directorio.</span><span class="sxs-lookup"><span data-stu-id="ac87f-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="ac87f-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="ac87f-111">SourcePath</span></span> |<span data-ttu-id="ac87f-112">Especifica la ruta de acceso de la que se copiará el recurso de archivo o carpeta.</span><span class="sxs-lookup"><span data-stu-id="ac87f-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="ac87f-113">Esta ruta de acceso puede ser una ruta de acceso local o una dirección URL `http/https/ftp`.</span><span class="sxs-lookup"><span data-stu-id="ac87f-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="ac87f-114">Las direcciones URL remotas `http/https/ftp` solo se admiten cuando el valor de la propiedad **Type** es **File**.</span><span class="sxs-lookup"><span data-stu-id="ac87f-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is **file**.</span></span> |
|<span data-ttu-id="ac87f-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="ac87f-115">Type</span></span> |<span data-ttu-id="ac87f-116">Especifica si el recurso que se está configurando es un directorio o un archivo.</span><span class="sxs-lookup"><span data-stu-id="ac87f-116">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="ac87f-117">Establezca esta propiedad en **Directory** para indicar que el recurso es un directorio.</span><span class="sxs-lookup"><span data-stu-id="ac87f-117">Set this property to **directory** to indicate that the resource is a directory.</span></span> <span data-ttu-id="ac87f-118">Establézcala en **File** para indicar que el recurso es un archivo.</span><span class="sxs-lookup"><span data-stu-id="ac87f-118">Set it to **file** to indicate that the resource is a file.</span></span> <span data-ttu-id="ac87f-119">El valor predeterminado es **File**.</span><span class="sxs-lookup"><span data-stu-id="ac87f-119">The default value is **file**.</span></span> |
|<span data-ttu-id="ac87f-120">Contenido</span><span class="sxs-lookup"><span data-stu-id="ac87f-120">Contents</span></span> |<span data-ttu-id="ac87f-121">Especifica el contenido de un archivo, como una cadena determinada.</span><span class="sxs-lookup"><span data-stu-id="ac87f-121">Specifies the contents of a file, such as a particular string.</span></span> |
|<span data-ttu-id="ac87f-122">Checksum</span><span class="sxs-lookup"><span data-stu-id="ac87f-122">Checksum</span></span> |<span data-ttu-id="ac87f-123">Define el tipo que se usará cuando se determine si dos archivos son iguales.</span><span class="sxs-lookup"><span data-stu-id="ac87f-123">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="ac87f-124">Si no se especifica **Checksum**, solo se usa el nombre del archivo o directorio para la comparación.</span><span class="sxs-lookup"><span data-stu-id="ac87f-124">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="ac87f-125">Los valores son: **ctime**, **mtime** o **md5**.</span><span class="sxs-lookup"><span data-stu-id="ac87f-125">Values are: **ctime**, **mtime**, or **md5**.</span></span> |
|<span data-ttu-id="ac87f-126">Recurse</span><span class="sxs-lookup"><span data-stu-id="ac87f-126">Recurse</span></span> |<span data-ttu-id="ac87f-127">Indica si se incluyen los subdirectorios.</span><span class="sxs-lookup"><span data-stu-id="ac87f-127">Indicates if subdirectories are included.</span></span> <span data-ttu-id="ac87f-128">Establezca esta propiedad en `$true` para indicar que quiere que los subdirectorios se incluyan.</span><span class="sxs-lookup"><span data-stu-id="ac87f-128">Set this property to `$true` to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="ac87f-129">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="ac87f-129">The default is `$false`.</span></span> <span data-ttu-id="ac87f-130">Esta propiedad solo es válida cuando la propiedad **Type** está establecida en **Directory**.</span><span class="sxs-lookup"><span data-stu-id="ac87f-130">This property is only valid when the **Type** property is set to **directory**.</span></span> |
|<span data-ttu-id="ac87f-131">Force</span><span class="sxs-lookup"><span data-stu-id="ac87f-131">Force</span></span> |<span data-ttu-id="ac87f-132">Determinadas operaciones de archivos (por ejemplo, sobrescribir un archivo o eliminar un directorio que no está vacío) provocarán un error.</span><span class="sxs-lookup"><span data-stu-id="ac87f-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="ac87f-133">Si se usa la propiedad **Force**, se invalidan estos errores.</span><span class="sxs-lookup"><span data-stu-id="ac87f-133">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="ac87f-134">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="ac87f-134">The default value is `$false`.</span></span> |
|<span data-ttu-id="ac87f-135">Vínculos</span><span class="sxs-lookup"><span data-stu-id="ac87f-135">Links</span></span> |<span data-ttu-id="ac87f-136">Especifica el comportamiento deseado de los vínculos simbólicos.</span><span class="sxs-lookup"><span data-stu-id="ac87f-136">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="ac87f-137">Establezca esta propiedad en **follow** para seguir los vínculos simbólicos y actuar sobre el destino de los vínculos.</span><span class="sxs-lookup"><span data-stu-id="ac87f-137">Set this property to **follow** to follow symbolic links and act on the links target.</span></span> <span data-ttu-id="ac87f-138">Por ejemplo, para copiar el archivo en lugar del vínculo.</span><span class="sxs-lookup"><span data-stu-id="ac87f-138">For example, copy the file instead of the link.</span></span> <span data-ttu-id="ac87f-139">Establezca esta propiedad en **manage** para actuar sobre el vínculo.</span><span class="sxs-lookup"><span data-stu-id="ac87f-139">Set this property to **manage** to act on the link.</span></span> <span data-ttu-id="ac87f-140">Por ejemplo, para copiar el propio vínculo.</span><span class="sxs-lookup"><span data-stu-id="ac87f-140">For example, copy the link itself.</span></span> <span data-ttu-id="ac87f-141">Establezca esta propiedad en **ignore** para omitir los vínculos simbólicos.</span><span class="sxs-lookup"><span data-stu-id="ac87f-141">Set this property to **ignore** to ignore symbolic links.</span></span> |
|<span data-ttu-id="ac87f-142">Grupo</span><span class="sxs-lookup"><span data-stu-id="ac87f-142">Group</span></span> |<span data-ttu-id="ac87f-143">El nombre del elemento **Group** con permisos para el archivo o directorio.</span><span class="sxs-lookup"><span data-stu-id="ac87f-143">The name of the **Group** to have permissions to the file or directory.</span></span> |
|<span data-ttu-id="ac87f-144">Modo</span><span class="sxs-lookup"><span data-stu-id="ac87f-144">Mode</span></span> |<span data-ttu-id="ac87f-145">Especifica los permisos deseados para el recurso, en notación octal o simbólica.</span><span class="sxs-lookup"><span data-stu-id="ac87f-145">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="ac87f-146">Por ejemplo, **777** o **rwxrwxrwx**.</span><span class="sxs-lookup"><span data-stu-id="ac87f-146">For example, **777** or **rwxrwxrwx**.</span></span> <span data-ttu-id="ac87f-147">Si utiliza la notación simbólica, no especifique el primer carácter que indica el directorio o archivo.</span><span class="sxs-lookup"><span data-stu-id="ac87f-147">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span> |
|<span data-ttu-id="ac87f-148">Propietario</span><span class="sxs-lookup"><span data-stu-id="ac87f-148">Owner</span></span> |<span data-ttu-id="ac87f-149">El nombre del elemento Group propietario del archivo o directorio.</span><span class="sxs-lookup"><span data-stu-id="ac87f-149">The name of the group to own the file or directory.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ac87f-150">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="ac87f-150">Common properties</span></span>

|<span data-ttu-id="ac87f-151">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ac87f-151">Property</span></span> |<span data-ttu-id="ac87f-152">Descripción</span><span class="sxs-lookup"><span data-stu-id="ac87f-152">Description</span></span> |
|---|---|
|<span data-ttu-id="ac87f-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ac87f-153">DependsOn</span></span> |<span data-ttu-id="ac87f-154">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="ac87f-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ac87f-155">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ac87f-155">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ac87f-156">Ensure</span><span class="sxs-lookup"><span data-stu-id="ac87f-156">Ensure</span></span> |<span data-ttu-id="ac87f-157">Determina si se debe comprobar si existe el archivo.</span><span class="sxs-lookup"><span data-stu-id="ac87f-157">Determines whether to check if the file exists.</span></span> <span data-ttu-id="ac87f-158">Establezca esta propiedad en **Present** para asegurarse de que el archivo exista.</span><span class="sxs-lookup"><span data-stu-id="ac87f-158">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="ac87f-159">Establézcala en **Absent** para asegurarse de que el archivo no exista.</span><span class="sxs-lookup"><span data-stu-id="ac87f-159">Set it to **Absent** to ensure the file does not exist.</span></span> <span data-ttu-id="ac87f-160">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="ac87f-160">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="ac87f-161">Información adicional</span><span class="sxs-lookup"><span data-stu-id="ac87f-161">Additional Information</span></span>

<span data-ttu-id="ac87f-162">Linux y Windows usan distintos caracteres de salto de línea en los archivos de texto de forma predeterminada, y esto puede provocar resultados inesperados cuando se configuran algunos archivos en un equipo Linux con **nxFile**.</span><span class="sxs-lookup"><span data-stu-id="ac87f-162">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with **nxFile**.</span></span> <span data-ttu-id="ac87f-163">Hay varias maneras de administrar el contenido de un archivo de Linux a la vez que se evitan los problemas provocados por los caracteres de salto de línea inesperados:</span><span class="sxs-lookup"><span data-stu-id="ac87f-163">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

1. <span data-ttu-id="ac87f-164">Copie el archivo desde un origen remoto (http, https o FTP)</span><span class="sxs-lookup"><span data-stu-id="ac87f-164">Copy the file from a remote source (http, https, or ftp)</span></span>

   <span data-ttu-id="ac87f-165">Realice una copia intermedia en un servidor web o FTP accesible para los nodos que va a configurar.</span><span class="sxs-lookup"><span data-stu-id="ac87f-165">Create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="ac87f-166">Defina la propiedad **SourcePath** del recurso **nxFile** con la dirección URL de la web o el ftp para el archivo.</span><span class="sxs-lookup"><span data-stu-id="ac87f-166">Define the **SourcePath** property in the **nxFile** resource with the web or ftp URL to the file.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      nxFile resolvConf
      {
         SourcePath = "http://10.185.85.11/conf/resolv.conf"
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
      }
   }
   ```

1. <span data-ttu-id="ac87f-167">lea el contenido del archivo del script de PowerShell con [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) tras establecer la propiedad **$OFS** que utilizará el carácter de salto de línea de Linux.</span><span class="sxs-lookup"><span data-stu-id="ac87f-167">Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the **$OFS** property to use the Linux line-break character.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      $OFS = "`n"
      $Contents = Get-Content C:\temp\resolv.conf

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = "$Contents"
      }
   }
   ```

1. <span data-ttu-id="ac87f-168">use una función de PowerShell para reemplazar los saltos de línea de Windows por caracteres de salto de línea de Linux.</span><span class="sxs-lookup"><span data-stu-id="ac87f-168">Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
      Return $outputStr
   }

   Import-DSCResource -Module nx

   Node $Node
   {
      $Contents = @'
   search contoso.com
   domain contoso.com
   nameserver 10.185.85.11
   '@
       $Contents = LinuxString $Contents

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = $Contents
      }
   }
   ```

## <a name="example"></a><span data-ttu-id="ac87f-169">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ac87f-169">Example</span></span>

<span data-ttu-id="ac87f-170">El ejemplo siguiente se asegura de que el directorio `/opt/mydir` exista y de que un archivo con el contenido especificado exista en este directorio.</span><span class="sxs-lookup"><span data-stu-id="ac87f-170">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxFile DirectoryExample
    {
        Ensure = "Present"
        DestinationPath = "/opt/mydir"
        Type = "Directory"
    }

    nxFile FileExample
    {
        Ensure = "Present"
        Destinationpath = "/opt/mydir/myfile"
        Contents=@"
#!/bin/bash`necho "hello world"`n
"@
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```