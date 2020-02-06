---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Lista de comprobación de creación de recursos
ms.openlocfilehash: e7401071db9cb149fff572d79568d69a0b8ea004
ms.sourcegitcommit: ea7d87a7a56f368e3175219686dfa2870053c644
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818148"
---
# <a name="resource-authoring-checklist"></a>Lista de comprobación de creación de recursos

Esta lista de comprobación es una lista de procedimientos recomendados cuando se crea un nuevo recurso de DSC.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>El módulo de recursos contiene los archivos .psd1 y schema.mof para cada recurso

Compruebe que el recurso tiene la estructura correcta y que contiene todos los archivos requeridos. Cada módulo de recursos debe contener un archivo. psd1 y todos los recursos no compuestos deben tener el archivo schema.mof. No se enumerarán los recursos que no incluyan esquema por `Get-DscResource` y los usuarios no podrán usar Intellisense al escribir código en esos módulos en ISE.
La estructura de directorios del recurso xRemoteFile, que forma parte del [módulo de recursos xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), tiene el siguiente aspecto:

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a>El recurso y el esquema son correctos

Compruebe el archivo del esquema del recurso (*. schema.mof). Puede usar el [Diseñador de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) como ayuda para desarrollar y probar su esquema.
Asegúrese de lo siguiente:

- Los tipos de propiedad sean correctos (por ejemplo, no use String para propiedades que acepten valores numéricos; debe usar UInt32 u otros tipos numéricos en su lugar).
- Los atributos de propiedad se especifican correctamente como: ([key], [required], [write], [read])
- Al menos un parámetro del esquema debe estar marcado como [key].
- La propiedad [read] no coexiste con [required], [key] o [write]
- Si se especifican varios calificadores excepto [read], [key] tiene prioridad.
- Si [write] y [required] están especificados, tiene prioridad [required].
- ValueMap esté especificado cuando sea necesario. Ejemplo:

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- El nombre descriptivo esté especificado y cumpla con las convenciones de nomenclatura de DSC.

  Ejemplo: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- Cada campo tenga una descripción descriptiva. El repositorio GitHub de PowerShell tiene buenos ejemplos, como [.schema.mof para xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Además, debe usar los cmdlets **Test-xDscResource** y **Test-xDscSchema** del [Diseñador de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) para comprobar automáticamente el recurso y el esquema:

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

Por ejemplo:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>El recurso se carga sin errores

Compruebe si el módulo de recursos se puede cargar correctamente.
Esta operación se puede realizar manualmente, para lo que hay que ejecutar `Import-Module <resource_module> -force` y confirmar que no se producen errores, o bien escribir la automatización de pruebas. Si opta por este último método, puede seguir esta estructura en el caso de prueba:

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw "Module was not imported correctly. Errors returned: $error"
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>El recurso es idempotente en el caso positivo

Una de las características fundamentales de los recursos de DSC es la idempotencia. Esto significa que la aplicación de una configuración de DSC que contenga dicho recurso varias veces siempre logrará el mismo resultado. Por ejemplo, si creamos una configuración que contenga el recurso File siguiente:

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

Después de aplicarlo por primera vez, el archivo test.txt debería aparecer en la carpeta `C:\test`. Sin embargo, las ejecuciones posteriores de la misma configuración no deben cambiar el estado de la máquina (por ejemplo, no deben crearse copias del archivo `test.txt`).
Para garantizar que un recurso es idempotente, puede llamar a `Set-TargetResource` repetidas veces al probar el recurso directamente, o bien llamar a `Start-DscConfiguration` varias veces al realizar pruebas globales. El resultado debería ser el mismo después de cada ejecución.

## <a name="test-user-modification-scenario"></a>Prueba de un escenario de modificación de un usuario

Si cambia el estado de la máquina y vuelve a ejecutar DSC, podrá comprobar que `Set-TargetResource` y `Test-TargetResource` funcionan correctamente. Estos son los pasos que debe realizar:

1. Comience con el recurso que no está en el estado deseado.
2. Ejecute la configuración con su recurso.
3. Compruebe que `Test-DscConfiguration` devuelve True
4. Modifique el elemento configurado para que no esté en el estado deseado
5. Compruebe que `Test-DscConfiguration` devuelve False

Este es un ejemplo más concreto de uso del recurso Registry:

1. Comience con la clave del Registro que no está en el estado deseado.
2. Ejecute `Start-DscConfiguration` con una configuración para colocarla en el estado deseado y compruebe si pasa.
3. Ejecute `Test-DscConfiguration` y compruebe que devuelve True
4. Modifique el valor de la clave para que no esté en el estado deseado.
5. Ejecute `Test-DscConfiguration` y compruebe que devuelve False
6. La funcionalidad `Get-TargetResource` se comprobó con `Get-DscConfiguration`

`Get-TargetResource` debe devolver los detalles del estado actual del recurso. Asegúrese de probarlo, para lo que debe llamar a `Get-DscConfiguration` después de aplicar la configuración y comprobar que el resultado refleja correctamente el estado actual de la máquina. Es importante probarlo por separado, ya que los problemas de esta área no aparecerán al llamar a `Start-DscConfiguration`.

## <a name="call-getsettest-targetresource-functions-directly"></a>Llame a las funciones **Get/Set/Test-TargetResource** directamente

Asegúrese de probar las funciones **Get/Set/Test-TargetResource** implementadas en el recurso. Para ello, llámelas directamente y compruebe que funcionan según lo esperado.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Realice la comprobación global mediante **Start-DscConfiguration**.

Es importante llamar directamente a las funciones **Get/Set/Test-TargetResource** para probarlas, pero no todos los problemas se detectarán de esta forma. Debe centrar una parte importante de las pruebas en el uso de `Start-DscConfiguration` o el servidor de incorporación de cambios. De hecho, así es como los usuarios usarán el recurso, por lo que no subestime la importancia de este tipo de pruebas.
Posibles tipos de problemas:

- Es posible que Credential/Session se comporten de manera diferente porque el agente DSC se ejecuta como un servicio.  Asegúrese de probar todas las características aquí de un extremo a otro.
- Los errores que produce `Start-DscConfiguration` pueden ser diferentes de los que se muestran al llamar a la función `Set-TargetResource` directamente.

## <a name="test-compatibility-on-all-dsc-supported-platforms"></a>Prueba de compatibilidad en todas las plataformas compatibles con DSC

El recurso debería funcionar en todas las plataformas compatibles de DSC (Windows Server 2008 R2 y versiones más recientes). Instalar la versión más reciente de WMF (Windows Management Framework) en el sistema operativo para obtener la versión más reciente de DSC. Si el recurso no funciona en algunas de estas plataformas por diseño, debería devolverse un mensaje de error específico. Asimismo, asegúrese de que el recurso comprueba si los cmdlets que está llamando están presentes en una máquina determinada. En Windows Server 2012 se agregó un gran número de cmdlets nuevos que no están disponibles en Windows Server 2008 R2, incluso con WMF instalado.

## <a name="verify-on-windows-client-if-applicable"></a>Compruébelo en el cliente de Windows (si es aplicable)

Una laguna muy común de las pruebas consiste en comprobar el recurso solo en las versiones de servidor de Windows. Muchos recursos también están diseñados para funcionar en las SKU de cliente. Si es su caso, no olvide probarlo también en estas plataformas.

## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource enumera el recurso

Después de implementar el módulo, una llamada a `Get-DscResource` debería enumerar su recurso, entre otros, como resultado. Si no encuentra el recurso en la lista, asegúrese de que el archivo schema.mof de ese recurso existe.

## <a name="resource-module-contains-examples"></a>El módulo de recursos contiene ejemplos

La creación de ejemplos de calidad ayudará a otros usuarios a aprender a usarlo. Esto es fundamental, sobre todo porque muchos usuarios tratan el código de ejemplo como documentación.

- En primer lugar, debe determinar los ejemplos que se incluirán con el módulo; como mínimo, debe cubrir los casos de uso más importantes para el recurso:
- Si el módulo contiene varios recursos que deben trabajar conjuntamente para un escenario de un extremo a otro, sería ideal que el ejemplo básico de un extremo a otro fuese primero.
- Los ejemplos iniciales deben ser muy simples: cómo empezar a trabajar con los recursos en pequeños fragmentos manejables (por ejemplo, crear un nuevo VHD).
- Los ejemplos siguientes deben basarse en esos ejemplos (por ejemplo, crear una VM a partir de un VHD, quitar la VM o modificarla) y mostrar una funcionalidad avanzada (por ejemplo, crear una VM con memoria dinámica).
- Las configuraciones de ejemplo deben tener parámetros (todos los valores deben pasarse a la configuración como parámetros y no debería haber ningún valor codificado):

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- Es recomendable incluir un ejemplo (comentado) de cómo llamar a la configuración con los valores reales al final del script de ejemplo.
  Por ejemplo, en la configuración anterior no es necesariamente obvio que la mejor forma de especificar UserAgent es:

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` En cuyo caso un comentario puede clarificar la ejecución prevista de la configuración:

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- Para cada ejemplo, escriba una breve descripción que explique qué hace y el significado de los parámetros.
- Asegúrese de que los ejemplos tratan la mayoría de los escenarios importantes para el recurso y, si no falta nada, compruebe que todos se ejecutan y coloque la máquina en el estado deseado.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Los mensajes de error son fáciles de entender y ayudar a los usuarios a solucionar problemas

Los mensajes de error correctos deben:

- Existir: el principal problema de los mensajes de error es que a menudo no existen, por lo que debe asegurarse de que estén presentes.
- Fáciles de entender: usar lenguaje natural, sin códigos de error ilegibles.
- Precisos: describir el problema con exactitud.
- Constructivos: aconsejar cómo corregir el problema.
- Educados: no culpar al usuario ni hacerle sentir mal.

Asegúrese de comprobar los errores en los escenarios de un extremo a otro (mediante `Start-DscConfiguration`), ya que pueden diferir de los devueltos al ejecutar las funciones de recursos directamente.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Los mensajes de registro son fáciles de entender e informativos (incluidos los registros –verbose, –debug y ETW)

Asegúrese de que los registros que emite el recurso son fáciles de comprender y proporcionan valor al usuario. Los recursos deben generar toda la información que pueda resultar útil para el usuario, pero un mayor número de registros no siempre es mejor. Debe evitar la redundancia y la salida de datos que no proporcionen valor adicional: evite que nadie deba consultar cientos de entradas de registro para encontrar lo que busca. Por supuesto, la ausencia de registros tampoco es una solución aceptable para este problema.

Al realizar pruebas, también debe analizar los registros detallados y de depuración (ejecutando `Start-DscConfiguration` con los modificadores `–Verbose` y `–Debug`, respectivamente), así como los registros ETW. Para ver los registros de ETW de DSC, vaya al Visor de eventos y abra la carpeta siguiente: Applications and Services- Microsoft - Windows - Desired State Configuration.  De forma predeterminada, será Canal operativo, pero asegúrese de habilitar Canal analítico y Canal de depuración antes de ejecutar la configuración.
Para habilitar los canales analítico o de depuración, puede ejecutar el script siguiente:

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>La implementación de recursos no contiene rutas de acceso codificadas

Asegúrese de no hay ninguna ruta de codificada en la implementación de recursos, especialmente si adoptan el idioma (en-us) o si hay variables del sistema que se pueden usar.
Si el recurso necesita acceder a rutas de acceso específicas, use las variables de entorno en lugar de codificar la ruta de acceso, ya que puede diferir en otras máquinas.

Ejemplo:

En lugar de:

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

Puede escribir:

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a>La implementación de recursos no contiene información de usuario

Asegúrese de que no hay nombres de correo electrónico, información de la cuenta o nombres de personas en el código.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>El recurso se probó con credenciales válidas o no válidas

Si el recurso toma una credencial como parámetro:

- Compruebe que el recurso funciona cuando Sistema local (o la cuenta de equipo para los recursos remotos) no tiene acceso.
- Compruebe que el recurso funciona con una credencial especificada para Get, Set y Test
- Si el recurso accede a recursos compartidos, pruebe todas las variantes que necesite admitir, como:
  - Recursos compartidos de Windows estándar.
  - Recursos compartidos de DFS.
  - Recursos compartidos de SAMBA (si desea admitir Linux).

## <a name="resource-does-not-require-interactive-input"></a>El recurso no requiere una entrada interactiva

Las funciones **Get/Set/Test-TargetResource** deben ejecutarse automáticamente y no deben esperar la entrada del usuario en ninguna fase de la ejecución (por ejemplo, no debe usar `Get-Credential`dentro de estas funciones). Si la entrada del usuario es necesaria, debe pasarla a la configuración como un parámetro durante la fase de compilación.

## <a name="resource-functionality-was-thoroughly-tested"></a>La funcionalidad del recurso se probó de manera exhaustiva

Esta lista de comprobación contiene elementos que es importante probar y/o que suelen omitirse. Se realizarán muchas pruebas, principalmente funcionales, que serán específicas para el recurso que se está probando y que no se mencionan aquí. No olvide los casos de prueba negativos.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Procedimiento recomendado: el módulo de recursos contiene la carpeta Tests con el script ResourceDesignerTests.ps1

Se recomienda crear la carpeta "Tests" en el módulo de recursos, crear el archivo `ResourceDesignerTests.ps1` y agregar pruebas mediante **Test-xDscResource** y **Test-xDscSchema** para todos los recursos del módulo determinado.
De este modo puede validar rápidamente los esquemas de todos los recursos de los módulos determinados y realizar una comprobación de integridad antes de la publicación.
Para xRemoteFile, `ResourceTests.ps1` podría ser tan simple como:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Procedimiento recomendado: la carpeta de recursos contiene el script del Diseñador de recursos para generar el esquema

Cada recurso debe contener un script del Diseñador de recursos que genere un esquema MOF del recurso. Este archivo debe colocarse en `<ResourceName>\ResourceDesignerScripts` y denominarse Generate`<ResourceName>Schema.ps1` Para el recurso xRemoteFile, este archivo se llamaría `GenerateXRemoteFileSchema.ps1` y contendría:

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a>Procedimiento recomendado: el recurso admite -whatif

Si el recurso realiza operaciones "peligrosas", se recomienda implementar la funcionalidad `-WhatIf`. Después de hacerlo, asegúrese de que la salida `-WhatIf` describe correctamente las operaciones que se realizarían si se ejecutara el comando sin el modificador `-WhatIf`.
Asimismo, compruebe que las operaciones no se ejecutan (no se realiza ningún cambio en el estado del nodo) cuando el modificador `–WhatIf` está presente.
Por ejemplo, supongamos que está probando el recurso File. A continuación se muestra una configuración sencilla que crea el archivo `test.txt` con contenido "test":

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

Si compilamos y, después, ejecutamos la configuración con el modificador `-WhatIf`, la salida nos indica qué ocurre exactamente cuando ejecutamos la configuración. Sin embargo, no se ejecutó la configuración en sí (no se creó el archivo `test.txt`).

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

Esta lista no es exhaustiva, pero abarca muchos problemas importantes que se pueden detectar durante el diseño, el desarrollo y las pruebas de los recursos de DSC.
