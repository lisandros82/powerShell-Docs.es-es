---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Recopilar información acerca de los equipos
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: ca92474eaf6fa546c3d6450f5a282e45157018a8
ms.sourcegitcommit: 4a841ebda3339ae2477e0f5f5be8c01740221232
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="collecting-information-about-computers"></a>Recopilar información acerca de los equipos

Los cmdlets del módulo **CimCmdlets** son los más importantes para tareas de administración generales del sistema.
Todas las opciones de configuración críticas del subsistema se exponen a través de WMI.
Además, WMI trata los datos como objetos que están en colecciones de uno o más elementos.
Dado que Windows PowerShell también funciona con objetos y tiene una canalización que permite tratar uno o varios objetos de la misma manera, el acceso genérico a WMI le permite realizar algunas tareas avanzadas con muy poco esfuerzo.

Los ejemplos siguientes muestran cómo recopilar información específica mediante `Get-CimInstance` en un equipo arbitrario.
Especificamos el parámetro **ComputerName** con el valor de punto (**.**), que representa el equipo local.
Puede especificar una dirección IP o un nombre asociado a cualquier equipo que pueda alcanzar a través de WMI.
Para recuperar información sobre el equipo local, puede omitir el parámetro **ComputerName**.

### <a name="listing-desktop-settings"></a>Enumerar la configuración del escritorio

Comenzaremos con un comando que recopila información acerca de los escritorios en el equipo local.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Devuelve información de todos los equipos de escritorio, independientemente de si están en uso.

> [!NOTE]
> La información devuelta por algunas clases WMI puede ser muy detallada y, a menudo, incluir metadatos acerca de la clase WMI.
Dado que la mayoría de las propiedades de estos metadatos tienen nombres que comienzan por **Cim**, puede filtrarlas mediante `Select-Object`.
Especifique el parámetro **-ExcludeProperty** con "Cim*" como valor.
Por ejemplo:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Para filtrar los metadatos, use un operador de canalización (|) para enviar los resultados del comando `Get-CimInstance` a `Select-Object -ExcludeProperty "CIM*"`.

### <a name="listing-bios-information"></a>Enumerar información del BIOS

La clase **Win32_BIOS** de WMI devuelve información bastante compacta y completa sobre el BIOS del sistema en el equipo local:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Enumerar información del procesador

Puede recuperar información general del procesador mediante la clase **Win32_Processor** de WMI, aunque probablemente desee filtrar la información:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Para obtener una cadena descriptiva genérica de la familia del procesador, puede devolver la propiedad **SystemType**:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Enumerar el modelo y el fabricante del equipo

La información del modelo del equipo también está disponible en **Win32_ComputerSystem**.
La salida estándar mostrada no necesita ningún filtrado para proporcionar datos de OEM:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

La salida de comandos como este, que devuelven información directamente de determinado hardware, es tan buena como los datos que posee.
Los fabricantes del hardware no configuran correctamente algunos datos, por lo que podrían no estar disponibles.

### <a name="listing-installed-hotfixes"></a>Enumerar las revisiones instaladas

Puede enumerar todas las revisiones instaladas mediante **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Esta clase devuelve una lista de revisiones que se ve así:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Para obtener una salida más concisa, puede excluir algunas propiedades.
Aunque puede usar el parámetro **Property** de `Get-CimInstance` para elegir solo **HotFixID**, al hacerlo se devolverá más información, porque se muestran todos los metadatos de manera predeterminada:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Se devuelven los datos adicionales, ya que el parámetro Property de `Get-CimInstance` restringe las propiedades devueltas de instancias de la clase WMI, no el objeto que se devuelve a Windows PowerShell.
Para reducir la salida, use `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a>Enumerar la información de versión del sistema operativo

Las propiedades de la clase **Win32_OperatingSystem** incluyen información acerca de la versión y del Service Pack.
Solo puede seleccionar explícitamente estas propiedades para obtener un resumen de la información de versión de **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

También puede usar caracteres comodín con el parámetro **Property** de `Select-Object`.
Dado que todas las propiedades que comienzan por **Build** o **ServicePack** son importantes para usar aquí, podemos reducirlo al formato siguiente:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>Enumerar el propietario y los usuarios locales

La información local del usuario general (número de usuarios con licencia, número actual de usuarios y nombre del propietario) puede encontrarse con una selección de propiedades de la clase **Win32_OperatingSystem**.
Puede seleccionar explícitamente las propiedades para que tengan el aspecto siguiente:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Una versión más concisa con caracteres comodín es:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Obtener el espacio disponible en disco

Para ver el espacio en disco y el espacio libre de las unidades locales, puede usar la clase Win32_LogicalDisk de WMI.
Solo necesita ver las instancias con un valor de DriveType de 3 (valor que WMI usa para los discos duros fijos).

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a>Obtener información de la sesión de inicio

Puede obtener información general sobre las sesiones de inicio asociadas a los usuarios a través de la clase **Win32_LogonSession** de WMI:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Ayudar al usuario a iniciar sesión en un equipo

Para ver el usuario que inició sesión en un equipo concreto use Win32_ComputerSystem.
Este comando devuelve solo el usuario que inició sesión en el escritorio del sistema:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Obtener la hora local de un equipo

Puede recuperar la hora local actual de un equipo específico mediante la clase **Win32_LocalTime** de WMI.

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

### <a name="displaying-service-status"></a>Visualizar el estado del servicio

Para ver el estado de todos los servicios de un equipo concreto, puede usar el cmdlet `Get-Service`localmente.
Para los sistemas remotos, puede usar la clase **Win32_Service** de WMI.
Si también usa `Select-Object` para filtrar los resultados con **Status**, **Name** y **DisplayName**, el formato de salida será prácticamente idéntico al de `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Para permitir la visualización completa de los nombres de los servicios ocasionales con nombres muy largos, puede usar `Format-Table` con los parámetros **AutoSize** y **Wrap** a fin de optimizar el ancho de columna y permitir que los nombres largos se ajusten en lugar de truncarse:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
