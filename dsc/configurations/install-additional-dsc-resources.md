---
ms.date: 12/12/2018
keywords: dsc,powershell,resource,gallery,setup
title: Instalación de recursos de DSC adicionales
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080091"
---
# <a name="install-additional-dsc-resources"></a>Instalación de recursos de DSC adicionales

PowerShell incluye varios recursos listos para usar para Desired State Configuration (DSC). El módulo **PSDesiredStateConfiguration** contiene todos los estos recursos disponibles en su instancia específica de PowerShell.

Se trata de una lista de los recursos listos para usar incluidos en PowerShell 4.0 y una descripción de las capacidades del recurso.

> [!NOTE]
> No es una lista completa, ya que la cantidad de estos recursos ha aumentado con cada versión de PowerShell.

|Recurso  |Descripción  |
|---------|---------|
|**File**|Controla el estado de los archivos y directorios. Copia los archivos de un **origen** a un **destino** y los actualiza cuando el **origen** cambia mediante la comparación de fechas, sumas de comprobación y algoritmos hash.|
|**Archive**|Desempaqueta los archivos y una ubicación especificada. Valida los archivos con una determinada **suma de comprobación**.|
|**Environment**|Administra variables de entorno.|
|**Grupo**|Administra grupos locales y controla la pertenencia al grupo.|
|**Log**|Escribe mensajes en el registro de eventos `Microsoft-Windows-Desired State Configuration/Analytic`.|
|**Package**|Instala o desinstala los paquetes mediante **Arguments**, **LogPath**, **ReturnCode** u otras configuraciones.|
|**Registry**|Administra los valores y claves del Registro.|
|**Script**|Le permite diseñar sus propios bloques de script [get-test-set](../resources/get-test-set.md).|
|**Service**|Configura los servicios de Windows.|
|**Usuario** |Administra los usuarios y atributos locales.|
|**WindowsFeature**|Administra roles y características.|
|**WindowsProcess**|Configura procesos de Windows.|

Los recursos listos para usar suponen un buen punto de partida para las operaciones comunes. Si tales recursos no satisfacen sus necesidades, puede escribir su propio [recurso personalizado](../resources/authoringResource.md). Antes de escribir un recurso personalizado para solucionar el problema, debe examinar el gran número de recursos de DSC que ya se han creado por Microsoft y la comunidad de PowerShell.

Puede encontrar los recursos de DSC tanto en la [Galería de PowerShell](https://www.powershellgallery.com/) como en [GitHub](https://github.com/). También puede instalar los recursos de DSC directamente desde la consola de PowerShell mediante [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Instalación de PowerShellGet

Para determinar si ya tiene **PowerShell** get o para obtener ayuda para instalarlo, consulte la guía siguiente: [Instalación de PowerShellGet](/powershell/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>Búsqueda de recursos de DSC mediante PowerShellGet

Una vez que **PowerShellGet** está instalado en el sistema, puede buscar e instalar recursos de DSC hospedados en la [Galería de PowerShell](https://www.powershellgallery.com/).

En primer lugar, use el cmdlet [Find-DSCResource](/powershell/module/powershellget/find-dscresource) para buscar los recursos de DSC. Al ejecutar `Find-DSCResource` por primera vez, verá el aviso siguiente para instalar el "proveedor de NuGet".

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

Después de presionar "y", se instalará el proveedor de "NuGet" y verá una lista de recursos de DSC que se pueden instalar desde la Galería de PowerShell.

> [!NOTE]
> La lista no se muestra porque es muy extensa.

También puede especificar el parámetro `-Name` mediante caracteres comodín, o el parámetro `-Filter` sin caracteres comodín para limitar la búsqueda. En este ejemplo se intenta encontrar un recurso de DSC "TimeZone" mediante caracteres comodín.

> [!IMPORTANT]
> Actualmente hay un error en el cmdlet `Find-DSCResource` que evita el uso de comodines en los parámetros `-Name` y `-Filter`. El segundo ejemplo a continuación muestra una solución utilizando `Where-Object`.

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

También puede usar `Where-Object` para buscar recursos de DSC con un filtrado más detallado. Este enfoque será más lento que el uso de parámetros de filtrado integrados.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Para obtener más información sobre el filtrado, consulte [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Instalación de recursos de DSC mediante PowerShellGet

Para instalar un recurso de DSC, use el cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module), especificando el nombre del módulo que se muestra bajo el nombre **Módulo** en los resultados de búsqueda.

El recurso "TimeZone" existe en el módulo "ComputerManagementDSC", así que es el módulo que instala este ejemplo.

> [!NOTE]
> Si no ha confiado en la Galería de PowerShell, verá la siguiente advertencia solicitando una confirmación, que le indicará cómo evitar las solicitudes posteriores en las instalaciones.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Presione "y" para continuar con la instalación del módulo. Después de la instalación, compruebe que el nuevo recurso está instalado mediante [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

También puede ver otros recursos en el módulo recién instalado, especificando el parámetro `-ModuleName`.

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>Vea también

- [¿Qué son los recursos?](../resources/resources.md)
