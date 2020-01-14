---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Recopilar información acerca de los equipos
ms.openlocfilehash: 9407ff15b3c3ca6b3adab60d4d01d957c599e79e
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737243"
---
# <a name="collecting-information-about-computers"></a>Recopilar información acerca de los equipos

Los cmdlets del módulo **CimCmdlets** son los más importantes para tareas de administración generales del sistema. Todas las opciones de configuración críticas del subsistema se exponen a través de WMI. Además, WMI trata los datos como objetos que están en colecciones de uno o más elementos. Dado que Windows PowerShell también funciona con objetos y tiene una canalización que permite tratar uno o varios objetos de la misma manera, el acceso genérico a WMI le permite realizar algunas tareas avanzadas con muy poco esfuerzo.

## <a name="listing-desktop-settings"></a>Enumerar la configuración del escritorio

Comenzaremos con un comando que recopila información acerca de los escritorios en el equipo local.

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

Devuelve información de todos los equipos de escritorio, independientemente de si están en uso.

> [!NOTE]
> La información devuelta por algunas clases WMI puede ser muy detallada y, a menudo, incluir metadatos acerca de la clase WMI.

Dado que la mayoría de las propiedades de estos metadatos tienen nombres que comienzan por **Cim**, puede filtrarlas mediante `Select-Object`. Especifique el parámetro **-ExcludeProperty** con "Cim*" como valor. Por ejemplo:

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

Para filtrar los metadatos, use un operador de canalización (|) para enviar los resultados del comando `Get-CimInstance` a `Select-Object -ExcludeProperty "CIM*"`.

## <a name="listing-bios-information"></a>Enumerar información del BIOS

La clase **Win32_BIOS** de WMI devuelve información bastante compacta y completa sobre el BIOS del sistema en el equipo local:

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a>Enumerar información del procesador

Puede recuperar información general del procesador mediante la clase **Win32_Processor** de WMI, aunque probablemente desee filtrar la información:

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

Para obtener una cadena descriptiva genérica de la familia del procesador, puede devolver la propiedad **SystemType**:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>Enumerar el modelo y el fabricante del equipo

La información del modelo del equipo también está disponible en **Win32_ComputerSystem**. La salida estándar mostrada no necesita ningún filtrado para proporcionar datos de OEM:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

La salida de comandos como este, que devuelven información directamente de determinado hardware, es tan buena como los datos que posee. Los fabricantes del hardware no configuran correctamente algunos datos, por lo que podrían no estar disponibles.

## <a name="listing-installed-hotfixes"></a>Enumerar las revisiones instaladas

Puede enumerar todas las revisiones instaladas mediante **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

Esta clase devuelve una lista de revisiones que se ve así:

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Para obtener una salida más concisa, puede excluir algunas propiedades. Aunque puede usar el parámetro **Property** de `Get-CimInstance` para elegir solo **HotFixID**, al hacerlo se devolverá más información, porque se muestran todos los metadatos de manera predeterminada:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixID
```

```Output
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4533002
InstalledBy           :
ServicePackInEffect   :
PSComputerName        :
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name…}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
...
```

Se devuelven los datos adicionales, ya que el parámetro **Property** de `Get-CimInstance` restringe las propiedades devueltas de instancias de la clase WMI, no el objeto que se devuelve a PowerShell. Para reducir la salida, use `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>Enumerar la información de versión del sistema operativo

Las propiedades de la clase **Win32_OperatingSystem** incluyen información acerca de la versión y del Service Pack. Solo puede seleccionar explícitamente estas propiedades para obtener un resumen de la información de versión de **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

También puede usar caracteres comodín con el parámetro **Property** de `Select-Object`. Dado que todas las propiedades que comienzan por **Build** o **ServicePack** son importantes para usar aquí, podemos reducirlo al formato siguiente:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property Build*,OSType,ServicePack*
```

```Output
BuildNumber             : 18362
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a>Enumerar el propietario y los usuarios locales

La información local del usuario general (número de usuarios con licencia, número actual de usuarios y nombre del propietario) puede encontrarse con una selección de propiedades de la clase **Win32_OperatingSystem**. Puede seleccionar explícitamente las propiedades para que tengan el aspecto siguiente:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Una versión más concisa con caracteres comodín es:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>Obtener el espacio disponible en disco

Para ver el espacio en disco y el espacio libre de las unidades locales, puede usar la clase Win32_LogicalDisk de WMI.
Solo necesita ver las instancias con un valor de DriveType de 3 (valor que WMI usa para los discos duros fijos).

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3"
```

```Output
DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .
```

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" |
  Measure-Object -Property FreeSpace,Size -Sum |
    Select-Object -Property Property,Sum
```

```Output
Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a>Obtener información de la sesión de inicio

Puede obtener información general sobre las sesiones de inicio asociadas a los usuarios a través de la clase **Win32_LogonSession** de WMI:

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>Ayudar al usuario a iniciar sesión en un equipo

Para ver el usuario que inició sesión en un equipo concreto use Win32_ComputerSystem. Este comando devuelve solo el usuario que inició sesión en el escritorio del sistema:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a>Obtener la hora local de un equipo

Puede recuperar la hora local actual de un equipo específico mediante la clase **Win32_LocalTime** de WMI.

```powershell
Get-CimInstance -ClassName Win32_LocalTime
```

```Output
Day            : 23
DayOfWeek      : 1
Hour           : 8
Milliseconds   :
Minute         : 52
Month          : 12
Quarter        : 4
Second         : 55
WeekInMonth    : 4
Year           : 2019
PSComputerName :
```

## <a name="displaying-service-status"></a>Visualizar el estado del servicio

Para ver el estado de todos los servicios de un equipo concreto, puede usar el cmdlet `Get-Service`localmente. Para los sistemas remotos, puede usar la clase **Win32_Service** de WMI. Si también usa `Select-Object` para filtrar los resultados con **Status**, **Name** y **DisplayName**, el formato de salida será prácticamente idéntico al de `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

Para permitir la visualización completa de los nombres de los servicios ocasionales con nombres muy largos, puede usar `Format-Table` con los parámetros **AutoSize** y **Wrap** a fin de optimizar el ancho de columna y permitir que los nombres largos se ajusten en lugar de truncarse:

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
