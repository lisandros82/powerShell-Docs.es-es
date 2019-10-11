---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Empaquetado y carga de recursos en un servidor de extracción
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954382"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="1f917-103">Empaquetado y carga de recursos en un servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="1f917-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="1f917-104">En las secciones siguientes se supone que ya ha configurado un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="1f917-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="1f917-105">De no ser así, puede usar las siguientes guías:</span><span class="sxs-lookup"><span data-stu-id="1f917-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="1f917-106">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="1f917-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="1f917-107">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="1f917-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="1f917-108">Cada nodo de destino puede configurarse para descargar configuraciones y recursos, e incluso para notificar de su estado.</span><span class="sxs-lookup"><span data-stu-id="1f917-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="1f917-109">Este artículo le mostrará cómo cargar recursos para que estén disponibles para su descarga, así como configurar clientes para descargar automáticamente los recursos.</span><span class="sxs-lookup"><span data-stu-id="1f917-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="1f917-110">Cuando el nodo recibe una configuración asignada, a través de **extracción** o **inserción** (v5), descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el LCM.</span><span class="sxs-lookup"><span data-stu-id="1f917-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="1f917-111">Módulos del recurso Package</span><span class="sxs-lookup"><span data-stu-id="1f917-111">Package Resource Modules</span></span>

<span data-ttu-id="1f917-112">Cada recurso disponible para que un cliente lo descargue debe almacenarse en un archivo ".zip".</span><span class="sxs-lookup"><span data-stu-id="1f917-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="1f917-113">El siguiente ejemplo mostrará los pasos necesarios utilizando el recurso [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="1f917-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="1f917-114">Si tiene clientes que utilizan PowerShell 4.0, deberá aplanar la estructura de la carpeta de recursos y eliminar las carpetas de la versión.</span><span class="sxs-lookup"><span data-stu-id="1f917-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="1f917-115">Para obtener más información, consulte [Varias versiones de recursos](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="1f917-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="1f917-116">Puede comprimir el directorio de recursos mediante cualquier utilidad, script o método que prefiera.</span><span class="sxs-lookup"><span data-stu-id="1f917-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="1f917-117">En Windows, puede *hacer clic con el botón derecho* en el directorio "xPSDesiredStateConfiguration" y seleccionar "Enviar a" y luego "Carpeta comprimida".</span><span class="sxs-lookup"><span data-stu-id="1f917-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Clic con el botón derecho](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="1f917-119">Cambio de nombre del archivo de recursos</span><span class="sxs-lookup"><span data-stu-id="1f917-119">Naming the Resource Archive</span></span>

<span data-ttu-id="1f917-120">El archivo de recursos debe tener un nombre con este formato:</span><span class="sxs-lookup"><span data-stu-id="1f917-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="1f917-121">En el ejemplo anterior, el nombre "xPSDesiredStateConfiguration.zip" debe cambiarse a "xPSDesiredStateConfiguration_8.4.4.0.zip".</span><span class="sxs-lookup"><span data-stu-id="1f917-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="1f917-122">Creación de sumas de comprobación</span><span class="sxs-lookup"><span data-stu-id="1f917-122">Create CheckSums</span></span>

<span data-ttu-id="1f917-123">Una vez que el módulo de recursos se ha comprimido y su nombre se ha cambiado, deberá crear una **suma de comprobación**.</span><span class="sxs-lookup"><span data-stu-id="1f917-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="1f917-124">La **suma de comprobación** la usa el LCM en el cliente para determinar si el recurso se ha cambiado y debe descargarse de nuevo.</span><span class="sxs-lookup"><span data-stu-id="1f917-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="1f917-125">Puede crear una **suma de comprobación** con el cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum), como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="1f917-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="1f917-126">No se mostrará ningún resultado, pero ahora debería ver "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span><span class="sxs-lookup"><span data-stu-id="1f917-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="1f917-127">También puede ejecutar `New-DSCCheckSum` en un directorio de archivos mediante el parámetro `-Path`.</span><span class="sxs-lookup"><span data-stu-id="1f917-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="1f917-128">Si ya existe una suma de comprobación, puede forzar que se cree de nuevo con el parámetro `-Force`.</span><span class="sxs-lookup"><span data-stu-id="1f917-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="1f917-129">Dónde almacenar los archivos de recursos</span><span class="sxs-lookup"><span data-stu-id="1f917-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="1f917-130">En un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="1f917-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="1f917-131">Al configurar el servidor de extracción HTTP, como se explica en [Configuración de un servidor de extracción HTTP de DSC](pullServer.md), se especifican directorios para las claves **ModulePath** y **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="1f917-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="1f917-132">La clave **ConfigurationPath** indica dónde se deben almacenar los archivos ".mof".</span><span class="sxs-lookup"><span data-stu-id="1f917-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="1f917-133">El parámetro **ModulePath** indica dónde se deben almacenar los módulos de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="1f917-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="1f917-134">En un recurso compartido SMB</span><span class="sxs-lookup"><span data-stu-id="1f917-134">On an SMB Share</span></span>

<span data-ttu-id="1f917-135">Si especificó un valor para **ResourceRepositoryShare**, al configurar el cliente de extracción, almacene los archivos y las sumas de comprobación en el directorio **SourcePath** del bloque **ResourceRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="1f917-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

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

<span data-ttu-id="1f917-136">Si especificó solo un valor **ConfigurationRepositoryShare**, al configurar el cliente de extracción, almacene los archivos y las sumas de comprobación en el directorio **SourcePath** del bloque **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="1f917-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="1f917-137">Actualización de los recursos</span><span class="sxs-lookup"><span data-stu-id="1f917-137">Updating resources</span></span>

<span data-ttu-id="1f917-138">Puede forzar que un nodo actualice sus recursos cambiando el número de versión en el nombre del archivo o creando una nueva suma de comprobación.</span><span class="sxs-lookup"><span data-stu-id="1f917-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="1f917-139">El cliente de extracción buscará las versiones más recientes de los recursos necesarios, así como las sumas de comprobación actualizadas, cuando se actualiza el LCM.</span><span class="sxs-lookup"><span data-stu-id="1f917-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f917-140">Vea también</span><span class="sxs-lookup"><span data-stu-id="1f917-140">See also</span></span>

- [<span data-ttu-id="1f917-141">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="1f917-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="1f917-142">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="1f917-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
