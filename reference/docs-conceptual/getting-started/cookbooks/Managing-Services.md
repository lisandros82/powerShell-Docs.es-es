---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Administración de servicios
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 81fd8802215da80ce22fa3fd4750b1df6efe8206
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268082"
---
# <a name="managing-services"></a>Administración de servicios

Existen ocho cmdlets Service principales, diseñados para una amplia gama de tareas de servicio. Solo veremos la enumeración y el cambio del estado de ejecución de los servicios, pero puede obtener una lista de cmdlets Service mediante `Get-Help \*-Service`. También puede encontrar información sobre cada cmdlet Service mediante `Get-Help <Cmdlet-Name>`, como `Get-Help New-Service`.

## <a name="getting-services"></a>Obtener servicios

Puede obtener los servicios en un equipo local o remoto mediante el cmdlet `Get-Service`. Del mismo modo que ocurre con `Get-Process`, si usa el comando `Get-Service` sin parámetros, se devolverán todos los servicios. Puede filtrar por nombre, incluso con un asterisco como carácter comodín:

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Dado que no siempre es evidente cuál es el nombre real del servicio, es posible que necesite buscar servicios por el nombre para mostrar. Puede hacerlo por el nombre específico, mediante caracteres comodín o con una lista de nombres para mostrar:

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

Puede usar el parámetro ComputerName del cmdlet Get-Service para obtener los servicios en equipos remotos. El parámetro ComputerName acepta varios valores y caracteres comodín, por lo que puede obtener los servicios en varios equipos con un solo comando. Por ejemplo, el siguiente comando obtiene los servicios en el equipo remoto Server01.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Obtener servicios necesarios y dependientes

El cmdlet Get-Service tiene dos parámetros que son muy útiles para la administración de servicios. El parámetro DependentServices obtiene servicios que dependen del servicio. El parámetro RequiredServices obtiene servicios de los que depende este servicio.

Estos parámetros solo muestran los valores de las propiedades DependentServices y ServicesDependedOn (alias=RequiredServices) del objeto System.ServiceProcess.ServiceController que devuelve Get-Service, pero simplifican los comandos y hacen que resulte mucho más fácil obtener esta información.

El comando siguiente obtiene los servicios que el servicio LanmanWorkstation requiere.

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

El comando siguiente obtiene los servicios que requieren el servicio LanmanWorkstation.

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

También puede obtener todos los servicios que tengan dependencias. El comando siguiente hace justamente eso y, después, usa el cmdlet Format-Table para mostrar las propiedades Status, Name, RequiredServices y DependentServices de los servicios en el equipo.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Detener, iniciar, suspender y reiniciar los servicios

Todos los cmdlets Service tienen el mismo formato general. Los servicios pueden especificarse por el nombre común o el nombre para mostrar, y toman listas y caracteres comodín como valores. Para detener el administrador de trabajos de impresión, use:

```powershell
Stop-Service -Name spooler
```

Para iniciar el administrador de trabajos de impresión una vez detenido, use:

```powershell
Start-Service -Name spooler
```

Para suspender el administrador de trabajos de impresión, use:

```powershell
Suspend-Service -Name spooler
```

El cmdlet `Restart-Service` funciona de la misma manera que los otros cmdlets Service, pero mostraremos algunos ejemplos más complejos. En el uso más simple, debe especificar el nombre del servicio:

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Observará que obtiene un mensaje de advertencia repetido sobre el inicio del administrador de trabajos de impresión. Si realiza una operación de servicio que tarda bastante tiempo, Windows PowerShell le notificará que todavía está intentando realizar la tarea.

Si desea reiniciar varios servicios, puede obtener una lista de estos, filtrarlos y, después, ejecutar el reinicio:

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

Estos cmdlets Service no tienen un parámetro ComputerName, pero se pueden ejecutar en un equipo remoto mediante el cmdlet Invoke-Command. Por ejemplo, el siguiente comando reinicia el servicio de administrador de trabajos en cola en el equipo remoto Server01.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Establecer las propiedades del servicio

El cmdlet `Set-Service` cambia las propiedades de un servicio en un equipo local o remoto. Dado que el estado del servicio es una propiedad, puede usar este cmdlet para iniciar, detener y suspender un servicio.
El cmdlet Set-Service también tiene un parámetro StartupType que permite cambiar el tipo de inicio del servicio.

Para usar `Set-Service` en Windows Vista y en versiones posteriores de Windows, abra Windows PowerShell con la opción "Ejecutar como administrador".

Para obtener más información, consulte [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## <a name="see-also"></a>Véase también

- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)