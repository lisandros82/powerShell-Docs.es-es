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
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367074"
---
# <a name="installing-a-powershell-module"></a>Instalación de un módulo de PowerShell

Una vez creado el módulo de PowerShell, es probable que desee instalar el módulo en un sistema, de modo que usted u otros usuarios puedan usarlo. Por lo general, esto consiste en copiar los archivos de módulo (por ej., psm1, el ensamblado binario, el manifiesto del módulo y cualquier otro archivo asociado) en un directorio de ese equipo. Para un proyecto muy pequeño, puede ser tan sencillo como copiar y pegar los archivos con el explorador de Windows en un único equipo remoto. sin embargo, en el caso de soluciones de mayor tamaño, es posible que desee usar un proceso de instalación más sofisticado. Independientemente de cómo obtenga el módulo en el sistema, PowerShell puede usar una serie de técnicas que permitirán a los usuarios buscar y usar los módulos. Por lo tanto, el problema principal de la instalación es asegurarse de que PowerShell pueda encontrar el módulo. Para obtener más información, vea [importar un módulo de PowerShell](./importing-a-powershell-module.md).

## <a name="rules-for-installing-modules"></a>Reglas para la instalación de módulos

La siguiente información pertenece a todos los módulos, incluidos los módulos que se crean para su propio uso, los módulos que se obtienen de otras partes y los módulos que se distribuyen a otros usuarios.

### <a name="install-modules-in-psmodulepath"></a>Instalación de módulos en PSModulePath

Siempre que sea posible, instale todos los módulos en una ruta de acceso que aparece en la variable de entorno **PSModulePath** o agregue la ruta de acceso del módulo al valor de la variable de entorno **PSModulePath** .

La variable de entorno **PSModulePath** ($env:P smodulepath) contiene las ubicaciones de los módulos de Windows PowerShell. Los cmdlets se basan en el valor de esta variable de entorno para buscar módulos.

De forma predeterminada, el valor de la variable de entorno **PSModulePath** contiene los siguientes directorios del módulo de usuario y del sistema, pero puede Agregar y editar el valor.

- `$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Esta ubicación está reservada para los módulos que se distribuyen con Windows. No instale módulos en esta ubicación.

- `$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)

  Para obtener el valor de la variable de entorno **PSModulePath** , use cualquiera de los siguientes comandos.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Para agregar una ruta de acceso de módulo al valor del valor de la variable de entorno **PSModulePath** , use el siguiente formato de comando. Este formato usa el método **SetEnvironmentVariable** de la clase **System. Environment** para hacer un cambio independiente de la sesión en la variable de entorno **PSModulePath** .

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Una vez que haya agregado la ruta de acceso a **PSModulePath**, debe difundir un mensaje de entorno sobre el cambio. Difundir el cambio permite a otras aplicaciones, como el Shell, recoger el cambio. Para difundir el cambio, haga que el código de instalación del producto envíe un mensaje **WM_SETTINGCHANGE** con `lParam` establecido en la cadena "entorno". Asegúrese de enviar el mensaje después de que el código de instalación del módulo haya actualizado **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Usar el nombre de directorio del módulo correcto

Un módulo con formato correcto es un módulo que se almacena en un directorio que tiene el mismo nombre que el nombre base de al menos un archivo en el directorio del módulo. Si un módulo no tiene el formato correcto, Windows PowerShell no lo reconoce como un módulo.

El "nombre base" de un archivo es el nombre sin la extensión de nombre de archivo. En un módulo con formato correcto, el nombre del directorio que contiene los archivos de módulo debe coincidir con el nombre base de al menos un archivo en el módulo.

Por ejemplo, en el módulo Fabrikam de ejemplo, el directorio que contiene los archivos de módulo se denomina "fabrikam" y al menos un archivo tiene el nombre base "fabrikam". En este caso, fabrikam. psd1 y fabrikam. dll tienen el nombre base "fabrikam".

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

Si el módulo no tiene el formato correcto y su ubicación no se incluye en el valor de la variable de entorno **PSModulePath** , las características de detección básicas de Windows PowerShell, como la siguiente, no funcionan.

- La característica de carga automática de módulos no puede importar automáticamente el módulo.

- El parámetro `ListAvailable` del cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) no puede encontrar el módulo.

- El cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) no puede encontrar el módulo. Para importar el módulo, debe proporcionar la ruta de acceso completa al archivo de módulo raíz o al archivo de manifiesto del módulo.

  Otras características, como las siguientes, no funcionan a menos que el módulo se importe en la sesión. En los módulos con formato correcto de la variable de entorno **PSModulePath** , estas características funcionan incluso cuando el módulo no se importa en la sesión.

- El cmdlet [get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) no puede encontrar comandos en el módulo.

- Los cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) no pueden actualizar ni guardar la ayuda del módulo.

- El cmdlet [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) no puede encontrar y mostrar los comandos en el módulo.

  Faltan los comandos del módulo en la ventana `Show-Command` en el entorno de scripting integrado (ISE) de Windows PowerShell.

## <a name="where-to-install-modules"></a>Dónde instalar los módulos

En esta sección se explica en qué parte del sistema de archivos se instalan los módulos de Windows PowerShell. La ubicación depende de cómo se use el módulo.

### <a name="installing-modules-for-a-specific-user"></a>Instalación de módulos para un usuario específico

Si crea su propio módulo u obtiene un módulo de otra entidad, como un sitio web de la comunidad de Windows PowerShell, y desea que el módulo esté disponible solo para su cuenta de usuario, instale el módulo en el directorio de los módulos específicos del usuario.

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

De forma predeterminada, el directorio de módulos específico del usuario se agrega al valor de la variable de entorno **PSModulePath** .

### <a name="installing-modules-for-all-users-in-program-files"></a>Instalación de módulos para todos los usuarios de archivos de programa

Si desea que un módulo esté disponible para todas las cuentas de usuario del equipo, instale el módulo en la ubicación de archivos de programa.

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> La ubicación de los archivos de programa se agrega al valor de la variable de entorno PSModulePath de forma predeterminada en Windows PowerShell 4,0 y versiones posteriores. En el caso de las versiones anteriores de Windows PowerShell, puede crear manualmente la ubicación de los archivos de programa ((%ProgramFiles%\WindowsPowerShell\Modules) y agregar esta ruta de acceso a la variable de entorno PSModulePath como se describió anteriormente.

### <a name="installing-modules-in-a-product-directory"></a>Instalación de módulos en un directorio de producto

Si va a distribuir el módulo a otras entidades, use la ubicación predeterminada de los archivos de programa descritos anteriormente, o bien cree su propio subdirectorio específico de la empresa o específico del producto del directorio% ProgramFiles%.

Por ejemplo, Fabrikam Technologies, una empresa ficticia, envía un módulo de Windows PowerShell para su producto Fabrikam Manager. Su instalador de módulos crea un subdirectorio modules en el subdirectorio Product de Fabrikam Manager.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Para habilitar las características de detección de módulos de Windows PowerShell para encontrar el módulo Fabrikam, el instalador del módulo de Fabrikam agrega la ubicación del módulo al valor de la variable de entorno **PSModulePath** .

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Instalación de módulos en el directorio de archivos comunes

Si un módulo se usa en varios componentes de un producto o en varias versiones de un producto, instale el módulo en un subdirectorio específico del módulo del subdirectorio%ProgramFiles%\Archivos Files\Modules.

En el ejemplo siguiente, el módulo Fabrikam se instala en un subdirectorio de Fabrikam del subdirectorio `%ProgramFiles%\Common Files\Modules`. Tenga en cuenta que cada módulo reside en su propio subdirectorio en el subdirectorio modules.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

A continuación, el instalador garantiza el valor de la variable de entorno **PSModulePath** incluye la ruta de acceso del subdirectorio de los módulos de archivos comunes.

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
2. Cree un manifiesto de módulo para cada versión del módulo. En el valor de la clave **ModuleVersion** del manifiesto, escriba el número de versión del módulo. Guarde el archivo de manifiesto (. psd1) en el directorio específico de la versión para el módulo.
3. Agregue la ruta de acceso de la carpeta raíz del módulo al valor de la variable de entorno **PSModulePath** , como se muestra en los ejemplos siguientes.

Para importar una versión determinada del módulo, el usuario final puede usar los parámetros `MinimumVersion` o `RequiredVersion` del cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Por ejemplo, si el módulo Fabrikam está disponible en las versiones 8,0 y 9,0, la estructura de directorios del módulo Fabrikam podría ser similar a la siguiente.

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

El instalador agrega las dos rutas de acceso del módulo al valor de la variable de entorno **PSModulePath** .

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Una vez completados estos pasos, el parámetro **ListAvailable** del cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) obtiene los dos módulos de fabrikam. Para importar un módulo determinado, use los parámetros `MinimumVersion` o `RequiredVersion` del cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Si ambos módulos se importan en la misma sesión y los módulos contienen cmdlets con los mismos nombres, los cmdlets que se importan en último lugar entran en vigor en la sesión.

## <a name="handling-command-name-conflicts"></a>Controlar conflictos de nombres de comando

Pueden producirse conflictos de nombres de comando cuando los comandos que exporta un módulo tienen el mismo nombre que los comandos de la sesión del usuario.

Cuando una sesión contiene dos comandos con el mismo nombre, Windows PowerShell ejecuta el tipo de comando que tiene prioridad. Cuando una sesión contiene dos comandos que tienen el mismo nombre y el mismo tipo, Windows PowerShell ejecuta el comando que se agregó a la sesión más recientemente. Para ejecutar un comando que no se ejecuta de forma predeterminada, los usuarios pueden calificar el nombre del comando con el nombre del módulo.

Por ejemplo, si la sesión contiene una función `Get-Date` y el cmdlet `Get-Date`, Windows PowerShell ejecuta la función de forma predeterminada. Para ejecutar el cmdlet, anteponga al comando el nombre del módulo, por ejemplo:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Para evitar conflictos de nombres, los autores de módulos pueden usar la clave **DefaultCommandPrefix** en el manifiesto del módulo para especificar un prefijo de sustantivo para todos los comandos exportados desde el módulo.

Los usuarios pueden usar el parámetro **prefix** del cmdlet `Import-Module` para utilizar un prefijo alternativo. El valor del parámetro **prefix** tiene prioridad sobre el valor de la clave **DefaultCommandPrefix** .

## <a name="see-also"></a>Véase también

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
