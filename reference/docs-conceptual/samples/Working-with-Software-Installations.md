---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Trabajar con instalaciones de software
ms.openlocfilehash: d164064418ad7a0209166c81a7c3cc32a9db300a
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737158"
---
# <a name="working-with-software-installations"></a>Trabajar con instalaciones de software

Puede usar la clase **Win32_Product** de WMI para acceder a las aplicaciones diseñadas para usar Windows Installer, si bien no todas las aplicaciones de hoy en día usan Windows Installer.
Por lo general, las aplicaciones que usan otras rutinas de instalación no se administran con Windows Installer.
Las técnicas concretas para trabajar con esas aplicaciones dependen del instalador de software y de las decisiones tomadas por el desarrollador de la aplicación. Por ejemplo, las aplicaciones que se instalan copiando los archivos a una carpeta del equipo no se suelen poder administrar con las técnicas aquí descritas. Puede administrar estas aplicaciones como archivos y carpetas recurriendo a las técnicas descritas en [Trabajar con archivos y carpetas](Working-with-Files-and-Folders.md).

> [!CAUTION]
> La clase **Win32_Product** no está optimizada para consultas. Las consultas que utilizan filtros con caracteres comodín provocan que WMI utilice el proveedor MSI para enumerar todos los productos instalados y, a continuación, analice la lista completa de forma secuencial para controlar el filtro. Esto también inicia una comprobación de coherencia de los paquetes instalados, verificando y reparando la instalación. La validación es un proceso lento y puede provocar errores en los registros de eventos. Para obtener más información, consulte el [artículo de KB 974524](https://support.microsoft.com/help/974524).

## <a name="listing-windows-installer-applications"></a>Lista de aplicaciones de Windows Installer

Para confeccionar una lista de las aplicaciones instaladas con Windows Installer en un sistema local o remoto, use esta sencilla consulta WMI:

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

Para mostrar todas las propiedades del objeto **Win32_Product**, use el parámetro **Properties** de los cmdlets de formato, como el cmdlet `Format-List`, con un valor de `*` (todos).

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.5 (x64)
Version               : 16.84.26919
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.5 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.5 (x64)
IdentifyingNumber     : {BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20181105
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}v16.84.26919\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\4f97a771.msi
PackageCache          : C:\WINDOWS\Installer\4f97a771.msi
PackageCode           : {9A271A10-039D-49EA-8D24-043D91B9F915}
PackageName           : dotnet-runtime-2.1.5-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Otra posibilidad es usar el parámetro `Get-CimInstance` **Filter** para seleccionar solo Microsoft .NET Framework 2.0 Runtime. El valor del parámetro **Filter** usa la sintaxis del lenguaje de consulta de WMI (WQL), no la sintaxis de Windows PowerShell. Por ejemplo:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

Para mostrar solo las propiedades que le interesen, use el parámetro **Property** de los cmdlets de formato.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.5 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\4f97a771.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>Enumerar todas las aplicaciones no instalables

La mayoría de las aplicaciones estándar registran un desinstalador con Windows, por lo que podemos trabajar con ellas localmente buscándolas en el Registro de Windows. No hay ninguna manera garantizada de encontrar todas las aplicaciones en un sistema. Sin embargo, es posible buscar todos los programas en las listas que se muestran en **Agregar o quitar programas** en la clave del Registro siguiente:

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

Podemos examinar esta clave para buscar aplicaciones. Podemos hacer que la clave Uninstall sea más fácil de ver si asignamos una unidad de PowerShell a esta ubicación del Registro:

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

Ya tenemos una unidad denominada "Uninstall:" que se puede usar para buscar instalaciones de aplicaciones de forma cómoda y rápida. Podemos hallar el número de aplicaciones instaladas contando el número de claves del Registro en la desinstalación: Unidad de PowerShell:

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

Podemos realizar más búsquedas en esta lista de aplicaciones mediante diversas técnicas, comenzando por `Get-ChildItem`. Use el siguiente comando para obtener una lista de aplicaciones y guardarlas en la variable `$UninstallableApplications`:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

Para ver los valores de las entradas del Registro en las claves del Registro bajo Uninstall, use el método GetValue en las claves del Registro. El valor del método es el nombre de la entrada del Registro.

Por ejemplo, use el siguiente comando para buscar los nombres para mostrar de las aplicaciones en la clave Uninstall:

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

No hay ninguna garantía de que estos valores sean únicos. En el siguiente ejemplo, aparecen dos elementos instalados como "Windows Media Encoder 9 Series":

```powershell
$UninstallableApplications | Where-Object -FilterScript {
  $_.GetValue("DisplayName") -eq "Microsoft Silverlight"
}
```

```Output
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name                           Property
----                           --------
{89F4137D-6C26-4A84-BDB8-2E5A4 AuthorizedCDFPrefix :
BB71E00}                       Comments            :
                               Contact             :
                               DisplayVersion      : 5.1.50918.0
                               HelpLink            : http://go.microsoft.com/fwlink/?LinkID=91955
                               HelpTelephone       :
                               InstallDate         : 20190115
                               InstallLocation     : C:\Program Files\Microsoft Silverlight\
                               InstallSource       : c:\ef64c54526db9c34cd477c103e68a254\
                               ModifyPath          : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               NoModify            : 1
                               NoRepair            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 236432
                               UninstallString     : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 5
                               VersionMinor        : 1
                               WindowsInstaller    : 1
                               Version             : 84002534
                               Language            : 1033
                               DisplayName         : Microsoft Silverlight
                               sEstimatedSize2     : 79214
```

## <a name="installing-applications"></a>Instalación de aplicaciones

Puede usar la clase **Win32_Product** para instalar paquetes de Windows Installer, tanto de forma local como remota.

> [!NOTE]
> Para instalar una aplicación, debe iniciar PowerShell con la opción "Ejecutar como administrador".

En las instalaciones remotas, use una ruta de red de convención de nomenclatura Universal (UNC) para especificar la ruta de acceso al paquete .msi, ya que el subsistema WMI no entiende las rutas de acceso de PowerShell. Por ejemplo, para instalar el paquete NewPackage.msi ubicado en el recurso compartido de red `\\AppServ\dsp` en el equipo remoto PC01, escriba el siguiente comando en el símbolo del sistema de PowerShell:

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Las aplicaciones que no usan la tecnología de Windows Installer pueden tener métodos específicos de aplicación para la implementación automática. Consulte la documentación de la aplicación o el sistema de soporte técnico del proveedor de la aplicación.

## <a name="removing-applications"></a>Desinstalación de aplicaciones

El proceso de desinstalación de un paquete de Windows Installer mediante PowerShell funciona aproximadamente del mismo modo que la instalación de un paquete. En este ejemplo, el paquete que se va a desinstalar se selecciona por su nombre; en algunos casos, probablemente sea más fácil filtrar con **IdentifyingNumber**:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

Desinstalar otras aplicaciones no es tan sencillo, aun cuando se haga localmente. Encontraremos las cadenas de desinstalación de línea de comandos de estas aplicaciones extrayendo la propiedad **UninstallString**.
Este método funciona con aplicaciones de Windows Installer y con los programas antiguos que aparecen bajo la clave Uninstall:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Si lo desea, puede filtrar el resultado por el nombre para mostrar:

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Sin embargo, puede que estas cadenas no se puedan usar directamente desde el símbolo del sistema de PowerShell sin realizar alguna modificación.

## <a name="upgrading-windows-installer-applications"></a>Actualización de aplicaciones de Windows Installer

Para actualizar una aplicación, es necesario conocer su nombre y la ruta de acceso al paquete de actualización de la aplicación. Con esa información, podrá actualizar una aplicación con un solo comando de PowerShell:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
