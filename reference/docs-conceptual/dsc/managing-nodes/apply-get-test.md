---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Aplicación, obtención y prueba de las configuraciones en un nodo
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953842"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>Aplicación, obtención y prueba de las configuraciones en un nodo

Esta guía le mostrará cómo trabajar con las configuraciones en un nodo de destino. Se divide en los pasos siguientes:

## <a name="apply-a-configuration"></a>Aplicación de una configuración

Para aplicar y administrar una configuración, es necesario generar un archivo ".mof". El siguiente código representará una configuración simple que se usará en esta guía.

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

La compilación de esta configuración dará como resultado dos archivos ".mof".

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Para aplicar una configuración, use el cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration). El parámetro `-Path` especifica un directorio donde residen los archivos ".mof". Si no se especifica `-Computername`, `Start-DSCConfiguration` intentará aplicar cada configuración al nombre de equipo especificado por el nombre del archivo ".mof" (\<nombredeequipo\>.mof). Especifique `-Verbose` e `Start-DSCConfiguration` para ver una salida más detallada.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Si `-Wait` no se especifica, verá un trabajo creado. El trabajo creado tendrá un **ChildJob** para cada archivo ".mof" procesado por `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Si una configuración está tardando mucho tiempo y desea detenerla, puede usar [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) para detener la aplicación en el nodo local.

```powershell
Stop-DSCConfiguration -Force
```

Una vez que haya finalizado, puede ver el estado de los trabajos a través del objeto de trabajo devuelto por [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

Para ver la salida de **Verbose**, use los siguientes comandos para ver la secuencia **Verbose** para cada **ChildJob**. Para más información sobre los trabajos de PowerShell, vea [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs) (Acerca de los trabajos).

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

A partir de PowerShell 5.0, se agregó el parámetro `-UseExisting` a `Start-DSCConfiguration`. Mediante la especificación de `-UseExisting`, indica al cmdlet que use la configuración aplicada existente en lugar de una especificada por el parámetro `-Path`.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Prueba de una configuración

Puede probar una configuración aplicada actualmente mediante [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` devolverá `True` si el nodo es compatible, y `False` si no lo es.

```powershell
Test-DSCConfiguration
```

A partir de PowerShell 5.0, se ha agregado el parámetro `-Detailed`, que devuelve un objeto con las colecciones de **ResourcesInDesiredState** y **ResourcesNotInDesiredState**.

```powershell
Test-DSCConfiguration -Detailed
```

A partir de PowerShell 5.0, puede probar una configuración sin aplicarla. El parámetro `-ReferenceConfiguration` acepta la ruta de acceso de un archivo ".mof" en la que probar el nodo. No se realizan acciones **Set** en el nodo. En PowerShell 4.0, hay soluciones alternativas para probar una configuración sin aplicarla, pero no se tratan aquí.

## <a name="get-configuration-values"></a>Obtención de valores de configuración

El cmdlet [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) devuelve los valores actuales de los recursos configurados en la configuración aplicada actualmente.

```powershell
Get-DSCConfiguration
```

Los resultados de ejemplo de nuestra configuración tendrían un aspecto similar al siguiente si se aplicaron correctamente.

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a>Obtención de estado de configuración

A partir de PowerShell 5.0, el cmdlet [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) le permite ver el historial de las configuraciones aplicadas al nodo. DSC de PowerShell realiza un seguimiento de los últimos {{N}} valores de configuración aplicados en modo de **inserción** o **extracción**. Esto incluye las comprobaciones de *coherencia* ejecutadas por el LCM. De forma predeterminada, `Get-DSCConfigurationStatus` muestra solo la última entrada del historial.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Use el parámetro `-All` para ver todo el historial del estado de configuración.

> [!NOTE]
> La salida se trunca por razones de brevedad.

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a>Administración de documentos de configuración

El LCM administra la configuración del nodo al trabajar con **documentos de configuración**. Estos archivos ".mof" residen en el directorio "C:\Windows\System32\Configuration".

A partir de PowerShell 5.0, [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) le permite quitar los archivos ".mof" para detener las futuras comprobaciones de coherencia o quitar una configuración que tiene errores cuando se aplica. El parámetro `-Stage` le permite especificar qué archivo ".mof" desea quitar.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> En PowerShell 4.0, todavía puede quitar estos archivos ".mof" directamente mediante [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Publicación de configuraciones

A partir de PowerShell 5.0, se agregó el cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration). Este cmdlet permite publicar un archivo ".mof" en equipos remotos, sin aplicarlo.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Vea también

- [Obtención, prueba y establecimiento](../resources/get-test-set.md)
