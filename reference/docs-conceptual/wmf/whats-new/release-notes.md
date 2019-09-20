---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Notas de la versión WMF 5.0
ms.openlocfilehash: 8924240a4bbedcd34bc68b7cacdd23189a3716d6
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147585"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Notas de la versión de Windows Management Framework (WMF) 5.x

## <a name="wmf-50-changes"></a>Cambios en WMF 5.0

- PowerShell 5.0 agrega un nuevo flujo de **información** estructurado
- Mejoras en DSC, incluidos cuatro recursos de DSC nuevos:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Se agregó Just Enough Administration para habilitar la administración basada en roles a través de la comunicación remota de PowerShell
- PowerShell 5.0 extiende el lenguaje para incluir enumeraciones y clases definidas por el usuario
- Se mejoraron las características de depuración de PowerShell ISE y se agregó la depuración remota
- Se agregaron los módulos PowerShellGet y PackageManagement
- Se mejoraron las transcripciones y el registro de scripts de PowerShell
- Se agregaron cmdlets de sintaxis de mensajes de cifrado
- WMF 5.0 incluye el módulo NetworkSwitchManager para Windows
- Se agregó el módulo Microsoft.PowerShell.ODataUtils
- Se agregó compatibilidad con el Registro de inventario de software (SIL)
- Varios cmdlets nuevos o actualizados en respuesta a problemas y solicitudes de usuarios

## <a name="wmf-51-changes"></a>Cambios en WMF 5.1

WMF 5.1 incluye los componentes de PowerShell, WMI, WinRM y Registro de inventario de software (SIL) que se lanzaron con Windows Server 2016. WMF 5.1 puede instalarse en Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 y 2012 R2 y proporciona varias mejoras con respecto a WMF 5.0 RTM, incluidos:

- Nuevos cmdlets
- En las mejoras de PowerShellGet se incluyen la aplicación de módulos firmados y la instalación de módulos JEA
- PackageManagement ha agregado compatibilidad con contenedores, configuración de CBS, configuración basada en EXE y paquetes de CAB
- Mejoras de depuración para las clases DSC y PowerShell
- Mejoras de seguridad, incluido el cumplimiento de módulos firmados por catálogos procedentes del servidor de extracción y al usar cmdlets de PowerShellGet
- Respuestas a varios problemas y varias solicitudes de usuarios

> [!IMPORTANT]
> Antes de instalar WMF 5.1 en Windows Server 2008 o Windows 7, confirme que WMF 3.0 no está instalado. Para obtener más información, consulte [Requisitos previos de WMF 5.1 para Windows Server 2008 R2 SP1 y Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).

## <a name="powershell-editions"></a>Ediciones de PowerShell

A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.

- **Desktop Edition:** basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y Windows Desktop.
- **Core Edition:** basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Nano Server y Windows IoT.

### <a name="learn-more-about-using-powershell-editions"></a>Más información acerca de las ediciones de PowerShell

- [Determinación de la edición de ejecución de PowerShell con $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrado de los resultados de Get-Module mediante CompatiblePSEditions con el parámetro PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Impedir la ejecución de scripts, a menos que se ejecuten en una edición compatible de PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Declarar la compatibilidad de un módulo con versiones específicas de PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Caché de análisis de módulo

A partir de WMF 5.1, PowerShell proporciona control sobre el archivo que se utiliza para almacenar en la caché los datos acerca de un módulo, como los comandos que exporta.

De manera predeterminada, esta caché se almacena en el archivo `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. La caché normalmente se lee en el inicio al buscar un comando y se escribe en un subproceso en segundo plano después de que se importa un módulo.

Para cambiar la ubicación predeterminada de la memoria caché, establezca la variable de entorno `$env:PSModuleAnalysisCachePath` antes de iniciar PowerShell. Los cambios en esta variable de entorno solo afectarán a los procesos secundarios. El valor debe asignar un nombre a una ruta de acceso completa (nombre de archivo incluido) en la que PowerShell tiene permiso para crear y escribir archivos. Para deshabilitar la caché del archivo, establezca este valor en una ubicación no válida, como por ejemplo:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Esto establece la ruta de acceso en un dispositivo no válido. Si PowerShell no puede escribir en la ruta de acceso, no se devuelve ningún error, pero se pueden ver informes del error a través de un seguimiento:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Al escribir en la caché, PowerShell buscará si hay módulos que no existen, con el fin de evitar que la caché sea demasiado grande. A veces no interesa que se realicen estas comprobaciones, en cuyo caso se pueden desactivar estableciendo:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

El establecimiento de esta variable de entorno surtirá efecto de inmediato en el proceso actual.

## <a name="specifying-module-version"></a>Especificación de la versión del módulo

En WMF 5.1, `using module` se comporta de la misma forma que las restantes construcciones relacionadas con módulos de PowerShell.
Antes no había forma de especificar una versión concreta del módulo; si había varias versiones, aparecía un error.

En WMF 5.1:

- Puede usar el [constructor ModuleSpecification (tabla hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

  Esta tabla hash tiene el mismo formato que `Get-Module -FullyQualifiedName`.

  **Ejemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Si hay varias versiones del módulo de multiplicar, PowerShell usa la **misma lógica de resolución** que `Import-Module` y no devuelve ningún error (el mismo comportamiento que `Import-Module` y `Import-DscResource`).

## <a name="improvements-to-pester"></a>Mejoras en Pester

En WMF 5.1, la versión de Pester que se incluye con PowerShell se actualizó de 3.3.5 a 3.4.0.
Esta actualización permite un mejor comportamiento para Pester en Nano Server.

Para revisar los cambios en Pest, inspeccione el [registro de cambios](https://github.com/pester/Pester/blob/master/CHANGELOG.md) del repositorio de GitHub.
