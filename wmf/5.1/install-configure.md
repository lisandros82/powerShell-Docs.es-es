---
title: "Instalación y configuración de WMF 5.1 (versión preliminar)"
ms.date: 2016-05-16
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
contributor: kriscv
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 21f26830cdc20a90ce48aa09bc7013d733242ae9
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="install-and-configure-wmf-51-preview"></a>Instalación y configuración de WMF 5.1 (versión preliminar) #

## <a name="install-net-46"></a>Instalar .NET 4.6
Debe instalar .NET Framework 4.6 para usar WMF 5.1. Es necesario para habilitar las nuevas características de firma de catálogo, que afectan a varias áreas de carga de módulo y script en WMF 5.1. 

[.NET Framework 4.6 está disponible como KB 3045560](https://support.microsoft.com/en-us/kb/3045560). Las instrucciones de instalación están disponibles en la ubicación de descarga.

> **Nota**: Es un problema conocido que el instalador de la versión preliminar de WMF 5.1 no detecta el requisito de .NET 4.6, por lo que podrá instalar la versión preliminar de WMF 5.1 antes de instalar .NET 4.6. Nuestras pruebas han demostrado que puede instalar .NET 4.6 después de instalar la versión preliminar de WMF 5.1. La versión final de WMF 5.1 comprobará correctamente este requisito previo antes de la instalación. 

## <a name="download-and-install-the-wmf-51-preview"></a>Descargar e instalar la versión preliminar de WMF 5.1

Descargue el paquete WMF 5.1 para el sistema operativo y la arquitectura en la que se va a instalar en:

| Sistema operativo       | Requisitos previos | Vínculos de paquete             |
|------------------------|---------------|---------------------------|
| Windows Server 2012 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586)|
| Windows Server 2012    | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823587)|
| Windows Server 2008 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> Actualización de seguridad para la [firma de código SHA-2](https://technet.microsoft.com/en-us/library/security/3033929) | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) |
| Windows 8.1            | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | **x64:** [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586) </br> **x86:** [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823589) |
| Windows 7 SP1          | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> Actualización de seguridad para la [firma de código SHA-2](https://technet.microsoft.com/en-us/library/security/3033929) | **x64:** [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) </br> **x86:** [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823590) |


## <a name="install-wmf-51-from-windows-explorer-or-file-explorer-in-windows-server-2012-r2-or-windows-81"></a>Instalación de WMF 5.1 desde el Explorador de Windows (o el Explorador de archivos en Windows Server 2012 R2 o Windows 8.1)

1. Desplácese a la carpeta en la que descargó el archivo MSU.

2. Haga doble clic en el archivo MSU para ejecutarlo.

## <a name="install-wmf-51-from-the-command-prompt"></a>Instalación de WMF 5.1 desde el símbolo del sistema##

1. Después de descargar el paquete correcto para la arquitectura del equipo, abra una ventana del símbolo del sistema con derechos de usuario elevados (Ejecutar como administrador). En las opciones de instalación de Server Core de Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1, el símbolo del sistema se abre de forma predeterminada con derechos de usuario elevados.

2. Cambie los directorios a la carpeta en la que descargó o copió el paquete de instalación de WMF 5.1.

3. Ejecute uno de los siguientes comandos:
    - En los equipos que están ejecutando Windows Server 2012 R2 o Windows 8.1 x64, ejecute `Win8.1AndW2K12R2-KB3156422-x64.msu /quiet`.
    - En los equipos que están ejecutando Windows Server 2012, ejecute `W2K12-KB3156423-x64.msu /quiet`.
    - En los equipos que están ejecutando Windows Server 2008 R2 SP1 o Windows 7 SP1 x64, ejecute `Win7AndW2K8R2-KB3156424-x64.msu /quiet`.
    - En los equipos que están ejecutando Windows 8.1 x86, ejecute `Win8.1-KB3156422-x86.msu /quiet`.
    - En los equipos que están ejecutando Windows 7 SP1 x86, ejecute `Win7-KB3156424-x86.msu /quiet`.

## <a name="additional-installation-notes-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Notas de instalación adicionales para Windows Server 2008 R2 SP1 y Windows 7 SP1##
La instalación de WMF 5.1 en Windows Server 2008 R2 SP1 o Windows 7 SP1, requiere la instalación de:
- Service Pack más reciente.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855)
- WMF 5.1 requiere [Microsoft .NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560). Puede instalar Microsoft .NET Framework 4.6 mediante las instrucciones que se proporcionan en la ubicación de descarga.
- Actualización de seguridad para la [firma de código SHA-2](https://technet.microsoft.com/en-us/library/security/3033929). Es necesaria para usar los nuevos cmdlets de PowerShell para los archivos de catálogo de Windows. 

> **Dependencia de WinRM**: la configuración de estado deseado (DSC) de Windows PowerShell depende de WinRM. WinRM no está habilitado de forma predeterminada en Windows Server 2008 R2 y Windows 7. Para habilitar WinRM, ejecute `Set-WSManQuickConfig` en una sesión de Windows PowerShell con permisos elevados.

