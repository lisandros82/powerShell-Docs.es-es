---
title: Instalación de un módulo de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: f7899713dd273b793017adfa0a20b3ff3352b62a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862171"
---
# <a name="installing-a-powershell-module"></a>Instalación de un módulo de PowerShell

Después de haber creado el módulo de PowerShell, probablemente deseará instalar el módulo en un sistema, para que usted u otros usuarios pueden usar. Por lo general, esto simplemente consiste en copiar los archivos de módulo (es decir, el. psm1, o el ensamblado binario, el manifiesto del módulo y los otros archivos asociados) en un directorio en el equipo. Para un proyecto muy pequeño, esto puede ser tan sencillo como copiar y pegar los archivos con el Explorador de Windows en un único equipo remoto. Sin embargo, para las soluciones más grandes se puede usar un proceso de instalación más sofisticado. Independientemente de cómo obtener el módulo en el sistema, PowerShell puede usar varias técnicas que permitirá a los usuarios a encontrar y usar los módulos. (Para obtener más información, consulte [importar un módulo de PowerShell](./importing-a-powershell-module.md).) Por lo tanto, el principal problema para la instalación es asegurarse de que PowerShell pueda encontrar el módulo.

Este tema contiene las siguientes secciones:

- Reglas para la instalación de módulos

- ¿Dónde instalar los módulos

- Instalar varias versiones de un módulo

- Control de conflictos de nombres de comando

## <a name="rules-for-installing-modules"></a>Reglas para la instalación de módulos

La siguiente información se aplica a todos los módulos, incluidos los módulos que se crean para su propio uso, los módulos que se obtienen de otras partes y los módulos que se distribución a otros usuarios.

### <a name="install-modules-in-psmodulepath"></a>Instalación de módulos en PSModulePath

Siempre que sea posible, instale todos los módulos en una ruta de acceso que aparece en el **PSModulePath** variable de entorno o agregar la ruta de acceso del módulo a la **PSModulePath** valor de variable de entorno.

El **PSModulePath** variable de entorno ($Env: PSModulePath) contiene las ubicaciones de los módulos de Windows PowerShell. Los cmdlets se basan en el valor de esta variable de entorno para encontrar los módulos.

De forma predeterminada, el **PSModulePath** valor de variable de entorno contiene el siguiente sistema y los directorios del módulo de usuario, pero puede agregar a y edite el valor.

- $PSHome\Modules (% Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Esta ubicación está reservada para módulos que se incluyen con Windows. No instale los módulos a esta ubicación.

- $Home\Documents\WindowsPowerShell\Modules (% UserProfile%\Documents\WindowsPowerShell\Modules)

- $Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)

  Para obtener el valor de la **PSModulePath** variable de entorno, utilice uno de los siguientes comandos.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Para agregar una ruta de acceso del módulo al valor de la **PSModulePath** variable de entorno de valor, use el siguiente formato de comando. Este formato utiliza el **SetEnvironmentVariable** método de la **System.Environment** clase para realizar un cambio de sesión independiente en el **PSModulePath** entorno variable.

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Una vez haya agregado la ruta de acceso **PSModulePath**, debe difundir un mensaje sobre el cambio del entorno. Difunde el cambio permite que otras aplicaciones, como el shell recoger el cambio. Para difundir el cambio, tener el código de instalación del producto enviar un **WM_SETTINGCHANGE** de mensajes con `lParam` establecido en la cadena "Entorno". Asegúrese de enviar el mensaje después de que se ha actualizado el código de instalación del módulo **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Utilice el nombre del directorio de módulo correcto

Un módulo de "correcto" es un módulo que se almacena en un directorio que tiene el mismo nombre que el nombre de base de al menos un archivo en el directorio del módulo. Si un módulo no está bien formado, Windows PowerShell no la reconoce como un módulo.

El "nombre de base" de un archivo es el nombre sin la extensión de nombre de archivo. En un módulo tiene el formato correcto, el nombre del directorio que contiene los archivos del módulo debe coincidir con el nombre de base de al menos un archivo en el módulo.

Por ejemplo, en el módulo de ejemplo Fabrikam, el directorio que contiene los archivos de módulo se denomina "Fabrikam" y al menos un archivo tiene el nombre de base "Fabrikam". En este caso, Fabrikam.psd1 y Fabrikam.dll tienen el nombre de base "Fabrikam".

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Efecto de una instalación incorrecta

Si el módulo no es correcto y su ubicación no se incluye en el valor de la **PSModulePath** variable de entorno, las características básicas de detección de Windows PowerShell, como la siguiente, no funcionan.

- La característica de carga automática del módulo no puede importar el módulo automáticamente.

- El `ListAvailable` parámetro de la [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet no puede encontrar el módulo.

- El [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet no puede encontrar el módulo. Para importar el módulo, debe proporcionar la ruta de acceso completa al archivo de módulo raíz o archivo de manifiesto de módulo.

  Características adicionales, como la siguiente, no funcionan a menos que el módulo se importa en la sesión. En los módulos correctos en el **PSModulePath** variable de entorno, estas características funcionan incluso cuando no se importa el módulo en la sesión.

- El [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet no puede encontrar los comandos en el módulo.

- El [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) no puede actualizar o guardar la Ayuda del módulo de cmdlets.

- El [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet no puede buscar y mostrar los comandos en el módulo.

  Faltan los comandos en el módulo en el `Show-Command` en Windows PowerShell Integrated Scripting Environment (ISE) de la ventana.

## <a name="where-to-install-modules"></a>¿Dónde instalar los módulos

En esta sección se explica dónde en el sistema de archivos para instalar los módulos de Windows PowerShell. La ubicación depende de cómo se usa el módulo.

### <a name="installing-modules-for-a-specific-user"></a>Instalación de módulos para un usuario específico

Si crea su propio módulo u obtener un módulo desde otra parte, como un sitio Web Comunidad de Windows PowerShell, y desea que el módulo está disponible para su cuenta de usuario solo, instale el módulo en el directorio de módulos específicos del usuario.

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

El directorio de módulos específicos del usuario se agrega al valor de la **PSModulePath** variable de entorno de forma predeterminada.

### <a name="installing-modules-for-all-users-in-program-files"></a>Instalación de módulos para todos los usuarios en archivos de programa

Si desea que un módulo que estén disponibles para todas las cuentas de usuario en el equipo, instale el módulo en la ubicación de archivos de programa.

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> De forma predeterminada en Windows PowerShell 4.0 y versiones posteriores, la ubicación de archivos de programa se agrega al valor de la variable de entorno PSModulePath. Las versiones anteriores de Windows PowerShell, manualmente puede crear el ((%ProgramFiles%\WindowsPowerShell\Modules) ubicación los archivos de programa y agregar esta ruta de acceso a la variable de entorno PSModulePath, como se describió anteriormente.

### <a name="installing-modules-in-a-product-directory"></a>Instalación de módulos en un directorio de productos

Si va a distribuir el módulo a otras partes, use la ubicación de archivos de programa predeterminado que se ha descrito anteriormente, o crear su propio subdirectorio específico de la compañía o específico del producto del directorio % ProgramFiles %.

Por ejemplo, las tecnologías de Fabrikam, una compañía ficticia, se envía a un módulo de Windows PowerShell para su producto del Administrador de Fabrikam. Instalador del módulo, crea un subdirectorio de módulos en el subdirectorio del producto de Fabrikam Manager.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Para habilitar las características de detección del módulo de Windows PowerShell encontrar el módulo de Fabrikam, el instalador del módulo Fabrikam agrega la ubicación de módulo en el valor de la **PSModulePath** variable de entorno.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technolgies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Instalación de módulos en el directorio de archivos comunes

Si se usa un módulo por varios componentes de un producto o por varias versiones de un producto, instale el módulo en un subdirectorio específico del módulo del subdirectorio Files\Modules %ProgramFiles%\Common.

En el ejemplo siguiente, se instala el módulo de Fabrikam en un subdirectorio de Fabrikam del subdirectorio Files\Modules %ProgramFiles%\Common. Tenga en cuenta que cada módulo reside en su propio subdirectorio en el subdirectorio de módulos.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

A continuación, el programa de instalación garantiza que el valor de la **PSModulePath** variable de entorno incluye la ruta de acceso del subdirectorio de módulos comunes de archivos.

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>Instalar varias versiones de un módulo

Para instalar varias versiones del mismo módulo, use el procedimiento siguiente.

1. Cree un directorio para cada versión del módulo. Incluya el número de versión en el nombre del directorio.

2. Cree un manifiesto de módulo para cada versión del módulo. En el valor de la **ModuleVersion** en el manifiesto de la clave, escriba el número de versión del módulo. Guarde el archivo de manifiesto (. psd1) en el directorio específico de la versión del módulo.

3. Agregar la ruta de acceso de carpeta de módulo raíz en el valor de la **PSModulePath** variable de entorno, como se muestra en los ejemplos siguientes.

Para importar una versión concreta del módulo, el usuario final puede usar el `MinimumVersion` o `RequiredVersion` parámetros de la [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Por ejemplo, si el módulo de Fabrikam está disponible en las versiones 8.0 y 9.0, la estructura de directorios del módulo de Fabrikam puede parecerse al siguiente.

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

El instalador agrega tanto de las rutas de acceso del módulo a la **PSModulePath** valor de variable de entorno.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Cuando termine estos pasos, el **ListAvailable** parámetro de la [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) obtiene ambos de los módulos de Fabrikam. Para importar un módulo determinado, utilice el `MiminumVersion` o `RequiredVersion` parámetros de la [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Si ambos módulos se importan en la misma sesión y los módulos contienen cmdlets con los mismos nombres, los cmdlets que se importa en último lugar son eficaces en la sesión.

## <a name="handling-command-name-conflicts"></a>Control de conflictos de nombres de comando

Cuando los comandos que exporta un módulo tienen el mismo nombre que los comandos en la sesión del usuario, pueden producirse conflictos de nombre de comando.

Cuando una sesión contiene dos comandos que tienen el mismo nombre, Windows PowerShell se ejecuta el tipo de comando que tiene prioridad. Cuando una sesión contiene dos comandos que tienen el mismo nombre y el mismo tipo, Windows PowerShell se ejecuta el comando que se agregó a la sesión más recientemente. Para ejecutar un comando que no se ejecuta de forma predeterminada, los usuarios pueden calificar el nombre de comando con el nombre del módulo.

Por ejemplo, si la sesión contiene una `Get-Date` función y el `Get-Date` , Windows PowerShell ejecuta la función de forma predeterminada. Para ejecutar el cmdlet, escriba el comando precedido por el nombre del módulo, como:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Para evitar conflictos de nombres, pueden utilizar los autores del módulo el **DefaultCommandPrefix** clave en el manifiesto de módulo para especificar un prefijo de sustantivo para todos los comandos exportados desde el módulo.

Los usuarios pueden usar el **prefijo** parámetro de la `Import-Module` cmdlet para utilizar un prefijo alternativo. El valor de la **prefijo** parámetro tiene prioridad sobre el valor de la **DefaultCommandPrefix** clave.

## <a name="see-also"></a>Véase también

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
