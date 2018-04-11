---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Creación de una canalización de integración continua e implementación continua con DSC
ms.openlocfilehash: a3803a8e6fe6ff1b93758a73ccd54754d7bb2a84
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Creación de una canalización de integración continua e implementación continua con DSC

En este ejemplo se muestra cómo crear una canalización de integración continua/implementación continua (CI/CD) con PowerShell, DSC, Pester y Visual Studio Team Foundation Server (TFS).

Una vez que se construye y configura la canalización, puede usarla para implementar, configurar y probar completamente un servidor DSN y los registros host asociados.
Este proceso simula la primera parte de una canalización que se usaría en un entorno de desarrollo.

Una canalización CI/CD automatizada le ayuda a actualizar software de forma más rápida y confiable, garantizando que se pruebe todo el código y que una compilación actual del código esté disponible en todo momento.

## <a name="prerequisites"></a>Requisitos previos

Para usar este ejemplo, debe estar familiarizado con lo siguiente:

- Los conceptos de CI-CD. Puede encontrar una excelente referencia en [el modelo de canalización de versiones](http://aka.ms/thereleasepipelinemodelpdf).
- El control de código fuente de [Git](https://git-scm.com/)
- El entorno de pruebas [Pester](https://github.com/pester/Pester)
- [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>Qué necesitará

Para compilar y ejecutar este ejemplo, necesitará un entorno con varios equipos o máquinas virtuales.

### <a name="client"></a>Remoto

El equipo donde llevará a cabo todo el trabajo de configuración y ejecución del ejemplo.

El equipo cliente debe ser un equipo Windows que tenga instalado lo siguiente:
- [Git](https://git-scm.com/)
- Un repositorio Git local clonado a partir de https://github.com/PowerShell/Demo_CI
- Un editor de texto, como [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

El equipo que hospeda el servidor TFS donde definirá la compilación y la versión.
Este equipo debe tener instalado [Team Foundation Server 2017](https://www.visualstudio.com/tfs/).

### <a name="buildagent"></a>BuildAgent

El equipo que ejecuta el agente de compilación Windows que compila el proyecto.
Este equipo debe tener instalado y en ejecución un agente de compilación Windows.
Consulte [Implementación de un agente en Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) para instrucciones sobre cómo instalar y ejecutar un agente de compilación Windows.

También necesita instalar los módulos `xDnsServer` y `xNetworking` de DSC en este equipo.

### <a name="testagent1"></a>TestAgent1

El equipo que la configuración de DSC configuró como servidor DNS en este ejemplo.
El equipo debe ejecutar [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

El equipo que hospeda el sitio web que se configura en este ejemplo.
El equipo debe ejecutar [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>Incorporación del código en TFS

Para comenzar, crearemos un repositorio Git en TFS e importaremos el código desde el repositorio local del equipo cliente.
Si todavía no clonó el repositorio Demo_CI en el equipo cliente, ejecute el siguiente comando de git para hacerlo ahora:

`git clone https://github.com/PowerShell/Demo_CI`

1. En el equipo cliente, vaya al servidor TFS en un explorador web.
1. En TFS, [cree un nuevo proyecto de equipo](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) llamado Demo_CI.

    Asegúrese de que el **control de versiones** esté establecido en **Git**.
1. En el equipo cliente, agregue un elemento remoto en el repositorio que acaba de crear en TFS con el comando siguiente:

    `git remote add tfs <YourTFSRepoURL>`

    Donde `<YourTFSRepoURL>` es la dirección URL de clonación al repositorio TFS que creó que en el paso anterior.

    Si no sabe dónde encontrar esta dirección URL, consulte cómo [clonar un repositorio Git existente](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).
1. Inserte el código del repositorio local en el repositorio TFS con el comando siguiente:

    `git push tfs --all`
1. El repositorio TFS se rellenará con el código de Demo_CI.

>**Nota:** en este ejemplo se usa el código que se encuentra en la rama `ci-cd-example` del repositorio Git.
>Asegúrese de especificarla como la rama predeterminada del proyecto TFS y para los desencadenadores de CI/CD que crea.

## <a name="understanding-the-code"></a>Descripción del código

Antes de crear las canalizaciones de compilación e implementación, observemos parte del código para comprender qué es lo que pasa.
En el equipo cliente, abra el editor de texto de su preferencia y vaya a la raíz del repositorio Git de Demo_CI.

### <a name="the-dsc-configuration"></a>La configuración de DSC

Abra el archivo `DNSServer.ps1` (en la raíz del repositorio Demo_CI local, `./InfraDNS/Configs/DNSServer.ps1`).

Este archivo contiene la configuración de DSC que configura el servidor DNS. A continuación se muestra en su totalidad:

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

Observe la instrucción `Node`:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Esta instrucción encuentra cualquier nodo que se haya definido con un rol de `DNSServer` en los [datos de configuración](configData.md), creados por el script `DevEnv.ps1`.

Usar datos de configuración para definir nodos es importantes cuando se hace CI, porque es probable que la información de los nodos cambie entre los entornos y usar los datos de configuración le permite hacer cambios con facilidad en la información de los nodos sin cambiar el código de configuración.

En el primer bloque de recursos, la configuración llama a [WindowsFeature](windowsFeatureResource.md) para asegurarse de que la característica DNS está habilitada.
Los bloques de recursos siguientes llaman a recursos del módulo [xDnsServer](https://github.com/PowerShell/xDnsServer) para configurar la zona principal y los registros DNS.

Tenga en cuenta que los dos bloques `xDnsRecord` están encapsulados en bucles `foreach` que iteran a través de matrices en los datos de configuración.
Como ya indicamos, el script `DevEnv.ps1` crea los datos de configuración, los que analizaremos a continuación.

### <a name="configuration-data"></a>Datos de configuración

El archivo `DevEnv.ps1` (de la raíz del repositorio Demo_CI local, `./InfraDNS/DevEnv.ps1`) especifica los datos de configuración específicos del entorno en una tabla hash y, luego, pasa esa tabla hash a una llamada a la función `New-DscConfigurationDataDocument`, que se define en `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

El archivo `DevEnv.ps1`:

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

La función `New-DscConfigurationDataDocument` (que se define en `\Assets\DscPipelineTools\DscPipelineTools.psm1`) crea mediante programación un documento de datos de configuración desde la tabla hash (datos de nodo) y la matriz (datos no de nodo) que se pasan como los parámetros `RawEnvData` y `OtherEnvData`.

En el caso en cuestión, solo se usa el parámetro `RawEnvData`.

### <a name="the-psake-build-script"></a>El script de compilación psake

El script de compilación [psake](https://github.com/psake/psake) definido en `Build.ps1` (de la raíz del repositorio Demo_CI, `./InfraDNS/Build.ps1`) define las tareas que forman parte de la compilación.
También define las otras tareas de las que depende cada tarea.
Cuando se invoca, el script psake garantiza que la tarea especificada (o la tarea llamada `Default`, si no se especifica ninguna) se ejecute y que también se ejecuten todas las dependencias (esta acción es recursiva, por lo que se ejecutan las dependencias de las dependencias, y así sucesivamente).

En este ejemplo, la tarea `Default` se define de la siguiente manera:

```powershell
Task Default -depends UnitTests
```

La tarea `Default` no tiene implementación, pero sí tiene una dependencia de la tarea `CompileConfigs`.
La cadena de dependencias de tareas resultante asegura que se ejecuten todas las tareas del script de compilación.

En este ejemplo, el script psake se invoca con una llamada a `Invoke-PSake` en el archivo `Initiate.ps1` (ubicado en la raíz del repositorio Demo_CI):

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

Cuando creamos la definición de compilación del ejemplo en TFS, proporcionamos el archivo de script psake como el parámetro `fileName` de este script.

El script de compilación define las siguientes tareas:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Ejecuta `DevEnv.ps1`, que genera el archivo de datos de configuración.

#### <a name="installmodules"></a>InstallModules

Instala los módulos que requiere la configuración `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Llama al [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Ejecuta las pruebas unitarias [Pester](https://github.com/pester/Pester/wiki).

#### <a name="compileconfigs"></a>CompileConfigs

Compila la configuración (`DNSServer.ps1`) en un archivo MOF, usando los datos de configuración que genera la tarea `GenerateEnvironmentFiles`.

#### <a name="clean"></a>Clean

Crea la carpeta que se usa en el ejemplo y quita los resultados de pruebas, los archivos de datos de configuración y los módulos de ejecuciones anteriores.

### <a name="the-psake-deploy-script"></a>El script de implementación psake

El script de implementación [psake](https://github.com/psake/psake) definido en `Deploy.ps1` (de la raíz del repositorio Demo_CI, `./InfraDNS/Deploy.ps1`) define las tareas que implementan y ejecutan la configuración.

`Deploy.ps1` define las tareas siguientes:

#### <a name="deploymodules"></a>DeployModules

Inicia una sesión de PowerShell en `TestAgent1` e instala los módulos que contienen los recursos de DSC que se requieren en la configuración.

#### <a name="deployconfigs"></a>DeployConfigs

Llama al cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) para ejecutar la configuración en `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Ejecuta las pruebas de integración [Pester](https://github.com/pester/Pester/wiki).

#### <a name="acceptancetests"></a>AcceptanceTests

Ejecuta las pruebas de aceptación [Pester](https://github.com/pester/Pester/wiki).

#### <a name="clean"></a>Clean

Quita los módulos que se instalaron en ejecuciones anteriores y se asegura de que exista la carpeta de resultados de pruebas.

### <a name="test-scripts"></a>Scripts de prueba

Las pruebas unitarias, de integración y de aceptación están definidas en la carpeta `Tests` (de la raíz del repositorio Demo_CI, `./InfraDNS/Tests`), cada una en archivos llamados `DNSServer.tests.ps1` en sus respectivas carpetas.

Los scripts de prueba usan la sintaxis de [Pester](https://github.com/pester/Pester/wiki) y [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

#### <a name="unit-tests"></a>Pruebas unitarias

Las pruebas unitarias prueban las configuraciones de DSC para asegurarse de que hagan lo esperado cuando se ejecuten.
El script de prueba unitaria usa [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Pruebas de integración

Las pruebas de integración prueban la configuración del sistema para garantizar que cuando se integre con otros componentes, el sistema esté configurado según lo previsto. Estas pruebas se ejecutan en el nodo de destino una vez que se configura con DSC.
El script de prueba de integración usa una combinación de sintaxis de [Pester](https://github.com/pester/Pester/wiki) y [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

#### <a name="acceptance-tests"></a>Pruebas de aceptación

Las pruebas de aceptación prueban el sistema para asegurarse de que se comporte según lo previsto.
Por ejemplo, se hacen pruebas para asegurarse de que una página web devuelve la información correcta cuando se consulta.
Estas pruebas se ejecutan de manera remota desde el nodo de destino para probar escenarios reales.
El script de prueba de aceptación usa una combinación de sintaxis de [Pester](https://github.com/pester/Pester/wiki) y [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

## <a name="define-the-build"></a>Definición de la compilación

Ahora que cargamos el código en TFS y sabemos qué hace, definamos la compilación.

En esta sección, solo analizaremos los pasos de compilación que agregará a la misma. Si desea instrucciones sobre cómo crear una definición de compilación en TFS, consulte el artículo sobre cómo [crear una definición de compilación y ponerla en cola](https://www.visualstudio.com/en-us/docs/build/define/create).

Cree una nueva definición de compilación (seleccione la plantilla **vacía**) llamada "InfraDNS".
Agregue los pasos siguientes a la definición de compilación:

- Script de PowerShell
- Publicación de los resultados de las pruebas
- Copia de los archivos
- Publicación del artefacto

Después de agregar estos pasos de compilación, edite las propiedades de cada paso de la siguiente manera:

### <a name="powershell-script"></a>Script de PowerShell

1. Establezca la propiedad **Type** (Tipo) en `File Path`.
1. Establezca la propiedad **Script Path** (Ruta del script) en `initiate.ps1`.
1. Agregue `-fileName build` a la propiedad **Arguments** (Argumentos).

Este paso de compilación ejecuta el archivo `initiate.ps1`, que llama al script de compilación psake.

### <a name="publish-test-results"></a>Publicación de los resultados de las pruebas

1. Establezca **Test Result Format** (Formato de resultados de las pruebas) en `NUnit`
1. Establezca **Test Results Files** (Archivos de resultados de las pruebas) en `InfraDNS/Tests/Results/*.xml`
1. Establezca **Test Run Title** (Título de la ejecución de pruebas) en `Unit`.
1. Asegúrese de que estén seleccionadas las opciones **Control Options** **Enabled** y **Always run**.

Este paso de compilación ejecuta las pruebas unitarias en el script Pester que analizamos anteriormente y almacena los resultados en la carpeta `InfraDNS/Tests/Results/*.xml`.

### <a name="copy-files"></a>Copia de los archivos

1. Agregue cada una de las siguientes líneas a **Contents** (Contenido):

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. Establezca **TargetFolder** en `$(Build.ArtifactStagingDirectory)\`

Este paso copia los scripts de compilación y prueba en el directorio de almacenamiento provisional para que se puedan publicar como artefactos de compilación en el paso siguiente.

### <a name="publish-artifact"></a>Publicación del artefacto

1. Establezca **Path to Publish** (Ruta de acceso para publicar) en `$(Build.ArtifactStagingDirectory)\`
1. Establezca **Artifact Name** (Nombre del artefacto) en `Deploy`
1. Establezca **Artifact Type** (Tipo de artefacto) en `Server`
1. Seleccione `Enabled` en **Control Options** (Opciones de control)

## <a name="enable-continuous-integration"></a>Habilitación de la integración continua

Ahora configuraremos un desencadenador que hará que el proyecto se compile cada vez que se confirme un cambio en la rama `ci-cd-example` del repositorio Git.

1. En TFS, haga clic en la pestaña **Build & Release** (Compilación y versión)
1. Seleccione la definición de compilación `DNS Infra` y haga clic en **Editar**
1. Haga clic en la pestaña **Desencadenadores**
1. Seleccione **Integración continua (CI)** y seleccione `refs/heads/ci-cd-example` en la lista desplegable de ramas
1. Haga clic en **Guardar** y, luego, en **Aceptar**

Ahora, cualquier cambio en el repositorio Git de TFS desencadena una compilación automatizada.

## <a name="create-the-release-definition"></a>Creación de la definición de versión

Vamos a crear una definición de versión para que el proyecto se implemente en el entorno de desarrollo con cada confirmación de código.

Para esto, agregue una nueva definición de versión asociada con la definición de compilación `InfraDNS` que creó anteriormente.
Asegúrese de seleccionar **Implementación continua** para que una nueva versión se desencadene cada vez que se complete una nueva compilación.
([Artículo sobre cómo trabajar con definiciones de versión](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) y configure de la siguiente manera:

Agregue los pasos siguientes a la definición de versión:

- Script de PowerShell
- Publicación de los resultados de las pruebas
- Publicación de los resultados de las pruebas

Edite los pasos de la siguiente manera:

### <a name="powershell-script"></a>Script de PowerShell

1. Establezca el campo **Script Path** en `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Establezca el campo **Arguments** en `-fileName Deploy`

### <a name="first-publish-test-results"></a>Publicación de los resultados de primera prueba

1. Seleccione `NUnit` en el campo **Test Result Format**
1. Establezca el campo **Test Result Files** en `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Establezca **Test Run Title** en `Integration`
1. En **Control Options** (Opciones de control), active **Always run** (Ejecutar siempre)

### <a name="second-publish-test-results"></a>Publicación de los resultados de la segunda prueba

1. Seleccione `NUnit` en el campo **Test Result Format**
1. Establezca el campo **Test Result Files** en `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Establezca **Test Run Title** en `Acceptance`
1. En **Control Options** (Opciones de control), active **Always run** (Ejecutar siempre)

## <a name="verify-your-results"></a>Comprobación de los resultados

Ahora, cada vez que inserte cambios en la rama `ci-cd-example` en TFS, se iniciará una nueva compilación.
Si la compilación se completa correctamente, se desencadena una nueva implementación.

Para comprobar el resultado de la implementación, abra un explorador en la máquina cliente y vaya a `www.contoso.com`.

## <a name="next-steps"></a>Pasos siguientes

En este ejemplo se configura el servidor DNS `TestAgent1` para que la dirección URL `www.contoso.com` se resuelva en `TestAgent2`, pero en realidad no implemente un sitio web.
La estructura para hacerlo se proporciona en el repositorio que se encuentra en la carpeta `WebApp`.
Puede usar los códigos auxiliares que se proporcionan para crear scripts psake, pruebas Pester y configuraciones de DSC a fin de implementar su propio sitio web.