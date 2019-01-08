---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Paquete y los recursos de carga para un servidor de extracción
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402298"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="5e0a7-103">Paquete y los recursos de carga para un servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="5e0a7-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="5e0a7-104">Las secciones siguientes se suponen que ya ha configurado un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="5e0a7-105">Si no ha configurado el servidor de incorporación de cambios, puede usar a las siguientes guías:</span><span class="sxs-lookup"><span data-stu-id="5e0a7-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="5e0a7-106">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="5e0a7-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="5e0a7-107">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="5e0a7-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="5e0a7-108">Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="5e0a7-109">En este artículo le mostrará cómo cargar recursos para que estén disponibles para descargarse y configurar clientes para descargar automáticamente los recursos.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="5e0a7-110">Cuando el nodo recibe una configuración asignada, a través de **extraer** o **Push** (v5), se descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el LCM.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="5e0a7-111">Módulos de recursos del paquete</span><span class="sxs-lookup"><span data-stu-id="5e0a7-111">Package Resource Modules</span></span>

<span data-ttu-id="5e0a7-112">Cada recurso disponible para el cliente descargue debe almacenarse en un archivo "zip".</span><span class="sxs-lookup"><span data-stu-id="5e0a7-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="5e0a7-113">El ejemplo siguiente mostrará los pasos necesarios mediante el [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) recursos.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="5e0a7-114">Si tiene cualquier cliente que emplee PowerShell 4.0, se deberá flaten la estructura de carpetas de recursos y quite las carpetas de versión.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="5e0a7-115">Para obtener más información, consulte [varias versiones de recursos](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="5e0a7-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="5e0a7-116">Puede comprimir el directorio de recursos mediante cualquier utilidad, un script o un método que prefiera.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="5e0a7-117">En Windows, puede *haga* en el directorio "xPSDesiredStateConfiguration" y seleccione "Enviar a" y "Carpeta comprimida".</span><span class="sxs-lookup"><span data-stu-id="5e0a7-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Clic con el botón derecho](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="5e0a7-119">El archivo de recursos de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="5e0a7-119">Naming the Resource Archive</span></span>

<span data-ttu-id="5e0a7-120">El archivo de recursos debe llamarse con el formato siguiente:</span><span class="sxs-lookup"><span data-stu-id="5e0a7-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="5e0a7-121">En el ejemplo anterior, "xPSDesiredStateConfiguration.zip" debe ser "xPSDesiredStateConfiguration_8.4.4.0.zip" cuyo nombre ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="5e0a7-122">Cree sumas de comprobación</span><span class="sxs-lookup"><span data-stu-id="5e0a7-122">Create CheckSums</span></span>

<span data-ttu-id="5e0a7-123">Una vez que el módulo de recursos se ha comprimido y se ha cambiado el nombre, deberá crear un **suma de comprobación**.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="5e0a7-124">El **suma de comprobación** se usa el LCM en el cliente, para determinar si el recurso se ha cambiado y debe descargarse de nuevo.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="5e0a7-125">Puede crear un **suma de comprobación** con el [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="5e0a7-126">No se mostrará ningún resultado, pero ahora debería ver un "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span><span class="sxs-lookup"><span data-stu-id="5e0a7-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="5e0a7-127">También puede ejecutar `New-DSCCheckSum` frente a un directorio de archivos mediante el `-Path` parámetro.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="5e0a7-128">Si ya existe una suma de comprobación, puede forzarlo a volver a crearse con el `-Force` parámetro.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="5e0a7-129">Dónde almacenar los archivos de recursos</span><span class="sxs-lookup"><span data-stu-id="5e0a7-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="5e0a7-130">En un servidor de extracción de DSC</span><span class="sxs-lookup"><span data-stu-id="5e0a7-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="5e0a7-131">Al configurar el servidor de extracción HTTP, como se explica en [configurar un servidor de extracción de DSC HTTP](pullServer.md), especificar directorios de la **ModulePath** y **ConfigurationPath** claves.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="5e0a7-132">El **ConfigurationPath** clave indica dónde se deben almacenar los archivos "MOF".</span><span class="sxs-lookup"><span data-stu-id="5e0a7-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="5e0a7-133">El **ModulePath** indica dónde se deben almacenar los módulos de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="5e0a7-134">En un recurso compartido SMB</span><span class="sxs-lookup"><span data-stu-id="5e0a7-134">On an SMB Share</span></span>

<span data-ttu-id="5e0a7-135">Si ha especificado un **ResourceRepositoryShare**, al configurar el cliente de extracción, el almacén de archivos y las sumas de comprobación en el **SourcePath** directorio desde el **ResourceRepositoryShare** bloque.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="5e0a7-136">Si sólo especifica una **ConfigurationRepositoryShare**, al configurar el cliente de extracción, el almacén de archivos y las sumas de comprobación en el **SourcePath** directorio desde el  **ConfigurationRepositoryShare** bloque.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="5e0a7-137">Actualización de los recursos</span><span class="sxs-lookup"><span data-stu-id="5e0a7-137">Updating resources</span></span>

<span data-ttu-id="5e0a7-138">Puede forzar un nodo para actualizar sus recursos cambiando el número de versión en el nombre del archivo, o mediante la creación de una nueva suma de comprobación.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="5e0a7-139">El cliente de incorporación de cambios buscará las versiones más recientes de los recursos necesarios, así como actualizar las sumas de comprobación, cuando se actualiza el LCM.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e0a7-140">Vea también</span><span class="sxs-lookup"><span data-stu-id="5e0a7-140">See also</span></span>

- [<span data-ttu-id="5e0a7-141">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="5e0a7-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="5e0a7-142">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="5e0a7-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
