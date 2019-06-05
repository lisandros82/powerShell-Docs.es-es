---
ms.date: 01/17/2019
keywords: dsc,powershell,configuration,setup
title: Reinicio de un nodo
ms.openlocfilehash: 106fa1e7b0e3aaf3070ec05548d51140fe9a7725
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470751"
---
# <a name="reboot-a-node"></a>Reinicio de un nodo

> [!NOTE]
> En este tema se trata sobre cómo reiniciar un nodo. Para que el reinicio se realice correctamente, las opciones de LCM **ActionAfterReboot** y **RebootNodeIfNeeded** deben configurarse correctamente.
> Para obtener información acerca de las opciones del administrador de configuración local, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md) o [Configuración del administrador de configuración local (v4)](../managing-nodes/metaConfig4.md).

Se pueden reiniciar los nodos desde dentro de un recurso, mediante el uso de la marca `$global:DSCMachineStatus`. Al establecer esta marca como `1` en la función `Set-TargetResource`, se obliga al LCM a reiniciar el nodo directamente después del método **Set** del recurso actual. Mediante el uso de esta marca, el recurso **xPendingReboot** detecta si está pendiente un reinicio fuera de DSC.

Sus [configuraciones](configurations.md) pueden realizar pasos que requieren que el nodo se reinicie. Esto puede incluir, por ejemplo:

- Actualizaciones de Windows
- Instalación de software
- Cambios de nombre de archivo
- Cambios de nombre de equipo

El recurso **xPendingReboot** comprueba las ubicaciones de equipos específicos para determinar si está pendiente un reinicio. Si el nodo requiere un reinicio fuera de DSC, el recurso **xPendingReboot** establece la marca `$global:DSCMachineStatus` en `1` y obliga a realizar un reinicio y a resolver la condición pendiente.

> [!NOTE]
> Cualquier recurso de DSC puede indicar al LCM que reinicie el nodo estableciendo esta marca en la función `Set-TargetResource`. Para obtener más información, consulte [Escribir un recurso de DSC personalizado con MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Sintaxis

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>Propiedades

| Propiedad | Descripción |
| --- | --- |
| Nombre| Parámetro obligatorio que debe ser único para cada instancia del recurso dentro de una configuración.|
| SkipComponentBasedServicing | Omite los reinicios desencadenados por el componente de servicio basado en componentes. |
| SkipWindowsUpdate | Omite los reinicios desencadenados por Windows Update.|
| SkipPendingFileRename | Omite los reinicios de cambio de nombre de archivo pendientes. |
| SkipCcmClientSDK | Omite los reinicios desencadenados por el cliente de Configuration Manager. |
| SkipComputerRename | Omite los reinicios desencadenados por cambios de nombre de equipo. |
| PSDSCRunAsCredential | Admitido en la versión 5. Ejecuta el recurso como el usuario especificado. |
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. Para obtener más información, vea [Uso de DependsOn](resource-depends-on.md)|

## <a name="example"></a>Ejemplo

El ejemplo siguiente instala Microsoft Exchange con el recurso [xExchange](https://github.com/PowerShell/xExchange).
A lo largo de la instalación, el recurso **xPendingReboot** se usa para reiniciar el nodo.

> [!NOTE]
> Este ejemplo requiere la credencial de una cuenta que tenga derechos para agregar un servidor de Exchange al bosque. Para obtener más información sobre el uso de credenciales en DSC, vea [Control de credenciales en DSC](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> En este ejemplo se asume que se ha configurado el administrador de configuración local para permitir reinicios y continuar la configuración tras un reinicio.

## <a name="where-to-download"></a>Dónde puede realizarse la descarga

Puede descargar los recursos usados en este tema en las siguientes ubicaciones, o mediante el uso de la Galería de PowerShell.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
