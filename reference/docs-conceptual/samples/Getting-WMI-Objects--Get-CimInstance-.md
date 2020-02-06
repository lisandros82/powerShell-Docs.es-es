---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Obtener objetos de WMI (Get-CimInstance)
ms.openlocfilehash: 4ff47844fd367a49f554c7c05c491bdddf28eabc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "77002655"
---
# <a name="getting-wmi-objects-get-ciminstance"></a>Obtener objetos de WMI (Get-CimInstance)

## <a name="getting-wmi-objects-get-ciminstance"></a>Obtener objetos de WMI (Get-CimInstance)

Windows Management Instrumentation (WMI) es una tecnología principal para la administración del sistema de Windows porque expone una amplia gama de información de manera uniforme. Debido a la medida en que WMI lo hace posible, el cmdlet de PowerShell para acceder a objetos WMI, `Get-CimInstance` es uno de los más útiles para realizar el trabajo real. Vamos a explicar cómo usar CimCmdlets para acceder a objetos WMI y, después, cómo usar objetos WMI para realizar acciones específicas.

### <a name="listing-wmi-classes"></a>Enumerar clases WMI

El primer problema que la mayoría de los usuarios de WMI experimentan es intentar averiguar qué se puede hacer con WMI. Las clases WMI describen los recursos que se pueden administrar. Existen cientos de clases WMI, algunas de los cuales contienen decenas de propiedades.

`Get-CimClass` hace que WMI se pueda detectar para abordar este problema. Para obtener una lista de las clases WMI disponibles en el equipo local, escriba:

```powershell
Get-CimClass -Namespace root/CIMV2 |
  Where-Object CimClassName -like Win32* |
    Select-Object CimClassName
```

```Output
CimClassName
------------
Win32_DeviceChangeEvent
Win32_SystemConfigurationChangeEvent
Win32_VolumeChangeEvent
Win32_SystemTrace
Win32_ProcessTrace
Win32_ProcessStartTrace
Win32_ProcessStopTrace
Win32_ThreadTrace
Win32_ThreadStartTrace
Win32_ThreadStopTrace
...
```

Puede recuperar la misma información de un equipo remoto mediante el parámetro **ComputerName**. Para ello, especifique un nombre de equipo o una dirección IP:

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

La lista de clases que devuelven los equipos remotos puede variar según el sistema operativo específico que el equipo está ejecutando y las extensiones WMI determinadas agregadas por las aplicaciones instaladas.

> [!NOTE]
> Al usar cmdlets de CIM para conectarse a un equipo remoto, este debe ejecutar WMI y la cuenta que está usando debe estar en el grupo de administradores local en el equipo remoto.
> El sistema remoto no necesita tener PowerShell instalado. Esto permite administrar los sistemas operativos que no ejecutan PowerShell, pero tienen WMI disponible.

### <a name="displaying-wmi-class-details"></a>Visualizar detalles de clases WMI

Si conoce el nombre de una clase WMI, puede usarlo para obtener información inmediatamente. Por ejemplo, una de las clases WMI que se usa habitualmente para recuperar información sobre un equipo es **Win32_OperatingSystem**.

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

Aunque vamos a presentar todos los parámetros, el comando se puede expresar de forma más concisa.
El parámetro **ComputerName** no es necesario cuando se conecta al sistema local. Los presentamos para demostrar el caso más general y recordarle el parámetro. **Namespace** se establece de manera predeterminada en `root/CIMV2` y también se puede omitir. Por último, la mayoría de los cmdlets permite omitir el nombre de los parámetros comunes. Con `Get-CimInstance`, si no se especifica ningún nombre para el primer parámetro, PowerShell lo trata como el parámetro **Class**. Esto significa que el último comando se podría haber emitido escribiendo:

```powershell
Get-CimInstance Win32_OperatingSystem
```

La clase **Win32_OperatingSystem** tiene muchas más propiedades de las que se muestran aquí. Puede usar Get-Member para ver todas las propiedades. Las propiedades de una clase WMI están disponibles automáticamente como otras propiedades de objeto:

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Get-Member -MemberType Property
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_OperatingSystem
Name                                      MemberType Definition
----                                      ---------- ----------
BootDevice                                Property   string BootDevice {get;}
BuildNumber                               Property   string BuildNumber {get;}
BuildType                                 Property   string BuildType {get;}
Caption                                   Property   string Caption {get;}
CodeSet                                   Property   string CodeSet {get;}
CountryCode                               Property   string CountryCode {get;}
CreationClassName                         Property   string CreationClassName {get;}
CSCreationClassName                       Property   string CSCreationClassName {get;}
CSDVersion                                Property   string CSDVersion {get;}
CSName                                    Property   string CSName {get;}
CurrentTimeZone                           Property   short CurrentTimeZone {get;}
DataExecutionPrevention_32BitApplications Property   bool DataExecutionPrevention_32BitApplications {get;}
DataExecutionPrevention_Available         Property   bool DataExecutionPrevention_Available {get;}
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Visualizar propiedades no predeterminadas con cmdlets de formato

Si quiere ver la información incluida en la clase **Win32_OperatingSystem** que no aparece de forma predeterminada, puede mostrarla mediante los cmdlets **Format**. Por ejemplo, si desea mostrar los datos de memoria disponible, escriba:

```powershell
Get-CimInstance -Class Win32_OperatingSystem |
  Format-Table -Property TotalVirtualMemorySize, TotalVisibleMemorySize,
    FreePhysicalMemory, FreeVirtualMemory, FreeSpaceInPagingFiles
```

```Output
TotalVirtualMemorySize TotalVisibleMemorySize FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------------- ------------------ ----------------- ----------------------
              33449088               16671872            6451868          18424496               16285032
```

> [!NOTE]
> Los caracteres comodín funcionan con nombres de propiedad de `Format-Table`, por lo que el elemento final de la canalización se puede reducir a `Format-Table -Property Total*Memory*, Free*`.

Los datos de la memoria podrían ser más legibles si se formatean como una lista escribiendo:

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Format-List Total*Memory*, Free*
```

```Output
TotalVirtualMemorySize : 33449088
TotalVisibleMemorySize : 16671872
FreePhysicalMemory     : 6524456
FreeSpaceInPagingFiles : 16285808
FreeVirtualMemory      : 18393668
Name                   : Microsoft Windows 10 Pro|C:\WINDOWS|\Device\Harddisk0\Partition2
```
