---
ms.date: 1/17/2019
keywords: dsc,powershell,configuration,setup
title: Reiniciar un nodo
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680745"
---
# <a name="reboot-a-node"></a>Reiniciar un nodo

> [!NOTE]
> En este tema trata sobre cómo reiniciar un nodo. En orden para el reinicio se realice correctamente la **ActionAfterReboot** y **RebootNodeIfNeeded** configuración del LCM debe configurarse correctamente.
> Para obtener información acerca de la configuración del Administrador de configuración Local, consulte [configurar el Administrador de configuración Local](../managing-nodes/metaConfig.md), o [configurar el Administrador de configuración Local (v4)](../managing-nodes/metaConfig4.md).

Se pueden reiniciar los nodos desde dentro de un recurso, mediante el uso de la `$global:DSCMachineStatus` marca. Al establecer esta marca en `1` en el `Set-TargetResource` función fuerza el LCM para reiniciar el nodo directamente después de la **establecer** método del recurso actual. Usar esta marca, el **xPendingReboot** recursos detecta si está pendiente un reinicio fuera de DSC.

Su [configuraciones](configurations.md) es posible que lleve a cabo los pasos que requieren el nodo se reinicie. Esto puede incluir cosas como:

- Windows: Actualizaciones
- Instalación del software
- Cambia el nombre de archivo
- Cambio de nombre de equipo

El **xPendingReboot** recursos comprueba las ubicaciones de equipo específico para determinar si está pendiente un reinicio. Si el nodo requiere un reinicio fuera de DSC, el **xPendingReboot** conjuntos de recursos el `$global:DSCMachineStatus` marca `1` forzar un reinicio y resolver la condición pendiente.

> [!NOTE]
> Cualquier recurso de DSC puede indicar que el LCM para reiniciar el nodo al establecer esta marca el `Set-TargetResource` función. Para obtener más información, consulte [escribir un recurso de DSC personalizado con MOF](../resources/authoringResourceMOF.md).

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
| SkipComponentBasedServicing | Reinicios de Skip desencadenados por el componente de servicio basado en componentes. |
| SkipWindowsUpdate | Reinicios de Skip desencadenados por Windows Update.|
| SkipPendingFileRename | Omitir los reinicios de cambio de nombre de archivo pendiente. |
| SkipCcmClientSDK | Reinicios de Skip desencadenados por el cliente de Configuration Manager. |
| SkipComputerRename | Omitir reinicia desencadenada por cambios de nombre de equipo. |
| PSDSCRunAsCredential | Se admiten en v5. El recurso se ejecuta como el usuario especificado. |
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. Para obtener más información, consulte [utilizando DependsOn](resource-depends-on.md)|

## <a name="example"></a>Ejemplo

El ejemplo siguiente, instala con Microsoft Exchange el [xExchange](https://github.com/PowerShell/xExchange) recursos.
A lo largo de la instalación, el **xPendingReboot** recurso se usa para reiniciar el nodo.

> [!NOTE]
> Este ejemplo requiere la credencial de una cuenta que tenga derechos para agregar un servidor de Exchange en el bosque. Para obtener más información sobre el uso de credenciales en DSC, consulte [control de credenciales en DSC](../configurations/configDataCredentials.md)

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
> En este ejemplo se da por supuesto que ha configurado el Administrador de configuración Local para permitir los reinicios y continuar con la configuración tras un reinicio.

## <a name="where-to-download"></a>Ubicación donde debe descargarse

Puede descargar los recursos usados en este tema en las siguientes ubicaciones, o mediante el uso de la Galería de PowerShell.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
