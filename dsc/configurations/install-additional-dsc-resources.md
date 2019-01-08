---
ms.date: 12/12/2018
keywords: DSC, powershell, recursos, la galería, el programa de instalación
title: Instalación de recursos de DSC adicionales
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402906"
---
# <a name="install-additional-dsc-resources"></a>Instalación de recursos de DSC adicionales

PowerShell incluye varios recursos de cuadro de Desired State Configuration (DSC). El **PSDesiredStateConfiguration** módulo contiene todos los recursos de DSC OOB disponibles en la instancia específica de PowerShell.

Se trata de una lista de los recursos OOB incluidos en PowerShell 4.0 y una descripción de las capacidades del recurso.

> [!NOTE]
> Se trata de una lista incompleta, como el número de recursos OOB ha crecido con cada versión de PowerShell.

|Recurso  |Descripción  |
|---------|---------|
|**File**|Controla el estado de los archivos y directorios. Copia los archivos de un **origen** a un **destino** y las actualiza cuando el **origen** cambios mediante la comparación de fechas, las sumas de comprobación y algoritmos hash.|
|**Archive**|Desempaqueta los archivos y una ubicación especificada. Valida los archivos con un determinado **suma de comprobación**.|
|**Environment**|Administra las variables de entorno.|
|**Grupo**|Administra grupos locales y controla la pertenencia al grupo.|
|**Log**|Escribe los mensajes a la `Microsoft-Windows-Desired State Configuration/Analytic` registro de eventos.|
|**Package**|Instala o desinstala los paquetes mediante **argumentos**, **LogPath**, **ReturnCode**, otras configuraciones.|
|**Registry**|Administra los valores y claves del registro.|
|**Script**|Le permite diseñar su propio [get-test-set](../resources/get-test-set.md) bloques de script.|
|**Service**|Configura los servicios de Windows.|
|**Usuario** |Administra usuarios locales y los atributos.|
|**WindowsFeature**|Administra los roles y características.|
|**WindowsProcess**|Configura los procesos de Windows.|

Los recursos OOB permiten un buen punto de partida para las operaciones comunes. Si los recursos OOB no satisfacen sus necesidades, puede escribir su propio [recurso personalizado](../resources/authoringResource.md). Antes de escribir un recurso personalizado para solucionar el problema, debe examinar el gran número de recursos de DSC que ya se han creado por Microsoft y la Comunidad de PowerShell.

Puede encontrar los recursos de DSC en ambos el [Galería de PowerShell](https://www.powershellgallery.com/) y [GitHub](https://github.com/). También puede instalar directamente desde la consola de PowerShell mediante los recursos de DSC [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Instalación de PowerShellGet

Para determinar si ya tiene **PowerShell** get o para obtener ayuda para instalarlo, consulte la guía siguiente: [instalación PowerShellGet](/powershell/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>Buscar recursos de DSC mediante PowerShellGet

Una vez **PowerShellGet** está instalado en el sistema, puede buscar e instalar recursos de DSC hospedados en el [Galería de PowerShell](https://www.powershellgallery.com/).

En primer lugar, use el [Find-DSCResource](/powershell/module/powershellget/find-dscresource) para encontrar los recursos de DSC. Al ejecutar `Find-DSCResource` por primera vez, verá el aviso siguiente para instalar el proveedor de NuGet"".

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

Después de presionar 'y', se instala el proveedor de "NuGet", verá una lista de recursos de DSC que se pueden instalar desde la Galería de PowerShell.

> [!NOTE]
> No se muestra la lista porque es muy grande.

También puede especificar el `-Name` parámetro mediante caracteres comodín, o `-Filter` parámetro sin caracteres comodín para limitar la búsqueda. En este ejemplo intenta encontrar un recurso de DSC "TimeZone" mediante los caracteres comodín.

> [!IMPORTANT]
> Actualmente no hay un error en la `Find-DSCResource` cmdlet que impida usar caracteres comodín en ambos el `-Name` y `-Filter` parámetros. El segundo ejemplo siguiente muestra el uso de una solución alternativa `Where-Object`.

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

También puede usar `Where-Object` para buscar recursos de DSC con filtrado más granular. Este enfoque será más lenta que la compila en parámetros de filtrado.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Para obtener más información sobre el filtrado, consulte [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Instalar recursos de DSC mediante PowerShellGet

Para instalar un recurso de DSC, use el [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, especificando el nombre del módulo que se muestra en **módulo** nombre en los resultados de búsqueda.

El recurso de "Zona horaria" existe en el módulo "ComputerManagementDSC", por lo que es que el módulo de este ejemplo se instala.

> [!NOTE]
> Si no ha confiado en la Galería de PowerShell, vea la advertencia debajo de confirmación y que se le indicará cómo evitar el número de solicitudes posterior en instala.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Presione "s" para continuar con la instalación del módulo. Después de la instalación, compruebe que el nuevo recurso está instalado mediante [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

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

También puede ver otros recursos en el módulo recién instalado, especificando el `-ModuleName` parámetro.

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
