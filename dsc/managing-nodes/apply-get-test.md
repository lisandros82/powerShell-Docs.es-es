---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Aplicación, obtención y prueba de las configuraciones en un nodo
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402946"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>Aplicación, obtención y prueba de las configuraciones en un nodo

Esta guía le mostrará cómo trabajar con las configuraciones en un nodo de destino. Esta guía se divide en los pasos siguientes:

## <a name="apply-a-configuration"></a>Aplicar una configuración

Para aplicar y administrar una configuración, es necesario generar un archivo "MOF". El siguiente código representa una configuración simple que se usará en esta guía.

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

Compilación de esta configuración dará como resultado dos archivos "MOF".

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Para aplicar una configuración, use el [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. El `-Path` parámetro especifica un directorio donde residen los archivos "MOF". Si no hay ningún `-Computername` se especifica, `Start-DSCConfiguration` intentará aplicar cada configuración en el nombre del equipo especificado por el nombre del archivo '.mof' (\<computername\>.mof). Especificar `-Verbose` a `Start-DSCConfiguration` para ver los resultados más detallados.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Si `-Wait` no se especifica, verá un trabajo que creó. El trabajo creado tendrá una **ChildJob** para cada archivo de "MOF" procesados por `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Si una configuración está tardando mucho tiempo y desea detenerlo, puede usar [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) para detener la aplicación en el nodo local.

```powershell
Stop-DSCConfiguration -Force
```

Una vez que haya finalizado, puede ver el estado de los trabajos a través del objeto de trabajo devueltos por [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

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

Para ver el **detallado** de salida, utilice los siguientes comandos para ver el **detallado** secuencia para cada **ChildJob**. Para obtener más información acerca de los trabajos de PowerShell, consulte [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

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

A partir de PowerShell 5.0, el `-UseExisting` parámetro se agregó a `Start-DSCConfiguration`. Mediante la especificación de `-UseExisting`, indicar al cmdlet que use la configuración aplicada existente en lugar de uno especificado por el `-Path` parámetro.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Probar una configuración

Puede probar una configuración aplicada actualmente mediante [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` devolverá `True` si el nodo es compatible, y `False` si no lo está.

```powershell
Test-DSCConfiguration
```

A partir de PowerShell 5.0, el `-Detailed` parámetro se ha agregado que devuelve un objeto con las colecciones de **ResourcesInDesiredState** y **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

A partir de PowerShell 5.0, puede probar una configuración sin aplicarlo. El `-ReferenceConfiguration` parámetro acepta la ruta de acceso de un archivo de "MOF" para probar el nodo contra. No **establecer** se realizan acciones en el nodo. En PowerShell 4.0, hay soluciones alternativas para probar una configuración sin aplicarlo, pero no se tratan aquí.

## <a name="get-configuration-values"></a>Obtener los valores de configuración

El [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet devuelve los valores actuales de los recursos configurados en la configuración aplicada actualmente.

```powershell
Get-DSCConfiguration
```

Resultados del ejemplo de nuestra configuración tendría un aspecto similar al siguiente si se aplicaron correctamente.

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

## <a name="get-configuration-status"></a>Obtener estado de configuración

A partir de PowerShell 5.0 el [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet le permite ver el historial de las configuraciones aplicadas al nodo. DSC de PowerShell realiza un seguimiento de los últimos valores de configuración de {{N}} aplicados en **Push** o **extraer** modo. Esto incluye cualquier *coherencia* comprueba que el LCM la ejecuta. De forma predeterminada, `Get-DSCConfigurationStatus` muestra solo la última entrada del historial.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Use el `-All` parámetro para ver todo el historial de estado de configuración.

> [!NOTE]
> Salida queda truncada por razones de brevedad.

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

## <a name="manage-configuration-documents"></a>Administrar documentos de configuración

El LCM administra la configuración del nodo al trabajar con **documentos de configuración**. Estos archivos "MOF" residen en el directorio "C:\Windows\System32\Configuration".

A partir de PowerShell 5.0 el [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) le permite quitar los archivos "MOF" para detener las comprobaciones de coherencia futura o quitar una configuración que tiene errores cuando se aplica. El `-Stage` parámetro le permite especificar qué archivo de "MOF" que desea quitar.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> En PowerShell 4.0, todavía puede quitar estos archivos "MOF" directamente mediante [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Las configuraciones de publicación

A partir de PowerShell 5.0, el [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) se agregó el cmdlet. Este cmdlet permite publicar un archivo de "MOF" en equipos remotos, sin aplicarlo.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Vea también

- [Obtención, prueba y establecimiento](../resources/get-test-set.md)
