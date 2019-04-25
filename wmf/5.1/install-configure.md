---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: Instalación y configuración de WMF 5.1
ms.openlocfilehash: c439d0851189a89a81fa38194632dc54475a001d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085004"
---
# <a name="install-and-configure-wmf-51"></a>Instalación y configuración de WMF 5.1

## <a name="download-and-install-the-wmf-51-package"></a>Descarga e instalación del paquete WMF 5.1

Descargue el paquete WMF 5.1 para el sistema operativo y la arquitectura en la que se va a instalar en:

| Sistema operativo       | Requisitos previos           | Vínculos de paquete                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Instalación de WMF 5.1 para Windows Server 2008 R2 y Windows 7

> [!NOTE]
> Las instrucciones de instalación de Windows Server 2008 R2 y Windows 7 han cambiado y se diferencian de las instrucciones para los otros paquetes. Las instrucciones de instalación de Windows Server 2012 R2, Windows Server 2012 y Windows 8.1 se indican a continuación.

**Instalación de WMF 5.1 para Windows Server 2008 R2 y Windows 7**

1. Desplácese a la carpeta en la que descargó el archivo ZIP.

2. Haga clic con el botón derecho en el archivo ZIP y seleccione "Extraer todo...". El archivo Zip contiene dos archivos: un archivo MSU y el archivo de script Install-WMF5.1.PS1.
Después de desempaquetar el archivo ZIP, puede copiar el contenido en cualquier máquina que ejecuta Windows 7 o Windows Server 2008 R2.

3. Después de extraer el contenido del archivo ZIP, abra PowerShell como administrador y navegue hasta la carpeta que contiene el contenido del archivo ZIP.

4. Ejecute el script Install-Wmf5.1.ps1 en esa carpeta y siga las instrucciones. Este script comprobará los requisitos previos en la máquina local e instalará WMF 5.1 si se cumplen esos requisitos. A continuación, se enumeran los requisitos previos.

Install-WMF5.1.ps1 toma los parámetros siguientes para facilitar la automatización de la instalación en Windows Server 2008 R2 y Windows 7:

- AcceptEula: cuando se incluye este parámetro, el CLUF se acepta automáticamente y no se muestra.
- AllowRestart: este parámetro solo se utiliza si se especifica AcceptEula. Si se incluye este parámetro y se requiere un reinicio después de instalar WMF 5.1, el reinicio se realizará sin pedir confirmación, inmediatamente después de finaliza la instalación.

**Requisitos previos de WMF 5.1 para Windows Server 2008 R2 SP1 y Windows 7 SP1**

La instalación de WMF 5.1 en Windows Server 2008 R2 SP1 o Windows 7 SP1, requiere lo siguiente:
- Debe instalarse el service pack más reciente.
- WMF 3.0 **no debe** instalarse. La instalación de WMF 5.1 en WMF 3.0 provocará la pérdida de PSModulePath, lo que puede producir errores en otras aplicaciones. Antes de instalar WMF 5.1, debe desinstalar WMF 3.0 o guardar PSModulePath y restaurarlo manualmente una vez completada la instalación de WMF 5.1.
- WMF 5.1 requiere al menos [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
Puede instalar Microsoft .NET Framework 4.5.2 mediante las instrucciones que se proporcionan en la ubicación de descarga.

**Dependencia de WinRM**

La configuración de estado deseado (DSC) de Windows PowerShell depende de WinRM.
WinRM no está habilitado de forma predeterminada en Windows Server 2008 R2 y Windows 7.
Para habilitar WinRM, ejecute `Set-WSManQuickConfig` en una sesión de Windows PowerShell con permisos elevados.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Instalación de WMF 5.1 para Windows Server 2012 R2, Windows 2012 y Windows 8.1

**Instalación desde el Explorador de Windows (o el Explorador de archivos en Windows Server 2012 R2 o Windows 8.1)**

1. Desplácese a la carpeta en la que descargó el archivo MSU.
2. Haga doble clic en el archivo MSU para ejecutarlo.

**Instalación desde el símbolo del sistema**

1. Después de descargar el paquete correcto para la arquitectura del equipo, abra una ventana del símbolo del sistema con derechos de usuario elevados (Ejecutar como administrador). En las opciones de instalación de Server Core de Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1, el símbolo del sistema se abre de forma predeterminada con derechos de usuario elevados.
2. Cambie los directorios a la carpeta en la que descargó o copió el paquete de instalación de WMF 5.1.
3. Ejecute uno de los siguientes comandos:
   - En los equipos que están ejecutando Windows Server 2012 R2 o Windows 8.1 x64, ejecute `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
   - En los equipos que están ejecutando Windows Server 2012, ejecute `W2K12-KB3191565-x64.msu /quiet`.
   - En los equipos que están ejecutando Windows 8.1 x86, ejecute `Win8.1-KB3191564-x86.msu /quiet`.

> [!NOTE]
> La instalación de WMF 5.1 requiere un reinicio. Con la opción `/quiet` se reiniciará el sistema sin advertencias.
> Utilice la opción `/norestart` para evitar reiniciar el sistema. Sin embargo, no se instalará WMF 5.1 hasta que haya reiniciado el sistema.
