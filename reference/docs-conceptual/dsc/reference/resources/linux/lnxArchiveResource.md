---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso nxArchive de DSC para Linux
ms.openlocfilehash: 77b52ad68344ba791501baeb585a5001cc97a126
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953332"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="fb41a-103">Recurso nxArchive de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="fb41a-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="fb41a-104">El recurso **nxArchive** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para desempaquetar archivos de almacenamiento (.tar, .zip) en una ruta de acceso específica de un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="fb41a-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb41a-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fb41a-105">Syntax</span></span>

```Syntax
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="fb41a-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="fb41a-106">Properties</span></span>

|<span data-ttu-id="fb41a-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="fb41a-107">Property</span></span> |<span data-ttu-id="fb41a-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="fb41a-108">Description</span></span> |
|---|---|
|<span data-ttu-id="fb41a-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="fb41a-109">SourcePath</span></span> |<span data-ttu-id="fb41a-110">Especifica la ruta de acceso de origen del archivo.</span><span class="sxs-lookup"><span data-stu-id="fb41a-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="fb41a-111">Debe ser un archivo .tar, .zip o .tar.gz.</span><span class="sxs-lookup"><span data-stu-id="fb41a-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
|<span data-ttu-id="fb41a-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="fb41a-112">DestinationPath</span></span> |<span data-ttu-id="fb41a-113">Especifica la ubicación donde quiere garantizar que se extraiga el contenido del archivo.</span><span class="sxs-lookup"><span data-stu-id="fb41a-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="fb41a-114">Checksum</span><span class="sxs-lookup"><span data-stu-id="fb41a-114">Checksum</span></span> |<span data-ttu-id="fb41a-115">Define el tipo que se utilizará al determinar si se ha actualizado el archivo de origen.</span><span class="sxs-lookup"><span data-stu-id="fb41a-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="fb41a-116">Los valores son: **ctime**, **mtime** o **md5**.</span><span class="sxs-lookup"><span data-stu-id="fb41a-116">Values are: **ctime**, **mtime**, or **md5**.</span></span> <span data-ttu-id="fb41a-117">El valor predeterminado es **md5**.</span><span class="sxs-lookup"><span data-stu-id="fb41a-117">The default value is **md5**.</span></span> |
|<span data-ttu-id="fb41a-118">Force</span><span class="sxs-lookup"><span data-stu-id="fb41a-118">Force</span></span> |<span data-ttu-id="fb41a-119">Determinadas operaciones de archivos (por ejemplo, sobrescribir un archivo o eliminar un directorio que no está vacío) provocarán un error.</span><span class="sxs-lookup"><span data-stu-id="fb41a-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="fb41a-120">Si se usa la propiedad **Force**, se invalidan estos errores.</span><span class="sxs-lookup"><span data-stu-id="fb41a-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="fb41a-121">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="fb41a-121">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="fb41a-122">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="fb41a-122">Common properties</span></span>

|<span data-ttu-id="fb41a-123">Propiedad</span><span class="sxs-lookup"><span data-stu-id="fb41a-123">Property</span></span> |<span data-ttu-id="fb41a-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="fb41a-124">Description</span></span> |
|---|---|
|<span data-ttu-id="fb41a-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fb41a-125">DependsOn</span></span> |<span data-ttu-id="fb41a-126">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="fb41a-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fb41a-127">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="fb41a-127">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="fb41a-128">Ensure</span><span class="sxs-lookup"><span data-stu-id="fb41a-128">Ensure</span></span> |<span data-ttu-id="fb41a-129">Determina si se debe comprobar si existe el contenido del archivo en **Destination**.</span><span class="sxs-lookup"><span data-stu-id="fb41a-129">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="fb41a-130">Establezca esta propiedad en **Present** para asegurarse de que el contenido exista.</span><span class="sxs-lookup"><span data-stu-id="fb41a-130">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="fb41a-131">Establézcala en **Absent** para asegurarse de que no exista.</span><span class="sxs-lookup"><span data-stu-id="fb41a-131">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="fb41a-132">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="fb41a-132">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="fb41a-133">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fb41a-133">Example</span></span>

<span data-ttu-id="fb41a-134">En el ejemplo siguiente se muestra cómo usar el recurso **nxArchive** para asegurarse de que el contenido de un archivo llamado `website.tar` exista y se extraiga en un destino determinado.</span><span class="sxs-lookup"><span data-stu-id="fb41a-134">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```powershell
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = "http://release.contoso.com/releases/website.tar"
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = "mtime"
}

nxArchive SyncWebDir
{
   SourcePath = "/usr/release/staging/website.tar"
   DestinationPath = "/usr/local/apache2/htdocs/"
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```