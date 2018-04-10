---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: Auditoría y creación de informes en JEA
ms.openlocfilehash: 7fc670c77b5fbf9bce8fb55dd99a2f9a984100d2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="auditing-and-reporting-on-jea"></a>Auditoría y creación de informes en JEA

> Se aplica a: Windows PowerShell 5.0

Después de haber implementado JEA, querrá auditar la configuración de JEA de forma periódica.
Esto le ayudará a evaluar si las personas adecuadas tienen acceso al punto de conexión de JEA y si sus roles asignados siguen siendo correctos.

En este tema, se describen las distintas formas en que puede auditar un punto de conexión de JEA.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Buscar sesiones de JEA registradas en un equipo

Para comprobar qué sesiones de JEA están registradas en un equipo, use el cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Los derechos efectivos del punto de conexión se muestran en la propiedad "Permission".
Estos usuarios tienen derecho a conectarse al punto de conexión de JEA, pero a qué roles (y, por extensión, comandos) tienen acceso viene determinado por el campo "RoleDefinitions" del [archivo de configuración de sesión](session-configurations.md) que se ha usado para registrar el punto de conexión.

Puede evaluar las asignaciones de rol en un punto de conexión de JEA registrado al expandir los datos de la propiedad "RoleDefinitions".

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Buscar funcionalidades de rol disponibles en el equipo

JEA solo usará los archivos de funcionalidad de rol si se almacenan en una carpeta "RoleCapabilities" dentro de un módulo de PowerShell válido.
Puede encontrar todas las funcionalidades de rol disponibles en un equipo al buscar la lista de módulos disponibles.

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> El orden de los resultados de esta función no es necesariamente el orden en que se seleccionarán las funcionalidades de rol si varias de ellas comparten el mismo nombre.

## <a name="check-effective-rights-for-a-specific-user"></a>Comprobar los derechos efectivos de un usuario específico

Una vez que ha configurado un punto de conexión de JEA, es posible que quiera comprobar qué comandos están disponibles para un usuario específico en una sesión de JEA.
Puede usar [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) para enumerar todos los comandos aplicables a un usuario si fuera a iniciar una sesión de JEA con los miembros de su grupo actual.
La salida de `Get-PSSessionCapability` es idéntica a la del usuario especificado que ejecuta `Get-Command -CommandType All` en una sesión de JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Si los usuarios no son miembros permanentes de grupos que les concederían derechos adicionales de JEA, es posible que este cmdlet no refleje esos permisos adicionales.
Este suele ser el caso al usar sistemas de administración de acceso con privilegios Just-In-Time para permitir que los usuarios pertenezcan de forma temporal a un grupo de seguridad.
Evalúe siempre cuidadosamente la asignación de usuarios a roles y el contenido de cada rol para asegurarse de que los usuarios solo obtienen acceso a la menor cantidad de comandos necesarios para realizar su trabajo correctamente.

## <a name="powershell-event-logs"></a>Registros de eventos de PowerShell

Si ha habilitado el registro de bloques de script o módulo en el sistema, podrá buscar eventos en los registros de eventos de Windows para cada comando que haya ejecutado un usuario en sus sesiones de JEA.
Para buscar estos eventos, abra el Visor de eventos de Windows, vaya al registro de eventos **Microsoft-Windows-PowerShell/Operational** y busque eventos con el identificador **4104**.

Cada entrada de registro de eventos incluirá información sobre la sesión en que se ha ejecutado el comando.
Para las sesiones de JEA, esto incluye información importante sobre el **ConnectedUser**, que es el usuario actual que ha creado la sesión de JEA, así como el **RunAsUser** que identifica la cuenta de JEA usada para ejecutar el comando.
Los registros de eventos de la aplicación mostrarán cambios realizados por el RunAsUser, por lo que tener el registro de script/módulo o transcripciones habilitado es fundamental para poder realizar un seguimiento de una invocación de comando específica hasta un usuario.

## <a name="application-event-logs"></a>Registros de eventos de la aplicación

Al ejecutar un comando en una sesión de JEA que interactúa con un servicio o aplicación externos, esas aplicaciones pueden registrar eventos en sus propios registros de eventos.
A diferencia de los registros y transcripciones de PowerShell, otros mecanismos de registro no capturarán al usuario conectado de la sesión de JEA y solo registrarán en su lugar al usuario de ejecución virtual o la cuenta de servicio administrada de grupo.
Para determinar quién ha ejecutado el comando, deberá consultar una [transcripción de sesión](#session-transcripts) o poner en correlación los registros de eventos de PowerShell con la hora y el usuario que aparecen en el registro de eventos de la aplicación.

Asimismo, el registro de WinRM puede ayudarle a poner en correlación a los usuarios de ejecución en un registro de eventos de la aplicación con el usuario que se conecta.
El identificador de evento **193** en el registro **Microsoft-Windows-Administración remota de Windows/Operational** registra el identificador de seguridad (SID) y el nombre de cuenta del usuario que se conecta y del usuario de ejecución cada vez que se crea una sesión de JEA.

## <a name="session-transcripts"></a>Transcripciones de sesión

Si ha configurado JEA para crear una transcripción para cada sesión de usuario, se almacenará una copia del texto de las acciones de todos los usuarios en la carpeta especificada.

Para buscar todos los directorios de transcripciones, ejecute el siguiente comando como administrador en el equipo configurado con JEA:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
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

En el cuerpo de la transcripción, se registra información sobre cada comando que ha invocado el usuario.
La sintaxis exacta del comando que ha ejecutado el usuario no está disponible en las sesiones de JEA debido a la forma en que se transforman los comandos para la comunicación remota de PowerShell, pero aún puede determinar el comando real que se ha ejecutado.
A continuación se muestra un fragmento de código de ejemplo de una transcripción de un usuario que ejecuta `Get-Service Dns` en una sesión de JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Para cada comando que ejecuta un usuario, se escribirá una línea "CommandInvocation", que describe el cmdlet o función que ha invocado el usuario.
ParameterBindings sigue a cada CommandInvocation para informarle sobre cada parámetro y valor que se ha proporcionado con el comando.
En el ejemplo anterior, puede ver que el parámetro "Name" ha proporcionado el valor "Dns" para el cmdlet "Get-Service".

El resultado de cada comando también desencadenará un CommandInvocation, normalmente para Out-Default.
El InputObject de Out-Default es el objeto de PowerShell que devuelve el comando.
Los detalles de ese objeto se imprimen unas líneas más adelante, imitando detenidamente lo que habría visto el usuario.

## <a name="see-also"></a>Vea también

- [Auditar acciones del usuario en una sesión JEA](audit-and-report.md)
- [Entrada de blog sobre seguridad de *PowerShell ♥ the Blue Team*](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)