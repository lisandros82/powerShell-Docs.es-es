---
ms.date: 08/15/2019
keywords: dsc,powershell,configuration,setup
title: Introducción a la configuración de estado deseado (DSC) para Windows
ms.openlocfilehash: a4f9db481afda65fc4ac5e553230dbba3037ac9a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954412"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>Introducción a la configuración de estado deseado (DSC) para Windows

En este tema se ofrece una introducción al uso de la configuración de estado deseado (DSC) de PowerShell para Windows.
Para obtener información general sobre DSC, consulte [Introducción a la configuración de estado deseado de Windows PowerShell](../overview/overview.md).

## <a name="supported-windows-operation-system-versions"></a>Versiones de sistemas operativos Windows compatibles

Las versiones compatibles son las siguientes:

- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- Windows 10
- Windows 8.1
- Windows 7

La referencia de almacén del producto independiente de [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) no contiene una implementación de la configuración de estado deseado, por lo que ni DSC de PowerShell ni la configuración de estado de Azure Automation pueden administrarla.

## <a name="installing-dsc"></a>Instalación de DSC

La configuración de estado deseado de PowerShell se incluye en Windows y se actualiza a través de Windows Management Framework.
La versión más reciente es [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).

> [!NOTE]
> No es necesario habilitar la característica de Windows Server "DSC-Service" para administrar una máquina mediante DSC.
> Esta característica solo es necesaria al crear una instancia de servidor de extracción de Windows.

## <a name="using-dsc-for-windows"></a>Uso de DSC para Windows

En las siguientes secciones se explica cómo crear y ejecutar configuraciones DSC en equipos Windows.

### <a name="creating-a-configuration-mof-document"></a>Creación de un documento MOF de configuración

Se utiliza la palabra clave de Windows PowerShell Configuration a fin de crear una configuración.
En los pasos siguientes se describe la creación de un documento de configuración con Windows PowerShell.

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>Defina una configuración y genere el documento de configuración:

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a>Instalación de un módulo con recursos de DSC

La configuración de estado deseado de Windows PowerShell incluye módulos integrados con recursos de DSC.
También puede cargar módulos desde orígenes externos como la Galería de PowerShell, mediante los cmdlet PowerShellGet.

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a>Aplicación de la configuración a la máquina

Los documentos de configuración (archivos MOF) se pueden aplicar a la máquina mediante el cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a>Obtención del estado actual de la configuración

El cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) consulta el estado actual de la máquina y devuelve los valores actuales de la configuración.

`Get-DscConfiguration`

El cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) devuelve la metaconfiguración actual aplicada a la máquina.

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a>Eliminación de la configuración actual de una máquina

[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a>Definición de configuración en el Administrador de configuración local

Aplique un archivo MOF de metaconfiguración a la máquina mediante el cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager).
Requiere la ruta de acceso al MOF de metaconfiguración.

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Archivos de registro de configuración de estado deseado de Windows PowerShell

Los registros para DSC se escriben en el registro de eventos de Windows en la ruta de acceso `Microsoft-Windows-Dsc/Operational`.
Se pueden habilitar registros adicionales con fines de depuración siguiendo los pasos en [¿Dónde se encuentran los registros de eventos de DSC?](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs)
