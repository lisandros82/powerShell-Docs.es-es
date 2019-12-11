---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Auditoría y creación de informes en JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017796"
---
# <a name="auditing-and-reporting-on-jea"></a>Auditoría y creación de informes en JEA

Después de haber implementado JEA, tendrá que auditar la configuración de JEA de forma periódica. La auditoría ayudar a evaluar si los usuarios adecuados tienen acceso al punto de conexión de JEA y sus roles asignados siguen siendo correctos.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Buscar sesiones de JEA registradas en un equipo

Para comprobar qué sesiones de JEA están registradas en un equipo, use el cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Los derechos efectivos del punto de conexión se muestran en la propiedad **Permission**. Estos usuarios tienen derecho a conectarse al punto de conexión de JEA. Pero los roles y los comandos a los que tienen acceso están determinados por la propiedad **RoleDefinitions** del [archivo de configuración de sesión](session-configurations.md) que se ha usado para registrar el punto de conexión. Expanda la propiedad **RoleDefinitions** para evaluar las asignaciones de rol en un punto de conexión de JEA registrado.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Buscar funcionalidades de rol disponibles en el equipo

JEA obtiene las funcionalidades de rol de los archivos `.psrc` almacenados en la carpeta **RoleCapabilities** dentro de un módulo de PowerShell. La función siguiente busca todas las funcionalidades de rol disponibles en un equipo.

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> El orden de los resultados de esta función no es necesariamente el orden en que se seleccionarán las funcionalidades de rol si varias de ellas comparten el mismo nombre.

## <a name="check-effective-rights-for-a-specific-user"></a>Comprobar los derechos efectivos de un usuario específico

El cmdlet [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) enumera todos los comandos disponibles en un punto de conexión de JEA en función de las pertenencias a grupos del usuario.
La salida de `Get-PSSessionCapability` es idéntica a la del usuario especificado que ejecuta `Get-Command -CommandType All` en una sesión de JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Si los usuarios no son miembros permanentes de grupos que les concederían derechos adicionales de JEA, es posible que este cmdlet no refleje esos permisos adicionales. Esto sucede al usar sistemas de administración de acceso con privilegios Just-In-Time para permitir que los usuarios pertenezcan de forma temporal a un grupo de seguridad. Evalúe con atención la asignación de usuarios a roles y funcionalidades para garantizar que los usuarios solo obtienen el nivel de acceso necesario para realizar su trabajo de forma correcta.

## <a name="powershell-event-logs"></a>Registros de eventos de PowerShell

Si ha habilitado el registro de bloques de script o de módulo en el sistema, puede ver eventos en los registros de eventos de Windows para cada comando que ejecute un usuario en una sesión de JEA. Para buscar estos eventos, abra el registro de eventos **Microsoft-Windows-PowerShell/Operational** y busque eventos con el identificador **4104**.

En cada entrada del registro de eventos se incluye información sobre la sesión en la que se ha ejecutado el comando. Para las sesiones de JEA, el evento incluye información sobre **ConnectedUser** y **RunAsUser**. **ConnectedUser** es el usuario actual que ha creado la sesión de JEA. **RunAsUser** es la cuenta de JEA que se ha usado para ejecutar el comando.

En los registros de eventos de la aplicación se muestran los cambios realizados por **RunAsUser**. Por tanto, es necesario tener habilitado el registro de scripts y módulos para realizar el seguimiento de la invocación de un comando específico hasta **ConnectedUser**.

## <a name="application-event-logs"></a>Registros de eventos de la aplicación

Es posible que los comandos que se ejecutan en una sesión de JEA que interactúan con aplicaciones o servicios externos registren eventos en sus propios registros de eventos. A diferencia de los registros y las transcripciones de PowerShell, otros mecanismos de registro no capturan el usuario conectado de la sesión de JEA. En su lugar, esas aplicaciones solo registran el usuario de ejecución virtual.
Para determinar quién ha ejecutado el comando, tiene que consultar una [transcripción de sesión](#session-transcripts) o poner en correlación los registros de eventos de PowerShell con la hora y el usuario que se muestran en el registro de eventos de la aplicación.

El registro de WinRM también puede ayudarle a poner en correlación a los usuarios de ejecución con el usuario que se conecta en un registro de eventos de la aplicación. El identificador de evento **193** del registro **operativo o de Administración remota de Windows de Microsoft Windows** registra el identificador de seguridad (SID) y el nombre de cuenta del usuario que se conecta y del usuario de ejecución en todas las sesiones de JEA nuevas.

## <a name="session-transcripts"></a>Transcripciones de sesión

Si ha configurado JEA para crear una transcripción para cada sesión de usuario, se almacena una copia de texto de las acciones de todos los usuarios en la carpeta especificada.

El comando siguiente (como administrador) busca todos los directorios de transcripción.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

Cada transcripción comienza con información sobre la hora en que se ha iniciado la sesión, qué usuario se ha conectado a la sesión y qué identidad de JEA se le ha asignado.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

El cuerpo de la transcripción contiene información sobre cada comando que ha invocado el usuario. La sintaxis exacta del comando que se usa no está disponible en las sesiones de JEA debido a la manera en que se transforman los comandos para la comunicación remota de PowerShell. Pero todavía puede determinar el comando real que se ha ejecutado. A continuación se muestra un fragmento de código de ejemplo de una transcripción de un usuario que ejecuta `Get-Service Dns` en una sesión de JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Se escribe una línea **CommandInvocation** para cada comando que ejecuta un usuario. En **ParameterBindings** se registran todos los parámetros y valores proporcionados con el comando. En el ejemplo anterior, puede ver que al parámetro **Name** se le ha proporcionado el valor **Dns** para el cmdlet `Get-Service`.

El resultado de cada comando también desencadenará una instancia de **CommandInvocation**, normalmente para `Out-Default`. **InputObject** de `Out-Default` es el objeto de PowerShell que devuelve el comando. Los detalles de ese objeto se imprimen unas líneas más adelante, imitando detenidamente lo que habría visto el usuario.

## <a name="see-also"></a>Vea también

[Entrada de blog sobre seguridad de *PowerShell ♥ the Blue Team*](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
