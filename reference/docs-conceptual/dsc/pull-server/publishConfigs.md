---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Publicación en un servidor de extracción mediante identificadores de configuración (v4/v5)
ms.openlocfilehash: c258814f480b91eba75c7ce9abf70c558f1f469e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953602"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="8f6bf-103">Publicación en un servidor de extracción mediante identificadores de configuración (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="8f6bf-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="8f6bf-104">En las secciones siguientes se supone que ya ha configurado un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="8f6bf-105">De no ser así, puede usar las siguientes guías:</span><span class="sxs-lookup"><span data-stu-id="8f6bf-105">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="8f6bf-106">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="8f6bf-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="8f6bf-107">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="8f6bf-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="8f6bf-108">Cada nodo de destino puede configurarse para descargar configuraciones y recursos, e incluso para notificar de su estado.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="8f6bf-109">Este artículo le muestra cómo cargar recursos para que estén disponibles para su descarga, así como configurar clientes para descargar automáticamente los recursos.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-109">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="8f6bf-110">Cuando el nodo recibe una configuración asignada, a través de **extracción** o **inserción** (v5), descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el Administrador de configuración local (LCM).</span><span class="sxs-lookup"><span data-stu-id="8f6bf-110">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="8f6bf-111">Compilación de configuraciones</span><span class="sxs-lookup"><span data-stu-id="8f6bf-111">Compile configurations</span></span>

<span data-ttu-id="8f6bf-112">El primer paso para almacenar [configuraciones](../configurations/configurations.md) en un servidor de extracción es compilarlas en archivos `.mof`.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="8f6bf-113">Para realizar una configuración genérica y aplicable a más clientes, use `localhost` en el bloque Node.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="8f6bf-114">El ejemplo siguiente muestra un shell de configuración que usa `localhost` en lugar de un nombre de cliente específico.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="8f6bf-115">Una vez que haya compilado su configuración genérica, debe tener un archivo `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-115">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="8f6bf-116">Cambio de nombre del archivo MOF</span><span class="sxs-lookup"><span data-stu-id="8f6bf-116">Renaming the MOF file</span></span>

<span data-ttu-id="8f6bf-117">Puede almacenar archivos de configuración `.mof` en un servidor de extracción por **ConfigurationName** o **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-117">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="8f6bf-118">Dependiendo de cómo planee configurar sus clientes de extracción, puede elegir una sección a continuación para cambiar adecuadamente el nombre de los archivos `.mof` compilados.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="8f6bf-119">Identificadores de configuración (GUID)</span><span class="sxs-lookup"><span data-stu-id="8f6bf-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="8f6bf-120">Deberá cambiar el nombre de su archivo `localhost.mof` a `<GUID>.mof`.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-120">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="8f6bf-121">Puede crear un **GUID** aleatorio mediante el ejemplo siguiente, o mediante el cmdlet [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).</span><span class="sxs-lookup"><span data-stu-id="8f6bf-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="8f6bf-122">Salida de muestra</span><span class="sxs-lookup"><span data-stu-id="8f6bf-122">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="8f6bf-123">A continuación, puede cambiar el nombre de su archivo `.mof` mediante cualquier método aceptable.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-123">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="8f6bf-124">En el ejemplo siguiente, se usa el cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).</span><span class="sxs-lookup"><span data-stu-id="8f6bf-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="8f6bf-125">Para obtener más información sobre el uso de **GUID** en su entorno, vea el tema sobre la [planificación de GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="8f6bf-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="8f6bf-126">Nombres de la configuración</span><span class="sxs-lookup"><span data-stu-id="8f6bf-126">Configuration names</span></span>

<span data-ttu-id="8f6bf-127">Deberá cambiar el nombre de su archivo `localhost.mof` a `<Configuration Name>.mof`.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-127">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="8f6bf-128">En el ejemplo siguiente, se usa el nombre de configuración de la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="8f6bf-129">A continuación, puede cambiar el nombre de su archivo `.mof` mediante cualquier método aceptable.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-129">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="8f6bf-130">En el ejemplo siguiente, se usa el cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).</span><span class="sxs-lookup"><span data-stu-id="8f6bf-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="8f6bf-131">Creación de la suma de comprobación</span><span class="sxs-lookup"><span data-stu-id="8f6bf-131">Create the checkSum</span></span>

<span data-ttu-id="8f6bf-132">Cada archivo `.mof` almacenado en un servidor de extracción o recurso compartido SMB necesita un archivo `.checksum` asociado.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-132">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="8f6bf-133">Este archivo permite a los clientes saber cuándo ha cambiado el archivo `.mof` asociado y debe descargarse nuevamente.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-133">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="8f6bf-134">Puede crear una **suma de comprobación** con el cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum).</span><span class="sxs-lookup"><span data-stu-id="8f6bf-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="8f6bf-135">También puede ejecutar `New-DSCCheckSum` en un directorio de archivos mediante el parámetro `-Path`.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="8f6bf-136">Si ya existe una suma de comprobación, puede forzar que se cree de nuevo con el parámetro `-Force`.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="8f6bf-137">En el ejemplo siguiente se especifica un directorio que contiene el archivo `.mof` de la sección anterior y usa el parámetro `-Force`.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-137">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="8f6bf-138">No se mostrará ningún resultado, pero ahora debería ver un archivo `<GUID or Configuration Name>.mof.checksum`.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-138">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="8f6bf-139">Dónde almacenar los archivos MOF y las sumas de comprobación</span><span class="sxs-lookup"><span data-stu-id="8f6bf-139">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="8f6bf-140">En un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="8f6bf-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="8f6bf-141">Al configurar el servidor de extracción HTTP, como se explica en [Configuración de un servidor de extracción HTTP de DSC](pullServer.md), se especifican directorios para las claves **ModulePath** y **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="8f6bf-142">La clave **ModulePath** indica dónde deben almacenarse los archivos `.zip` empaquetados de un módulo.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-142">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="8f6bf-143">**ConfigurationPath** indica dónde se deben almacenar los archivos `.mof` y `.checksum`.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-143">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="8f6bf-144">En un recurso compartido SMB</span><span class="sxs-lookup"><span data-stu-id="8f6bf-144">On an SMB share</span></span>

<span data-ttu-id="8f6bf-145">Al configurar un cliente de extracción para usar un recurso compartido de SMB, especifique un valor para **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span>
<span data-ttu-id="8f6bf-146">Todos los archivos `.mof` y `.checksum` deben almacenarse en el directorio **SourcePath** del bloque **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-146">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="8f6bf-147">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="8f6bf-147">Next steps</span></span>

<span data-ttu-id="8f6bf-148">A continuación, querrá configurar los clientes de extracción para extraer la configuración especificada.</span><span class="sxs-lookup"><span data-stu-id="8f6bf-148">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="8f6bf-149">Para obtener más información, consulte una de las guías siguientes:</span><span class="sxs-lookup"><span data-stu-id="8f6bf-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="8f6bf-150">Configuración de un cliente de extracción mediante id. de configuración (v4)</span><span class="sxs-lookup"><span data-stu-id="8f6bf-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="8f6bf-151">Configuración de un cliente de extracción mediante id. de configuración (v5)</span><span class="sxs-lookup"><span data-stu-id="8f6bf-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="8f6bf-152">Configuración de un cliente de extracción mediante nombres de configuración (v5)</span><span class="sxs-lookup"><span data-stu-id="8f6bf-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="8f6bf-153">Vea también</span><span class="sxs-lookup"><span data-stu-id="8f6bf-153">See also</span></span>

- [<span data-ttu-id="8f6bf-154">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="8f6bf-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="8f6bf-155">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="8f6bf-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="8f6bf-156">Empaquetado y carga de recursos en un servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="8f6bf-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
