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
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Configuración de máquinas virtuales en el arranque inicial mediante DSC

> [!IMPORTANT]
> Se aplica a: Windows PowerShell 5.0

## <a name="requirements"></a>Requisitos

> [!NOTE] 
> La clave del Registro **DSCAutomationHostEnabled** descrita en este tema no está disponible en PowerShell 4.0.
> Para obtener información sobre cómo configurar nuevas máquinas virtuales en el arranque inicial de PowerShell 4.0, consulte [¿Desea configurar automáticamente su máquinas con DSC en el arranque inicial?]> (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

Para ejecutar estos ejemplos, necesitará:

- Un VHD de arranque con el que trabajar. Puede descargar una imagen ISO con una copia de evaluación de Windows Server 2016 en [Centro de evaluación de TechNet](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016). Puede encontrar instrucciones sobre cómo crear un VHD desde una imagen ISO en [Creación de discos duros virtuales de arranque](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).
- Un equipo host con Hyper-V habilitado. Para obtener más información, consulte [Introducción a Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).

  Mediante el uso de DSC, puede automatizar la instalación de software y configuración de un equipo en el arranque inicial.
  Para ello, inserte cualquier documento MOF de configuración o una metaconfiguración en un medio de arranque (por ejemplo, VHD) para que se ejecuten durante el proceso de arranque inicial.
  Este comportamiento se especifica mediante la [clave del Registro DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) bajo `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.
  De forma predeterminada, el valor de esta clave es 2, lo que permite a DSC ejecutarse durante el tiempo de arranque.

  Si no desea que DSC se ejecute durante el tiempo de arranque, establezca el valor de la clave del Registro [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) en 0.

- Inserción de un documento MOF de configuración en un VHD
- Inserción de una metaconfiguración DSC en un VHD
- Deshabilitación de DSC en un tiempo de arranque

> [!NOTE]
> Puede insertar `Pending.mof` y `MetaConfig.mof` en un equipo al mismo tiempo.
> Si ambos archivos están presentes, la configuración especificada en `MetaConfig.mof` tiene prioridad.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Inserción de un documento MOF de configuración en un VHD

Para establecer una configuración en el arranque inicial, puede insertar un documento MOF de configuración compilado en el VHD como su archivo `Pending.mof`.
Si la clave del Registro **DSCAutomationHostEnabled** está establecida en 2 (el valor predeterminado), DSC aplicará la configuración definida por `Pending.mof` cuando el equipo arranque por primera vez.

En este ejemplo, utilizaremos la siguiente configuración, que instalará IIS en el equipo nuevo:

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Para insertar el documento MOF de configuración en el VHD

1. Monte el VHD en el que desee insertar la configuración llamando al cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd). Por ejemplo:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. En un equipo que ejecute PowerShell 5.0 o posterior, guarde la configuración anterior (**SampleIISInstall**) como un archivo de script de PowerShell (.ps1).

3. En una consola de PowerShell, navegue hasta la carpeta donde guardó el archivo. ps1.

4. Ejecute los siguientes comandos de PowerShell para compilar el documento MOF (para obtener información sobre la compilación de configuraciones de DSC, consulte [Configuraciones de DSC](configurations.md):

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. Esto creará un archivo `localhost.mof` en una carpeta nueva denominada `SampleIISInstall`.
   Cambie el nombre y mueva ese archivo a la ubicación adecuada en el VHD como `Pending.mof` utilizando el cmdlet [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx). Por ejemplo:

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. Desmonte el VHD mediante una llamada al cmdlet [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd). Por ejemplo:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. Cree una VM con el VHD donde instaló el documento MOF de DSC.

Después de la instalación de sistema operativo y el arranque inicial, IIS se instalará.
Puede comprobar esto mediante una llamada al cmdlet [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx).

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Inserción de una metaconfiguración DSC en un VHD

También puede configurar un equipo para extraer una configuración en el arranque inicial insertando una metaconfiguración (consulte [Configuración del administrador de configuración local (LCM)](metaConfig.md)) en el VHD como su archivo `MetaConfig.mof`.
Si la clave del Registro **DSCAutomationHostEnabled** está establecida en 2 (el valor predeterminado), DSC aplicará la metaconfiguración definida por `MetaConfig.mof` en LCM cuando el equipo arranque por primera vez.
Si la metaconfiguración especifica que LCM debe extraer las configuraciones de un servidor de extracción, el equipo intentará extraer una configuración de ese servidor de extracción en el arranque inicial.
Para obtener información sobre la configuración de un servidor de extracción de DSC, consulte [Configuración de un servidor de extracción web de DSC](pullServer.md).

En este ejemplo, usaremos la configuración descrita en la sección anterior (**SampleIISInstall**) y la siguiente metaconfiguración:

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Para insertar el documento MOF de metaconfiguración en el VHD

1. Monte el VHD en el que desee insertar la metaconfiguración llamando al cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd). Por ejemplo:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. [Configure un servidor de extracción web de DSC](pullServer.md) y guarde la configuración **SampleIISInistall** en la carpeta apropiada.

3. En un equipo que ejecute PowerShell 5.0 o posterior, guarde la metaconfiguración anterior (**PullClientBootstrap**) como un archivo de script de PowerShell (.ps1).

4. En una consola de PowerShell, navegue hasta la carpeta donde guardó el archivo. ps1.

5. Ejecute los siguientes comandos de PowerShell para compilar el documento MOF de metaconfiguración (para obtener información sobre la compilación de configuraciones de DSC, consulte [Configuraciones de DSC](configurations.md):

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. Esto creará un archivo `localhost.meta.mof` en una carpeta nueva denominada `PullClientBootstrap`.
   Cambie el nombre y mueva ese archivo a la ubicación adecuada en el VHD como `MetaConfig.mof` utilizando el cmdlet [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx).

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. Desmonte el VHD mediante una llamada al cmdlet [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd). Por ejemplo:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. Cree una VM con el VHD donde instaló el documento MOF de DSC.

Después de la instalación de sistema operativo y el arranque inicial, DSC extraerá la configuración del servidor de extracción e IIS se instalará.
Puede comprobar esto mediante una llamada al cmdlet [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx).

## <a name="disable-dsc-at-boot-time"></a>Deshabilitación de DSC en un tiempo de arranque

De forma predeterminada, el valor de la clave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` se establece en 2, lo que permite a una configuración de DSC ejecutarse si el equipo está en estado pendiente o actual. Si no desea que una configuración se ejecute en el arranque inicial, necesita establecer el valor de esta clave en 0:

1. Monte el VHD llamando al cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd). Por ejemplo:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Cargue la subclave del Registro `HKLM\Software` desde el VHD llamando a `reg load`.

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. Vaya a `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` con el proveedor del Registro de PowerShell.

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. Cambie el valor de `DSCAutomationHostEnabled` a 0.

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. Descargar el registro ejecutando los siguientes comandos:

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>Véase también

[Configuraciones DSC](configurations.md)

[Clave del Registro DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)

[Configuración del administrador de configuración local (LCM)](metaConfig.md)

[Configuración de un servidor de extracción web de DSC](pullServer.md)
