---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Uso de DSC on Nano Server
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402562"
---
# <a name="using-dsc-on-nano-server"></a>Uso de DSC on Nano Server

> Se aplica a: Windows PowerShell 5.0

**DSC on Nano Server** es un paquete opcional de la carpeta `NanoServer\Packages` de los medios de Windows Server 2016. Se puede instalar el paquete cuando se crea un VHD para un Nano Server mediante la especificación de **Microsoft-NanoServer-DSC-Package** como valor del parámetro **Packages** de la función **New-NanoServerImage**. Por ejemplo, si está creando un VHD para una máquina virtual, el comando sería similar al siguiente:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Para obtener más información sobre cómo instalar y usar Nano Server, y también cómo administrar Nano Server con comunicación remota de PowerShell, vea [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server) (Introducción a Nano Server).

## <a name="dsc-features-available-on-nano-server"></a>Características de DSC disponibles en Nano Server

Dado que Nano Server solo admite un conjunto limitado de API en comparación con una versión completa de Windows Server; por el momento, DSC on Nano Server no tiene paridad completa funcional con DSC cuando se ejecuta en SKU completas. DSC on Nano Server está en desarrollo activo y todavía no es una característica completa.

Las siguientes características de DSC están disponibles actualmente en Nano Server:

Modos de inserción y extracción

- Todos los cmdlets de DSC que existen en una versión completa de Windows Server, incluidos los siguientes:
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- Compilación de configuraciones (vea [Configuraciones DSC](../configurations/configurations.md))

  **Issue #1629** Cifrado de contraseña (consulte [proteger el archivo MOF](../pull-server/secureMOF.md)) durante la configuración de compilación no funciona.

- Compilación de metaconfiguraciones (vea [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md))

- Ejecutar un recurso en el contexto de usuario (vea [DSC de ejecución con las credenciales de usuario (RunAs)](../configurations/runAsUser.md))

- Recursos basados en clases (vea [Escribir un recurso de DSC personalizado con clases de PowerShell](../resources/authoringResourceClass.md))

- Depuración de recursos de DSC (vea [Depuración de recursos de DSC](../troubleshooting/debugResource.md))

  **Issue #1629** No funciona si un recurso usa PsDscRunAsCredential (vea [DSC ejecutando con credenciales de usuario](../configurations/runAsUser.md))

- [Especificación de las dependencias entre nodos](../configurations/crossNodeDependencies.md)

- [Control de versiones de recursos](../configurations/sxsResource.md)

- Cliente de extracción (configuraciones y recursos) (vea [Configuración de un cliente de extracción mediante nombres de configuración](../pull-server/pullClientConfigNames.md))

- [Configuraciones parciales (extracción e incorporación de cambios)](../pull-server/partialConfigs.md)

- [Generación de informes en el servidor de extracción](../pull-server/reportServer.md)

- Cifrado de MOF

- Registro de eventos

- Informes de DSC de automatización de Azure

- Recursos que son totalmente funcionales

- **Archive**
- **Environment**
- **File**
- **Log**
- **ProcessSet**
- **Registry**
- **Script**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll** (vea [Especificación de dependencias entre nodos](../configurations/crossNodeDependencies.md))
- **WaitForAny** (vea [Especificación de dependencias entre nodos](../configurations/crossNodeDependencies.md))
- **WaitForSome** (vea [Especificación de dependencias entre nodos](../configurations/crossNodeDependencies.md))

- Recursos que son parcialmente funcionales
- **Grupo**
- **GroupSet**

  **Issue #1629** Los recursos anteriores producirá un error si se llama dos veces a una instancia específica (que se ejecuta dos veces la misma configuración)

- **Service**
- **ServiceSet**

  **Issue #1629** Solo funciona para iniciar y detener el servicio (estado). Produce un error si intenta cambiar otros atributos del servicio, como startuptype, credenciales, descripción, etc. El error que se produce es similar a:

  *No se puede encontrar el tipo [management.managementobject]. Compruebe que está cargado el ensamblado que lo contiene.*

- Recursos que no son funcionales
- **Usuario**

## <a name="dsc-features-not-available-on-nano-server"></a>Características de DSC no disponibles en Nano Server

Las siguientes características de DSC no están disponibles actualmente en Nano Server:

- Descifrar el documento MOF con contraseñas cifradas
- Servidor de extracción: actualmente no se puede establecer un servidor de extracción en Nano Server
- Todo lo que no está en la lista de trabajos funciona

## <a name="using-custom-dsc-resources-on-nano-server"></a>Uso de recursos personalizados de DSC en Nano Server

Debido a un conjunto limitado de bibliotecas CLR y API de Windows disponibles en Nano Server, los recursos de DSC que funcionan en la versión CLR completa de Windows no funcionan necesariamente en Nano Server.
Pruebas de un extremo a otro antes de implementar los recursos personalizados de DSC en un entorno de producción.

## <a name="see-also"></a>Véase también

- [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server) (Introducción a Nano Server)
