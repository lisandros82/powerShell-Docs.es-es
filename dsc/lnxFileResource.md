---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso nxFile de DSC para Linux
ms.openlocfilehash: f1eb98092049ae837d144ccf99a84fe5614144e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189863"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="90085-103">Recurso nxFile de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="90085-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="90085-104">El recurso **nxFile** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar archivos y directorios en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="90085-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="90085-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="90085-105">Syntax</span></span>

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="90085-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="90085-106">Properties</span></span>

|  <span data-ttu-id="90085-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="90085-107">Property</span></span> |  <span data-ttu-id="90085-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="90085-108">Description</span></span> |
|---|---|
| <span data-ttu-id="90085-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="90085-109">DestinationPath</span></span>| <span data-ttu-id="90085-110">Especifica la ubicación donde desea garantizar el estado de un archivo o directorio.</span><span class="sxs-lookup"><span data-stu-id="90085-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="90085-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="90085-111">SourcePath</span></span>| <span data-ttu-id="90085-112">Especifica la ruta de acceso de la que se copiará el recurso de archivo o carpeta.</span><span class="sxs-lookup"><span data-stu-id="90085-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="90085-113">Esta ruta de acceso puede ser una ruta de acceso local o una dirección URL `http/https/ftp`.</span><span class="sxs-lookup"><span data-stu-id="90085-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="90085-114">Las direcciones URL remotas `http/https/ftp` solo se admiten cuando el valor de la propiedad **Type** propiedad es file.</span><span class="sxs-lookup"><span data-stu-id="90085-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="90085-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="90085-115">Ensure</span></span>| <span data-ttu-id="90085-116">Determina si se debe comprobar si existe el archivo.</span><span class="sxs-lookup"><span data-stu-id="90085-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="90085-117">Establezca esta propiedad en "Present" para asegurarse de que el archivo exista.</span><span class="sxs-lookup"><span data-stu-id="90085-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="90085-118">Establézcala en "Absent" para asegurarse de que el archivo no exista.</span><span class="sxs-lookup"><span data-stu-id="90085-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="90085-119">El valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="90085-119">The default value is "Present".</span></span>|
| <span data-ttu-id="90085-120">Tipo</span><span class="sxs-lookup"><span data-stu-id="90085-120">Type</span></span>| <span data-ttu-id="90085-121">Especifica si el recurso que se está configurando es un directorio o un archivo.</span><span class="sxs-lookup"><span data-stu-id="90085-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="90085-122">Establezca esta propiedad en "directory" para indicar que el recurso es un directorio.</span><span class="sxs-lookup"><span data-stu-id="90085-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="90085-123">Establézcala en "file" para indicar que el recurso es un archivo.</span><span class="sxs-lookup"><span data-stu-id="90085-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="90085-124">El valor predeterminado es "file".</span><span class="sxs-lookup"><span data-stu-id="90085-124">The default value is "file"</span></span>|
| <span data-ttu-id="90085-125">Contenido</span><span class="sxs-lookup"><span data-stu-id="90085-125">Contents</span></span>| <span data-ttu-id="90085-126">Especifica el contenido de un archivo, como una cadena determinada.</span><span class="sxs-lookup"><span data-stu-id="90085-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="90085-127">Checksum</span><span class="sxs-lookup"><span data-stu-id="90085-127">Checksum</span></span>| <span data-ttu-id="90085-128">Define el tipo que se usará cuando se determine si dos archivos son iguales.</span><span class="sxs-lookup"><span data-stu-id="90085-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="90085-129">Si no se especifica **Checksum**, solo se usa el nombre del archivo o directorio para la comparación.</span><span class="sxs-lookup"><span data-stu-id="90085-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="90085-130">Los valores son: "ctime", "mtime" o "md5".</span><span class="sxs-lookup"><span data-stu-id="90085-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="90085-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="90085-131">Recurse</span></span>| <span data-ttu-id="90085-132">Indica si se incluyen los subdirectorios.</span><span class="sxs-lookup"><span data-stu-id="90085-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="90085-133">Establezca esta propiedad en **$true** para indicar que quiere que los subdirectorios se incluyan.</span><span class="sxs-lookup"><span data-stu-id="90085-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="90085-134">El valor predeterminado es **$false**.</span><span class="sxs-lookup"><span data-stu-id="90085-134">The default is **$false**.</span></span> <span data-ttu-id="90085-135">**Nota**: Esta propiedad solo es válida cuando la propiedad **Type** está establecida en directory.</span><span class="sxs-lookup"><span data-stu-id="90085-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="90085-136">Force</span><span class="sxs-lookup"><span data-stu-id="90085-136">Force</span></span>| <span data-ttu-id="90085-137">Determinadas operaciones de archivos (por ejemplo, sobrescribir un archivo o eliminar un directorio que no está vacío) provocarán un error.</span><span class="sxs-lookup"><span data-stu-id="90085-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="90085-138">Si se usa la propiedad **Force**, se invalidan estos errores.</span><span class="sxs-lookup"><span data-stu-id="90085-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="90085-139">El valor predeterminado es **$false**.</span><span class="sxs-lookup"><span data-stu-id="90085-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="90085-140">Vínculos</span><span class="sxs-lookup"><span data-stu-id="90085-140">Links</span></span>| <span data-ttu-id="90085-141">Especifica el comportamiento deseado de los vínculos simbólicos.</span><span class="sxs-lookup"><span data-stu-id="90085-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="90085-142">Establezca esta propiedad en "follow" para seguir los vínculos simbólicos y actuar sobre el destino de los vínculos (por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="90085-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="90085-143">copiar el archivo en lugar del vínculo).</span><span class="sxs-lookup"><span data-stu-id="90085-143">copy the file instead of the link).</span></span> <span data-ttu-id="90085-144">Establezca esta propiedad en "manage" para actuar sobre el vínculo (por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="90085-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="90085-145">copiar el propio vínculo).</span><span class="sxs-lookup"><span data-stu-id="90085-145">copy the link itself).</span></span> <span data-ttu-id="90085-146">Establezca esta propiedad en "ignore" para omitir los vínculos simbólicos.</span><span class="sxs-lookup"><span data-stu-id="90085-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="90085-147">Grupo</span><span class="sxs-lookup"><span data-stu-id="90085-147">Group</span></span>| <span data-ttu-id="90085-148">El nombre del elemento **Group** propietario del archivo o directorio.</span><span class="sxs-lookup"><span data-stu-id="90085-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="90085-149">Modo</span><span class="sxs-lookup"><span data-stu-id="90085-149">Mode</span></span>| <span data-ttu-id="90085-150">Especifica los permisos deseados para el recurso, en notación octal o simbólica.</span><span class="sxs-lookup"><span data-stu-id="90085-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="90085-151">(por ejemplo, 777 o rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="90085-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="90085-152">Si utiliza la notación simbólica, no especifique el primer carácter que indica el directorio o archivo.</span><span class="sxs-lookup"><span data-stu-id="90085-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="90085-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="90085-153">DependsOn</span></span> | <span data-ttu-id="90085-154">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="90085-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="90085-155">Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="90085-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="90085-156">Información adicional</span><span class="sxs-lookup"><span data-stu-id="90085-156">Additional Information</span></span>


<span data-ttu-id="90085-157">Linux y Windows usan distintos caracteres de salto de línea en los archivos de texto de forma predeterminada, y esto puede provocar resultados inesperados cuando se configuran algunos archivos en un equipo Linux con __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="90085-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="90085-158">Hay varias maneras de administrar el contenido de un archivo de Linux a la vez que se evitan los problemas provocados por los caracteres de salto de línea inesperados:</span><span class="sxs-lookup"><span data-stu-id="90085-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="90085-159">Paso 1: copie el archivo desde un origen remoto (http, https o ftp). Cree un archivo en Linux con el contenido que desee y realice una copia intermedia en un servidor web o ftp accesible para los nodos que va a configurar.</span><span class="sxs-lookup"><span data-stu-id="90085-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="90085-160">Defina la propiedad __SourcePath__ del recurso __nxFile__ con la dirección URL de la web o el ftp para el archivo.</span><span class="sxs-lookup"><span data-stu-id="90085-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

```
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


<span data-ttu-id="90085-161">Paso 2: lea el contenido del archivo del script de PowerShell con [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) después de establecer la propiedad __$OFS__ que utilizará el carácter de salto de línea de Linux.</span><span class="sxs-lookup"><span data-stu-id="90085-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


```
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


<span data-ttu-id="90085-162">Paso 3: use una función de PowerShell para reemplazar los saltos de línea de Windows por caracteres de salto de línea de Linux.</span><span class="sxs-lookup"><span data-stu-id="90085-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
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

## <a name="example"></a><span data-ttu-id="90085-163">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="90085-163">Example</span></span>

<span data-ttu-id="90085-164">El ejemplo siguiente se asegura de que el directorio `/opt/mydir` exista y de que un archivo con el contenido especificado exista en este directorio.</span><span class="sxs-lookup"><span data-stu-id="90085-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```
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
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```