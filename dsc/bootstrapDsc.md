---
title: "Configuración de máquinas virtuales en el arranque inicial mediante DSC"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 77ca52b130a432f79b9b4399afa5480e0daec983
ms.openlocfilehash: 471684ffe62edfb10005f0ade162222eef4c9a32

---

>Se aplica a: Windows PowerShell 5.0

>**Nota:** la clave del Registro **DSCAutomationHostEnabled** descrita en este tema no está disponible en PowerShell 4.0. Para obtener información sobre cómo configurar nuevas máquinas virtuales en el arranque inicial de PowerShell 4.0, consulte [¿Desea configurar automáticamente su máquinas con DSC en el arranque inicial?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

# <a name="configure-a-virtual-machines-at-initial-bootup-by-using-dsc"></a>Configuración de máquinas virtuales en el arranque inicial mediante DSC

## <a name="requirements"></a>Requisitos

Para ejecutar estos ejemplos, necesitará:

- Un VHD de arranque con el que trabajar. Puede descargar una imagen ISO con una copia de evaluación de Windows Server 2016 en   [Centro de evaluación de TechNet](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016). Puede encontrar instrucciones sobre cómo crear un VHD desde una imagen ISO en [Creación de discos duros virtuales de arranque](https://technet.microsoft.com/en-us/library/gg318049.aspx).
- Un equipo host con Hyper-V habilitado. Para obtener más información, consulte [Introducción a Hyper-V](https://technet.microsoft.com/library/hh831531.aspx).

Mediante el uso de DSC, puede automatizar la instalación de software y configuración de un equipo en el arranque inicial. Para ello, inserte cualquier documento MOF de configuración o una metaconfiguración en un medio de arranque (por ejemplo, VHD) para que se ejecuten durante el proceso de arranque inicial. Este comportamiento se especifica mediante la clave del Registro [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**. De forma predeterminada, el valor de esta clave es 2, lo que permite a DSC ejecutarse durante el tiempo de arranque.

Si no desea que DSC se ejecute durante el tiempo de arranque, establezca el valor de la clave del Registro [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) en 0.


- [Inserción de un documento MOF de configuración en un VHD](##Inject-a-configuration-MOF-document-into-a-VHD)
- [Inserción de una metaconfiguración DSC en un VHD](##Inject-a-DSC-metaconfiguration-into-a-VHD)
- [Deshabilitación de DSC en un tiempo de arranque](##Disable-DSC-at-boot-time)

>**Nota:** puede insertar `Pending.mof` y `MetaConfig.mof` en un equipo al mismo tiempo. Si ambos archivos están presentes, la configuración especificada en `MetaConfig.mof` tiene prioridad.


## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Inserción de un documento MOF de configuración en un VHD

Para establecer una configuración en el arranque inicial, puede insertar un documento MOF de configuración compilado en el VHD como su archivo `Pending.mof`. Si la clave del Registro **DSCAutomationHostEnabled** está establecida en 2 (el valor predeterminado), DSC aplicará la configuración definida por `Pending.mof` cuando el equipo arranque por primera vez.

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

1. Monte el VHD en el que desee insertar la configuración llamando al cmdlet [Mount-VHD](). Por ejemplo:  `Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd`
1. En un equipo que ejecute PowerShell 5.0 o posterior, guarde la configuración anterior (**SampleIISInstall**) como un archivo de script de PowerShell (.ps1).
1. En una consola de PowerShell, navegue hasta la carpeta donde guardó el archivo. ps1.
1. Ejecute los siguientes comandos de PowerShell para compilar el documento MOF (para obtener información sobre la compilación de configuraciones de DSC, consulte [Configuraciones de DSC](configurations.md):
    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```
1. Esto creará un archivo `localhost.mof` en una carpeta nueva denominada `SampleIISInstall`. Cambie el nombre y mueva ese archivo a la ubicación adecuada en el VHD como `Pending.mof` 
    utilizando el cmdlet []Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx). Por ejemplo:

        `Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\Sytem32\Configuration\Pending.mof`
1. Desmonte el VHD mediante una llamada al cmdlet [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx). Por ejemplo:  `Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd`
1. Cree una VM con el VHD donde instaló el documento MOF de DSC. Después de la instalación de sistema operativo y el arranque inicial, IIS se instalará.
    Puede comprobar esto mediante una llamada al cmdlet [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx).

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Inserción de una metaconfiguración DSC en un VHD

También puede configurar un equipo para extraer una configuración en el arranque inicial insertando una metaconfiguración (consulte [Configuración del administrador de configuración local (LCM)](metaConfig.md)) en el VHD como su archivo `MetaConfig.mof`. Si la clave del Registro **DSCAutomationHostEnabled** está establecida en 2 (el valor predeterminado), DSC aplicará la metaconfiguración definida por `MetaConfig.mof` en LCM cuando el equipo arranque por primera vez. Si la metaconfiguración especifica que LCM debe extraer las configuraciones de un servidor de extracción, el equipo intentará extraer una configuración de ese servidor de extracción en el arranque inicial. Para obtener información sobre la configuración de un servidor de extracción de DSC, consulte [Configuración de un servidor de extracción web de DSC](pullServer.md).

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

1. Monte el VHD en el que desee insertar la metaconfiguración llamando al cmdlet [Mount-VHD](). Por ejemplo:  `Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd`
1. [Configure un servidor de extracción web de DSC](pullServer.md) y guarde la configuración **SampleIISInistall** en la carpeta apropiada.
1. En un equipo que ejecute PowerShell 5.0 o posterior, guarde la metaconfiguración anterior (**PullClientBootstrap**) como un archivo de script de PowerShell (.ps1).
1. En una consola de PowerShell, navegue hasta la carpeta donde guardó el archivo. ps1.
1. Ejecute los siguientes comandos de PowerShell para compilar el documento MOF de metaconfiguración (para obtener información sobre la compilación de configuraciones de DSC, consulte [Configuraciones de DSC](configurations.md):
    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```
1. Esto creará un archivo `localhost.meta.mof` en una carpeta nueva denominada `PullClientBootstrap`. Cambie el nombre y mueva ese archivo a la ubicación adecuada en el VHD como `MetaConfig.mof` 
    utilizando el cmdlet []Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx). Por ejemplo:  `Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof`
1. Desmonte el VHD mediante una llamada al cmdlet [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx). Por ejemplo:  `Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd`
1. Cree una VM con el VHD donde instaló el documento MOF de DSC. Después de la instalación de sistema operativo y el arranque inicial, DSC extraerá la configuración del servidor de extracción e IIS se instalará. Puede comprobar esto mediante una llamada al cmdlet [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx).

## <a name="disable-dsc-at-boot-time"></a>Deshabilite DSC en el tiempo de arranque.

De forma predeterminada, la clave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** se establece en 2, lo que permite que una configuración DSC se ejecute si el equipo está en estado pendiente o actual. Si no desea que una configuración se ejecute en el arranque inicial, necesita establecer el valor de esta clave en 0:

1. Monte el VHD llamando al cmdlet [Mount-VHD](). Por ejemplo:  `Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd`
2. Cargue la subclave del registro **HKLM\Software** desde el VHD llamando a `reg load`. Por ejemplo, si  `reg load HKLM\Vhd E:\Windows\System32\Config\Software`
3. Navegue hasta **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*** usando el proveedor de registro de PowerShell. Por ejemplo:  `Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
4. Cambie el valor de `DSCAutomationHostEnabled` a 0:  `Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0`
5. Descargar el registro ejecutando los siguientes comandos:
    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```
## <a name="see-also"></a>Véase también

- [Configuraciones DSC](configurations.md)
- [Clave del Registro DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)
- [Configuración del administrador de configuración local (LCM)](metaConfig.md)
- [Configuración de un servidor de extracción web de DSC](pullServer.md)















<!--HONumber=Oct16_HO4-->


