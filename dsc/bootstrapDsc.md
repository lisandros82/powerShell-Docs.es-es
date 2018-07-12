---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuración de máquinas virtuales en el arranque inicial mediante DSC
ms.openlocfilehash: 2f228a38379d1e65b31c03594e876f7226474fc3
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893359"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="27754-103">Configuración de máquinas virtuales en el arranque inicial mediante DSC</span><span class="sxs-lookup"><span data-stu-id="27754-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27754-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="27754-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="27754-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27754-105">Requirements</span></span>

> [!NOTE] 
> <span data-ttu-id="27754-106">La clave del Registro **DSCAutomationHostEnabled** descrita en este tema no está disponible en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="27754-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="27754-107">Para obtener información sobre cómo configurar nuevas máquinas virtuales en el arranque inicial de PowerShell 4.0, consulte [¿Desea configurar automáticamente su máquinas con DSC en el arranque inicial?]> (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="27754-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?]> (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="27754-108">Para ejecutar estos ejemplos, necesitará:</span><span class="sxs-lookup"><span data-stu-id="27754-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="27754-109">Un VHD de arranque con el que trabajar.</span><span class="sxs-lookup"><span data-stu-id="27754-109">A bootable VHD to work with.</span></span> <span data-ttu-id="27754-110">Puede descargar una imagen ISO con una copia de evaluación de Windows Server 2016 en [Centro de evaluación de TechNet](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="27754-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> <span data-ttu-id="27754-111">Puede encontrar instrucciones sobre cómo crear un VHD desde una imagen ISO en [Creación de discos duros virtuales de arranque](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="27754-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="27754-112">Un equipo host con Hyper-V habilitado.</span><span class="sxs-lookup"><span data-stu-id="27754-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="27754-113">Para obtener más información, consulte [Introducción a Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="27754-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="27754-114">Mediante el uso de DSC, puede automatizar la instalación de software y configuración de un equipo en el arranque inicial.</span><span class="sxs-lookup"><span data-stu-id="27754-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="27754-115">Para ello, inserte cualquier documento MOF de configuración o una metaconfiguración en un medio de arranque (por ejemplo, VHD) para que se ejecuten durante el proceso de arranque inicial.</span><span class="sxs-lookup"><span data-stu-id="27754-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="27754-116">Este comportamiento se especifica mediante la [clave del Registro DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) bajo `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.</span><span class="sxs-lookup"><span data-stu-id="27754-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.</span></span>
  <span data-ttu-id="27754-117">De forma predeterminada, el valor de esta clave es 2, lo que permite a DSC ejecutarse durante el tiempo de arranque.</span><span class="sxs-lookup"><span data-stu-id="27754-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="27754-118">Si no desea que DSC se ejecute durante el tiempo de arranque, establezca el valor de la clave del Registro [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) en 0.</span><span class="sxs-lookup"><span data-stu-id="27754-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="27754-119">Inserción de un documento MOF de configuración en un VHD</span><span class="sxs-lookup"><span data-stu-id="27754-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="27754-120">Inserción de una metaconfiguración DSC en un VHD</span><span class="sxs-lookup"><span data-stu-id="27754-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="27754-121">Deshabilitación de DSC en un tiempo de arranque</span><span class="sxs-lookup"><span data-stu-id="27754-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="27754-122">Puede insertar `Pending.mof` y `MetaConfig.mof` en un equipo al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="27754-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="27754-123">Si ambos archivos están presentes, la configuración especificada en `MetaConfig.mof` tiene prioridad.</span><span class="sxs-lookup"><span data-stu-id="27754-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="27754-124">Inserción de un documento MOF de configuración en un VHD</span><span class="sxs-lookup"><span data-stu-id="27754-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="27754-125">Para establecer una configuración en el arranque inicial, puede insertar un documento MOF de configuración compilado en el VHD como su archivo `Pending.mof`.</span><span class="sxs-lookup"><span data-stu-id="27754-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="27754-126">Si la clave del Registro **DSCAutomationHostEnabled** está establecida en 2 (el valor predeterminado), DSC aplicará la configuración definida por `Pending.mof` cuando el equipo arranque por primera vez.</span><span class="sxs-lookup"><span data-stu-id="27754-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="27754-127">En este ejemplo, utilizaremos la siguiente configuración, que instalará IIS en el equipo nuevo:</span><span class="sxs-lookup"><span data-stu-id="27754-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="27754-128">Para insertar el documento MOF de configuración en el VHD</span><span class="sxs-lookup"><span data-stu-id="27754-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="27754-129">Monte el VHD en el que desee insertar la configuración llamando al cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="27754-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="27754-130">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="27754-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="27754-131">En un equipo que ejecute PowerShell 5.0 o posterior, guarde la configuración anterior (**SampleIISInstall**) como un archivo de script de PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="27754-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="27754-132">En una consola de PowerShell, navegue hasta la carpeta donde guardó el archivo. ps1.</span><span class="sxs-lookup"><span data-stu-id="27754-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="27754-133">Ejecute los siguientes comandos de PowerShell para compilar el documento MOF (para obtener información sobre la compilación de configuraciones de DSC, consulte [Configuraciones de DSC](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="27754-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="27754-134">Esto creará un archivo `localhost.mof` en una carpeta nueva denominada `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="27754-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="27754-135">Cambie el nombre y mueva ese archivo a la ubicación adecuada en el VHD como `Pending.mof` utilizando el cmdlet [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx).</span><span class="sxs-lookup"><span data-stu-id="27754-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span> <span data-ttu-id="27754-136">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="27754-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="27754-137">Desmonte el VHD mediante una llamada al cmdlet [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd).</span><span class="sxs-lookup"><span data-stu-id="27754-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="27754-138">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="27754-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="27754-139">Cree una VM con el VHD donde instaló el documento MOF de DSC.</span><span class="sxs-lookup"><span data-stu-id="27754-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="27754-140">Después de la instalación de sistema operativo y el arranque inicial, IIS se instalará.</span><span class="sxs-lookup"><span data-stu-id="27754-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="27754-141">Puede comprobar esto mediante una llamada al cmdlet [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx).</span><span class="sxs-lookup"><span data-stu-id="27754-141">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="27754-142">Inserción de una metaconfiguración DSC en un VHD</span><span class="sxs-lookup"><span data-stu-id="27754-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="27754-143">También puede configurar un equipo para extraer una configuración en el arranque inicial insertando una metaconfiguración (consulte [Configuración del administrador de configuración local (LCM)](metaConfig.md)) en el VHD como su archivo `MetaConfig.mof`.</span><span class="sxs-lookup"><span data-stu-id="27754-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="27754-144">Si la clave del Registro **DSCAutomationHostEnabled** está establecida en 2 (el valor predeterminado), DSC aplicará la metaconfiguración definida por `MetaConfig.mof` en LCM cuando el equipo arranque por primera vez.</span><span class="sxs-lookup"><span data-stu-id="27754-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="27754-145">Si la metaconfiguración especifica que LCM debe extraer las configuraciones de un servidor de extracción, el equipo intentará extraer una configuración de ese servidor de extracción en el arranque inicial.</span><span class="sxs-lookup"><span data-stu-id="27754-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="27754-146">Para obtener información sobre la configuración de un servidor de extracción de DSC, consulte [Configuración de un servidor de extracción web de DSC](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="27754-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="27754-147">En este ejemplo, usaremos la configuración descrita en la sección anterior (**SampleIISInstall**) y la siguiente metaconfiguración:</span><span class="sxs-lookup"><span data-stu-id="27754-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="27754-148">Para insertar el documento MOF de metaconfiguración en el VHD</span><span class="sxs-lookup"><span data-stu-id="27754-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="27754-149">Monte el VHD en el que desee insertar la metaconfiguración llamando al cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="27754-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="27754-150">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="27754-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="27754-151">[Configure un servidor de extracción web de DSC](pullServer.md) y guarde la configuración **SampleIISInistall** en la carpeta apropiada.</span><span class="sxs-lookup"><span data-stu-id="27754-151">[Set up a DSC web pull server](pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="27754-152">En un equipo que ejecute PowerShell 5.0 o posterior, guarde la metaconfiguración anterior (**PullClientBootstrap**) como un archivo de script de PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="27754-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="27754-153">En una consola de PowerShell, navegue hasta la carpeta donde guardó el archivo. ps1.</span><span class="sxs-lookup"><span data-stu-id="27754-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="27754-154">Ejecute los siguientes comandos de PowerShell para compilar el documento MOF de metaconfiguración (para obtener información sobre la compilación de configuraciones de DSC, consulte [Configuraciones de DSC](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="27754-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="27754-155">Esto creará un archivo `localhost.meta.mof` en una carpeta nueva denominada `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="27754-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="27754-156">Cambie el nombre y mueva ese archivo a la ubicación adecuada en el VHD como `MetaConfig.mof` utilizando el cmdlet [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx).</span><span class="sxs-lookup"><span data-stu-id="27754-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="27754-157">Desmonte el VHD mediante una llamada al cmdlet [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd).</span><span class="sxs-lookup"><span data-stu-id="27754-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="27754-158">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="27754-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="27754-159">Cree una VM con el VHD donde instaló el documento MOF de DSC.</span><span class="sxs-lookup"><span data-stu-id="27754-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="27754-160">Después de la instalación de sistema operativo y el arranque inicial, DSC extraerá la configuración del servidor de extracción e IIS se instalará.</span><span class="sxs-lookup"><span data-stu-id="27754-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="27754-161">Puede comprobar esto mediante una llamada al cmdlet [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx).</span><span class="sxs-lookup"><span data-stu-id="27754-161">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="27754-162">Deshabilitación de DSC en un tiempo de arranque</span><span class="sxs-lookup"><span data-stu-id="27754-162">Disable DSC at boot time</span></span>

<span data-ttu-id="27754-163">De forma predeterminada, el valor de la clave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` se establece en 2, lo que permite a una configuración de DSC ejecutarse si el equipo está en estado pendiente o actual.</span><span class="sxs-lookup"><span data-stu-id="27754-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="27754-164">Si no desea que una configuración se ejecute en el arranque inicial, necesita establecer el valor de esta clave en 0:</span><span class="sxs-lookup"><span data-stu-id="27754-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="27754-165">Monte el VHD llamando al cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="27754-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="27754-166">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="27754-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="27754-167">Cargue la subclave del Registro `HKLM\Software` desde el VHD llamando a `reg load`.</span><span class="sxs-lookup"><span data-stu-id="27754-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="27754-168">Vaya a `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` con el proveedor del Registro de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27754-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. <span data-ttu-id="27754-169">Cambie el valor de `DSCAutomationHostEnabled` a 0.</span><span class="sxs-lookup"><span data-stu-id="27754-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="27754-170">Descargar el registro ejecutando los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="27754-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="27754-171">Véase también</span><span class="sxs-lookup"><span data-stu-id="27754-171">See Also</span></span>

[<span data-ttu-id="27754-172">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="27754-172">DSC Configurations</span></span>](configurations.md)

[<span data-ttu-id="27754-173">Clave del Registro DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="27754-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="27754-174">Configuración del administrador de configuración local (LCM)</span><span class="sxs-lookup"><span data-stu-id="27754-174">Configuring the Local Configuration Manager (LCM)</span></span>](metaConfig.md)

[<span data-ttu-id="27754-175">Configuración de un servidor de extracción web de DSC</span><span class="sxs-lookup"><span data-stu-id="27754-175">Setting up a DSC web pull server</span></span>](pullServer.md)
