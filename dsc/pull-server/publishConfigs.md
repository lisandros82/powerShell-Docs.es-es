---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Publicar en un servidor de extracción mediante identificadores de configuración (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402401"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="02e45-103">Publicar en un servidor de extracción mediante identificadores de configuración (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="02e45-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="02e45-104">Las secciones siguientes se suponen que ya ha configurado un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="02e45-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="02e45-105">Si no ha configurado el servidor de incorporación de cambios, puede usar a las siguientes guías:</span><span class="sxs-lookup"><span data-stu-id="02e45-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="02e45-106">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="02e45-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="02e45-107">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="02e45-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="02e45-108">Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado.</span><span class="sxs-lookup"><span data-stu-id="02e45-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="02e45-109">En este artículo le mostrará cómo cargar recursos para que estén disponibles para descargarse y configurar clientes para descargar automáticamente los recursos.</span><span class="sxs-lookup"><span data-stu-id="02e45-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="02e45-110">Cuando el nodo recibe una configuración asignada, a través de **extraer** o **Push** (v5), se descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el LCM.</span><span class="sxs-lookup"><span data-stu-id="02e45-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="02e45-111">Compilar las configuraciones</span><span class="sxs-lookup"><span data-stu-id="02e45-111">Compile Configurations</span></span>

<span data-ttu-id="02e45-112">El primer paso para almacenar [configuraciones](../configurations/configurations.md) en un servidor de incorporación de cambios, es compilarlos en archivos ".mof".</span><span class="sxs-lookup"><span data-stu-id="02e45-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="02e45-113">Para realizar una configuración genérica y es aplicable a más clientes, use `localhost` en el bloque de nodo.</span><span class="sxs-lookup"><span data-stu-id="02e45-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="02e45-114">El ejemplo siguiente muestra un shell de configuración que usa `localhost` en lugar de un nombre de cliente específico.</span><span class="sxs-lookup"><span data-stu-id="02e45-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="02e45-115">Una vez que ha compilado su configuración genérico, debe tener un archivo "localhost.mof".</span><span class="sxs-lookup"><span data-stu-id="02e45-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="02e45-116">Cambiar el nombre del archivo MOF</span><span class="sxs-lookup"><span data-stu-id="02e45-116">Renaming the MOF file</span></span>

<span data-ttu-id="02e45-117">Puede almacenar archivos de configuración "MOF" en un servidor de extracción por **ConfigurationName** o **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="02e45-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="02e45-118">Dependiendo de cómo se va a configurar los clientes de incorporación de cambios, puede elegir una sección a continuación para cambiar correctamente el nombre de los archivos compilados ".mof".</span><span class="sxs-lookup"><span data-stu-id="02e45-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="02e45-119">Identificadores de configuración (GUID)</span><span class="sxs-lookup"><span data-stu-id="02e45-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="02e45-120">Tendrá que cambiar el nombre de su archivo de "localhost.mof" a "<GUID>.mof" archivo.</span><span class="sxs-lookup"><span data-stu-id="02e45-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="02e45-121">Puede crear uno aleatorio **Guid** en el ejemplo a continuación, o mediante el [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02e45-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="02e45-122">Salida de muestra</span><span class="sxs-lookup"><span data-stu-id="02e45-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="02e45-123">A continuación, puede cambiar el nombre de su archivo de ".mof" mediante cualquier método aceptable.</span><span class="sxs-lookup"><span data-stu-id="02e45-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="02e45-124">El ejemplo siguiente, se usa el [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02e45-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="02e45-125">Para obtener más información sobre el uso de **GUID** en su entorno, consulte [planear GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="02e45-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="02e45-126">Nombres de la configuración</span><span class="sxs-lookup"><span data-stu-id="02e45-126">Configuration Names</span></span>

<span data-ttu-id="02e45-127">Tendrá que cambiar el nombre de su archivo de "localhost.mof" a "<Configuration Name>.mof" archivo.</span><span class="sxs-lookup"><span data-stu-id="02e45-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="02e45-128">En el ejemplo siguiente, se usa el nombre de configuración de la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="02e45-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="02e45-129">A continuación, puede cambiar el nombre de su archivo de ".mof" mediante cualquier método aceptable.</span><span class="sxs-lookup"><span data-stu-id="02e45-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="02e45-130">El ejemplo siguiente, se usa el [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02e45-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="02e45-131">Creación de la suma de comprobación</span><span class="sxs-lookup"><span data-stu-id="02e45-131">Create the CheckSum</span></span>

<span data-ttu-id="02e45-132">Cada archivo de "MOF" almacena en un recurso compartido SMB o servidor de extracción debe tener un archivo asociado ".checksum".</span><span class="sxs-lookup"><span data-stu-id="02e45-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="02e45-133">Este archivo permite que los clientes saber cuándo el archivo asociado ".mof" ha cambiado y debe descargarse de nuevo.</span><span class="sxs-lookup"><span data-stu-id="02e45-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="02e45-134">Puede crear un **suma de comprobación** con el [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02e45-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="02e45-135">También puede ejecutar `New-DSCCheckSum` frente a un directorio de archivos mediante el `-Path` parámetro.</span><span class="sxs-lookup"><span data-stu-id="02e45-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="02e45-136">Si ya existe una suma de comprobación, puede forzarlo a volver a crearse con el `-Force` parámetro.</span><span class="sxs-lookup"><span data-stu-id="02e45-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="02e45-137">En el ejemplo siguiente se especifica un directorio que contiene el archivo "MOF" de la sección anterior y usa el `-Force` parámetro.</span><span class="sxs-lookup"><span data-stu-id="02e45-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="02e45-138">No se mostrará ningún resultado, pero ahora debería ver un "<GUID or Configuration Name>. mof.checksum" archivo.</span><span class="sxs-lookup"><span data-stu-id="02e45-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="02e45-139">Dónde almacenar los archivos MOF y las sumas de comprobación</span><span class="sxs-lookup"><span data-stu-id="02e45-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="02e45-140">En un servidor de extracción de DSC</span><span class="sxs-lookup"><span data-stu-id="02e45-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="02e45-141">Al configurar el servidor de extracción HTTP, como se explica en [configurar un servidor de extracción de DSC HTTP](pullServer.md), especificar directorios de la **ModulePath** y **ConfigurationPath** claves.</span><span class="sxs-lookup"><span data-stu-id="02e45-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="02e45-142">El **ConfigurationPath** clave indica dónde se deben almacenar los archivos "MOF".</span><span class="sxs-lookup"><span data-stu-id="02e45-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="02e45-143">El **ConfigurationPath** indica dónde se deben almacenar los archivos de "MOF" y ".checksum" archivos.</span><span class="sxs-lookup"><span data-stu-id="02e45-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="02e45-144">En un recurso compartido SMB</span><span class="sxs-lookup"><span data-stu-id="02e45-144">On an SMB Share</span></span>

<span data-ttu-id="02e45-145">Al configurar un cliente de extracción para usar un recurso compartido SMB, especifique un **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="02e45-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="02e45-146">Todos los archivos "MOF" y ".checksum", a continuación, se deben almacenar en el **SourcePath** directorio desde el **ConfigurationRepositoryShare** bloque.</span><span class="sxs-lookup"><span data-stu-id="02e45-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="02e45-147">Pasos a seguir</span><span class="sxs-lookup"><span data-stu-id="02e45-147">Next Steps</span></span>

<span data-ttu-id="02e45-148">A continuación, querrá configurar los clientes de extracción para extraer la configuración especificada.</span><span class="sxs-lookup"><span data-stu-id="02e45-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="02e45-149">Para obtener más información, consulte una de las siguientes guías:</span><span class="sxs-lookup"><span data-stu-id="02e45-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="02e45-150">Configurar un cliente de incorporación de cambios mediante identificadores de configuración (v4)</span><span class="sxs-lookup"><span data-stu-id="02e45-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="02e45-151">Configurar un cliente de incorporación de cambios mediante identificadores de configuración (v5)</span><span class="sxs-lookup"><span data-stu-id="02e45-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="02e45-152">Configurar un cliente de extracción mediante nombres de configuración (v5)</span><span class="sxs-lookup"><span data-stu-id="02e45-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="02e45-153">Vea también</span><span class="sxs-lookup"><span data-stu-id="02e45-153">See also</span></span>

- [<span data-ttu-id="02e45-154">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="02e45-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="02e45-155">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="02e45-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="02e45-156">Paquete y los recursos de carga para un servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="02e45-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
