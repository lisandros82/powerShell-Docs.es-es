---
title: Importar un módulo de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360704"
---
# <a name="importing-a-powershell-module"></a>Importación de un módulo de PowerShell

Una vez que haya instalado un módulo en un sistema, es probable que desee importar el módulo. La importación es el proceso que carga el módulo en la memoria activa, para que un usuario pueda acceder a ese módulo en su sesión de PowerShell. En PowerShell 2,0, puede importar un módulo de PowerShell recién instalado con una llamada al cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) . En PowerShell 3,0, PowerShell puede importar implícitamente un módulo cuando un usuario llama a una de las funciones o cmdlets del módulo. Tenga en cuenta que ambas versiones suponen que instala el módulo en una ubicación donde PowerShell puede encontrarlo; para obtener más información, vea [instalar un módulo de PowerShell](./installing-a-powershell-module.md). Puede usar un manifiesto de módulo para restringir qué partes del módulo se exportan y puede usar los parámetros de la llamada `Import-Module` para restringir qué partes se importan.

## <a name="importing-a-snap-in-powershell-10"></a>Importar un complemento (PowerShell 1,0)

Los módulos no existían en PowerShell 1,0: en su lugar, tenía que registrar y usar complementos. Sin embargo, no se recomienda usar esta tecnología en este momento, ya que los módulos suelen ser más fáciles de instalar e importar. Para obtener más información, vea [Cómo crear un complemento de Windows PowerShell](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importar un módulo con Import-Module (PowerShell 2,0)

PowerShell 2,0 usa el cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) con el nombre adecuado para importar módulos. Cuando se ejecuta este cmdlet, Windows PowerShell busca el módulo especificado en los directorios especificados en la variable `PSModulePath`. Cuando se encuentra el directorio especificado, Windows PowerShell busca archivos en el siguiente orden: archivos de manifiesto de módulo (. psd1), archivos de módulo de script (. psm1), archivos de módulo binario (. dll). Para obtener más información sobre cómo agregar directorios a la búsqueda, consulte [modificar la ruta de instalación de PSModulePath](./modifying-the-psmodulepath-installation-path.md). En el código siguiente se describe cómo importar un módulo:

```powershell
Import-Module myModule
```

Suponiendo que MyModule se encuentre en el `PSModulePath`, PowerShell cargaría MyModule en la memoria activa. Si no se encuentra MyModule en una ruta de acceso `PSModulePath`, puede indicar explícitamente a PowerShell dónde encontrarlo:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

También puede usar el parámetro-verbose para identificar lo que se va a exportar fuera del módulo y lo que se va a importar en la memoria activa. Las exportaciones y las importaciones restringen lo que se expone al usuario: la diferencia es quién controla la visibilidad. Esencialmente, las exportaciones se controlan mediante código dentro del módulo. Por el contrario, la llamada `Import-Module` controla las importaciones. Para obtener más información, vea **restringir los miembros que se importan**a continuación.

## <a name="implicitly-importing-a-module-powershell-30"></a>Importación implícita de un módulo (PowerShell 3,0)

A partir de Windows PowerShell 3,0, los módulos se importan automáticamente cuando cualquier cmdlet o función del módulo se usa en un comando. Esta característica funciona en cualquier módulo de un directorio que se incluye en el valor de la variable de entorno **PSModulePath** . Sin embargo, si no guarda el módulo en una ruta de acceso válida, todavía puede cargarlo mediante la opción [de Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) explícita, descrita anteriormente.

Las siguientes acciones desencadenan la importación automática de un módulo, también conocido como "carga automática de módulos".

- Usar un cmdlet en un comando. Por ejemplo, al escribir `Get-ExecutionPolicy` se importa el módulo Microsoft. PowerShell. Security que contiene el cmdlet `Get-ExecutionPolicy`.

- Usar el cmdlet [get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) para obtener el comando.  Por ejemplo, al escribir `Get-Command Get-JobTrigger` se importa el módulo **PSScheduledJob** que contiene el cmdlet @no__t 2. Un comando `Get-Command` que incluye caracteres comodín se considera detección y no desencadena la importación de un módulo.

- Use el cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) para obtener ayuda para un cmdlet. Por ejemplo, al escribir `Get-Help Get-WinEvent` se importa el módulo Microsoft. PowerShell. Diagnostics que contiene el cmdlet `Get-WinEvent`.

Para admitir la importación automática de módulos, el cmdlet `Get-Command` obtiene todos los cmdlets y las funciones de todos los módulos instalados, incluso si el módulo no se importa en la sesión. Para obtener más información, vea el tema de ayuda para el cmdlet [get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) .

## <a name="the-importing-process"></a>El proceso de importación

Cuando se importa un módulo, se crea un nuevo estado de sesión para el módulo y se crea un objeto [System. Management. Automation. PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) en la memoria. Se crea un estado de sesión para cada módulo que se importa (esto incluye el módulo raíz y los módulos anidados). Los miembros que se exportan desde el módulo raíz, incluidos los miembros que se exportaron al módulo raíz mediante cualquier módulo anidado, se importan después en el estado de sesión del llamador.

Los metadatos de los miembros que se exportan desde un módulo tienen una propiedad ModuleName. Esta propiedad se rellena con el nombre del módulo que los exportó.

> [!WARNING]
> Si el nombre de un miembro exportado usa un verbo no aprobado o si el nombre del miembro usa caracteres restringidos, se muestra una advertencia cuando se ejecuta el cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

De forma predeterminada, el cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) no devuelve ningún objeto a la canalización. Sin embargo, el cmdlet admite un parámetro `PassThru` que se puede usar para devolver un objeto [System. Management. Automation. PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) para cada módulo que se importa. Para enviar la salida al host, los usuarios deben ejecutar el cmdlet [write-host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) .

## <a name="restricting--the-members-that-are-imported"></a>Restringir los miembros que se importan

Cuando se importa un módulo mediante el cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) , de forma predeterminada, todos los miembros de módulo exportados se importan en la sesión, incluidos los comandos exportados al módulo por un módulo anidado. De forma predeterminada, las variables y los alias no se exportan. Para restringir los miembros que se exportan, use un [manifiesto del módulo](./how-to-write-a-powershell-module-manifest.md). Para restringir los miembros que se importan, use los parámetros siguientes del cmdlet `Import-Module`.

- `Function`: este parámetro restringe las funciones que se exportan. (Si usa un manifiesto de módulo, consulte la clave FunctionsToExport).

- `Cmdlet`: este parámetro restringe los cmdlets que se exportan (si usa un manifiesto de módulo, consulte la clave CmdletsToExport).

- `Variable`: este parámetro restringe las variables que se exportan (si usa un manifiesto de módulo, consulte la clave VariablesToExport).

- `Alias`: este parámetro restringe los alias que se exportan (si usa un manifiesto de módulo, consulte la clave AliasesToExport).

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
