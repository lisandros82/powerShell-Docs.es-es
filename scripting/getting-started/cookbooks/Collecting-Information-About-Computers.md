---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "Recopilar información acerca de los equipos"
ms.technology: powershell
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: ba81489749ba51ec19febb9de81de1b2a5150aa4
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="collecting-information-about-computers"></a>Recopilar información acerca de los equipos
**Get-WmiObject** es el cmdlet más importante para las tareas generales de administración del sistema. Todas las opciones de configuración críticas del subsistema se exponen a través de WMI. Además, WMI trata los datos como objetos que están en colecciones de uno o más elementos. Dado que Windows PowerShell también funciona con objetos y tiene una canalización que permite tratar uno o varios objetos de la misma manera, el acceso genérico a WMI le permite realizar algunas tareas avanzadas con muy poco esfuerzo.

Los ejemplos siguientes muestran cómo recopilar información específica mediante **Get-WmiObject** en un equipo arbitrario. Especificamos el parámetro **ComputerName** con el valor de punto (**.**), que representa el equipo local. Puede especificar una dirección IP o un nombre asociado a cualquier equipo que pueda alcanzar a través de WMI. Para recuperar información acerca del equipo local, puede omitir **-ComputerName.**

### <a name="listing-desktop-settings"></a>Enumerar la configuración del escritorio
Comenzaremos con un comando que recopila información acerca de los escritorios en el equipo local.

```
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

Devuelve información de todos los equipos de escritorio, independientemente de si están en uso.

> [!NOTE]
> La información devuelta por algunas clases WMI puede ser muy detallada y, a menudo, incluir metadatos acerca de la clase WMI. Dado que la mayoría de las propiedades de estos metadatos tiene nombres que comienzan por un carácter de subrayado doble, puede filtrar las propiedades mediante Select-Object. Especifique solo las propiedades que comiencen por caracteres alfabéticos mediante **[a-z]*** como el valor de Property. Por ejemplo:

```
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

Para filtrar los metadatos, use el operador de canalización (|) para enviar los resultados del comando Get-WmiObject a **Select-Object -Property [a-z]***.

### <a name="listing-bios-information"></a>Enumerar información del BIOS
La clase Win32_BIOS de WMI devuelve información bastante compacta y completa acerca del BIOS del sistema en el equipo local:

```
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Enumerar información del procesador
Puede recuperar información general del procesador mediante la clase **Win32_Processor** de WMI, aunque probablemente desee filtrar la información:

```
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

Para obtener una cadena descriptiva genérica de la familia del procesador, puede devolver la propiedad **SystemType**:

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType
SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Enumerar el modelo y el fabricante del equipo
La información del modelo del equipo también está disponible en **Win32_ComputerSystem**. La salida estándar mostrada no necesita ningún filtrado para proporcionar datos de OEM:

```
PS> Get-WmiObject -Class Win32_ComputerSystem
Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

La salida de comandos como este, que devuelven información directamente de determinado hardware, es tan buena como los datos que posee. Los fabricantes del hardware no configuran correctamente algunos datos, por lo que podrían no estar disponibles.

### <a name="listing-installed-hotfixes"></a>Enumerar las revisiones instaladas
Puede enumerar todas las revisiones instaladas mediante **Win32_QuickFixEngineering**:

```
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

Esta clase devuelve una lista de revisiones que se ve así:

```
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

Para obtener una salida más concisa, puede excluir algunas propiedades. Aunque puede usar el parámetro **Property de Get-WmiObject** para elegir solo **HotFixID**, al hacerlo se devolverá más información, porque de forma predeterminada se muestran todos los metadatos:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixID
HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

Los datos adicionales se devuelven, porque el parámetro Property de **Get-WmiObject** restringe las propiedades devueltas de instancias de la clase WMI, no el objeto devuelto a Windows PowerShell. Para reducir la salida, use **Select-Object**:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property Hot
FixId | Select-Object -Property HotFixId
HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a>Enumerar la información de versión del sistema operativo
Las propiedades de la clase **Win32_OperatingSystem** incluyen información acerca de la versión y del Service Pack. Solo puede seleccionar explícitamente estas propiedades para obtener un resumen de la información de versión de **Win32_OperatingSystem**:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

También puede usar caracteres comodín con el parámetro **Property de Select-Object**. Dado que todas las propiedades que comienzan por **Build** o **ServicePack** son importantes para usar aquí, podemos reducirlo al formato siguiente:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>Enumerar el propietario y los usuarios locales
La información local del usuario general (número de usuarios con licencia, número actual de usuarios y nombre del propietario) puede encontrarse con una selección de propiedades de **Win32_OperatingSystem**. Puede seleccionar explícitamente las propiedades para que tengan el aspecto siguiente:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Una versión más concisa con caracteres comodín es:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Obtener el espacio disponible en disco
Para ver el espacio en disco y el espacio libre de las unidades locales, puede usar la clase Win32_LogicalDisk de WMI. Solo necesita ver las instancias con un valor de DriveType de 3 (valor que WMI usa para los discos duros fijos).

```
Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum
```

### <a name="getting-logon-session-information"></a>Obtener información de la sesión de inicio
Puede obtener información general acerca de las sesiones de inicio asociadas a los usuarios a través de la clase Win32_LogonSession de WMI:

```
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Ayudar al usuario a iniciar sesión en un equipo
Para ver el usuario que inició sesión en un equipo concreto use Win32_ComputerSystem. Este comando devuelve solo el usuario que inició sesión en el escritorio del sistema:

```
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Obtener la hora local de un equipo
Puede recuperar la hora local actual en un equipo específico mediante la clase Win32_LocalTime de WMI. Dado que esta clase muestra todos los metadatos de forma predeterminada, puede filtrarlos mediante **Select-Object**:

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### <a name="displaying-service-status"></a>Visualizar el estado del servicio
Para ver el estado de todos los servicios de un equipo específico, puede usar el cmdlet **Get-Service** localmente como ya se ha mencionado. Para los sistemas remotos, puede usar la clase Win32_Service de WMI. Si también usa **Select-Object** para filtrar los resultados con **Status**, **Name** y **DisplayName**, el formato de salida será casi idéntico al de **Get-Service**:

```
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Para permitir la visualización completa de los nombres de los servicios ocasionales con nombres muy largos, puede usar **Format-Table** con los parámetros **AutoSize** y **Wrap**, con el fin de optimizar el ancho de columna y permitir que los nombres largos se ajusten, en lugar de truncarse:

```
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```

