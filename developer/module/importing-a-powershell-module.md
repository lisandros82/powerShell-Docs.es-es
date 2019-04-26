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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082256"
---
# <a name="importing-a-powershell-module"></a>Importación de un módulo de PowerShell

Una vez que la ha instalado un módulo en un sistema, es probable que desee importar el módulo. Importar es el proceso que carga el módulo en la memoria activa, para que un usuario puede tener acceso a ese módulo en su sesión de PowerShell. En PowerShell 2.0, puede importar un módulo de PowerShell recién instalado con una llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet. En PowerShell 3.0, es capaz implícitamente importar un módulo cuando se llama por el usuario a una de las funciones o los cmdlets del módulo de PowerShell. Tenga en cuenta que ambas versiones se suponen que instalar el módulo en una ubicación donde PowerShell es capaz de encontrar Para obtener más información, consulte [instalar un módulo de PowerShell](./installing-a-powershell-module.md). Puede usar un manifiesto de módulo para restringir qué partes del módulo se exportan y se puede usar parámetros de la `Import-Module` llamadas para restringir qué partes se importan.

## <a name="importing-a-snap-in-powershell-10"></a>Importación de un complemento (PowerShell 1.0)

Los módulos no existía en PowerShell 1.0: en su lugar, debía registrar y usar complementos. Sin embargo, no se recomienda que utilice esta tecnología en este momento, como son generalmente más fáciles de instalar e importar módulos. Para obtener más información, consulte [cómo crear un Windows PowerShell Snap-in](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importar un módulo con Import-Module (PowerShell 2.0)

PowerShell 2.0 usa apropiadamente denominado [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) para importar módulos. Cuando se ejecuta este cmdlet, Windows PowerShell busca en el módulo especificado dentro de los directorios especificados en el `PSModulePath` variable. Cuando se encuentra el directorio especificado, Windows PowerShell para buscar archivos en el siguiente orden: archivos de manifiesto de módulo (. psd1), los archivos de módulo (. psm1), archivos de módulo binario (.dll) de script. Para obtener más información sobre cómo agregar directorios a la búsqueda, consulte [modificar la ruta de instalación PSModulePath](./modifying-the-psmodulepath-installation-path.md). El código siguiente describe cómo importar un módulo:

```powershell
Import-Module myModule
```

Suponiendo que myModule se encontraba en el `PSModulePath`, PowerShell cargaría myModule en la memoria activa. Si no se encuentra myModule en un `PSModulePath` ruta de acceso, se podría seguir indicar explícitamente a PowerShell dónde encontrarla:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

También puede usar el parámetro - verbose para identificar lo que se va a exportar fuera del módulo y lo que se va a importar en la memoria activa. Las exportaciones e importaciones restringen lo que se expone al usuario: la diferencia es que controla la visibilidad. Básicamente, las exportaciones se controlan mediante código dentro del módulo. En cambio, las importaciones se controlan mediante el `Import-Module` llamar. Para obtener más información, consulte **restringir los miembros que se importan**, a continuación.

## <a name="implicitly-importing-a-module-powershell-30"></a>Importación de forma implícita un módulo (PowerShell 3.0)

A partir de Windows PowerShell 3.0, los módulos se importan automáticamente cuando se usa cualquier cmdlet o función en el módulo en un comando. Esta característica funciona en cualquier módulo en un directorio incluido en el valor de la **PSModulePath** variable de entorno. Si no guarda el módulo en una ruta de acceso válida sin embargo, todavía puede cargar mediante la configuración explícita [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) opción, se ha descrito anteriormente.

Las siguientes acciones desencadenan la importación automática de un módulo, también conocido como "módulo carga automática".

- Usar un cmdlet en un comando. Por ejemplo, si escribe `Get-ExecutionPolicy` importa el módulo Microsoft.PowerShell.Security que contiene el `Get-ExecutionPolicy` cmdlet.

- Mediante el [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) para obtener el comando.  Por ejemplo, si escribe `Get-Command Get-JobTrigger` importa el **PSScheduledJob** módulo que contiene el `Get-JobTrigger` cmdlet. Un `Get-Command` comando que incluye caracteres comodín se considera que es la detección y desencadenar la importación de un módulo.

- Mediante el [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) para obtener ayuda para un cmdlet. Por ejemplo, si escribe `Get-Help Get-WinEvent` importa el módulo Microsoft.PowerShell.Diagnostics que contiene el `Get-WinEvent` cmdlet.

Para admitir la importación automática de módulos, el `Get-Command` cmdlet Obtiene todos los cmdlets y funciones en todos los módulos instalados, incluso si no se importa el módulo en la sesión. Para obtener más información, vea el tema de ayuda para la [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet.

## <a name="the-importing-process"></a>El proceso de importación

Cuando se importa un módulo, se crea un estado de sesión nuevo para el módulo y un [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) se crea el objeto en memoria. Un estado de sesión se crea para cada módulo importado (Esto incluye el módulo raíz y los módulos anidados). Los miembros que se exportan desde el módulo raíz, incluidos a los miembros que se exportaron al módulo raíz por los módulos anidados, a continuación, se importan en el estado de sesión del llamador.

Los metadatos de los miembros que se exportan desde un módulo tiene una propiedad ModuleName. Esta propiedad se rellena con el nombre del módulo que exporta a ellos.

> [!WARNING]
> Si el nombre de un miembro exportado usa un verbo no aprobado o si el nombre del miembro utiliza caracteres restringidos, se muestra una advertencia cuando el [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet se ejecuta.

De forma predeterminada, el [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet no devuelve ningún objeto a la canalización. Sin embargo, el cmdlet admite una `PassThru` parámetro que puede usarse para devolver un [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) objeto para cada módulo que se importa. Para enviar el resultado al host, los usuarios deben ejecutar la [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet.

## <a name="restricting--the-members-that-are-imported"></a>Restringir a los miembros que se importan

Cuando se importa un módulo mediante el uso de la [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet, de forma predeterminada, todos los módulos exportados miembros se importan en la sesión, incluidos los comandos exportan al módulo mediante un módulo anidado. De forma predeterminada, no se exportan las variables y alias. Para restringir los miembros que se exportan, use un [manifiesto del módulo](./how-to-write-a-powershell-module-manifest.md). Para restringir los miembros que se importan, use los siguientes parámetros de la `Import-Module` cmdlet.

- `Function`: Este parámetro limita las funciones que se exportan. (Si usa un manifiesto de módulo, consulte la clave FunctionsToExport).

- `Cmdlet`: Este parámetro limita los cmdlets que se exportan (si está usando un manifiesto, vea módulo la clave CmdletsToExport.)

- `Variable`: Este parámetro limita las variables que se exportan (si está usando un manifiesto, vea módulo la clave VariablesToExport.)

- `Alias`: Este parámetro limita los alias que se exportan (si está usando un manifiesto, vea módulo la clave AliasesToExport.)

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
