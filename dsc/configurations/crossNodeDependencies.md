---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Especificación de dependencias entre nodos
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402201"
---
# <a name="specifying-cross-node-dependencies"></a>Especificación de dependencias entre nodos

> Se aplica a: Windows PowerShell 5.0

DSC proporciona recursos especiales, **WaitForAll**, **WaitForAny** y **WaitForSome**, que se pueden usar en configuraciones para especificar las dependencias en configuraciones de otros nodos. El comportamiento de estos recursos es el siguiente:

- **WaitForAll**: Se realiza correctamente si el recurso especificado está en el estado deseado en todos los nodos de destino definidos en el **NodeName** propiedad.
- **WaitForAny**: Se realiza correctamente si el recurso especificado está en el estado deseado en al menos uno de los nodos de destino definido en el **NodeName** propiedad.
- **WaitForSome**: Especifica un **NodeCount** propiedad además un **NodeName** propiedad. El recurso se ejecuta si está en el estado deseado en un número mínimo de nodos (especificado por **NodeCount**) definido por la propiedad **NodeName**.

## <a name="syntax"></a>Sintaxis

El **WaitForAll** y **WaitForAny** recursos comparten la misma sintaxis. Reemplace \<ResourceType\> en el ejemplo siguiente con cualquiera **WaitForAny** o **WaitForAll**.
Al igual que el **DependsOn** palabra clave, tendrá que dar formato al nombre como "[ResourceType] ResourceName". Si el recurso pertenece a otro [configuración](configurations.md), incluya el **ConfigurationName** en la cadena con formato "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]". El **NodeName** es el equipo, o nodo, en el que debe esperar el recurso actual.

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

El **WaitForSome** recurso tiene una sintaxis similar al ejemplo anterior, pero agrega la **NodeCount** clave. El **NodeCount** indica cuántos nodos debe esperar el recurso actual.

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

Todos los **WaitForXXXX** compartir las claves de la sintaxis siguiente.

|  Propiedad |  Descripción || RetryIntervalSec | El número de segundos antes de Reintentar. Valor mínimo es 1. | | RetryCount | El número máximo de reintentos. | | ThrottleLimit | Número de equipos se conecten simultáneamente. El valor predeterminado es `New-CimSession` predeterminada. | | DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de configura este recurso. Para obtener más información, consulte [DependsOn](resource-depends-on.md)|| PsDscRunAsCredential | Consulte [mediante DSC con credenciales de usuario](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>Uso de recursos WaitForXXXX

Cada **WaitForXXXX** esperas de recursos para que los recursos especificados completar en el nodo especificado. Otros recursos en la misma configuración pueden, a continuación, *dependen* el **WaitForXXXX** recursos mediante el **DependsOn** clave.

Por ejemplo, en la configuración siguiente, el nodo de destino está esperando que el recurso **xADDomain** finalice en el nodo **MyDC** con un número máximo de 30 reintentos, a intervalos de 15 segundos, antes de que el nodo de destino pueda unirse al dominio.

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

Cuando se compila la configuración, se generan dos archivos de "MOF". Ambos archivos "MOF" se aplican a los nodos de destino mediante el [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet

>**Nota:** De forma predeterminada el waitforxxx lo recursos intentan una vez y, a continuación, se producirá un error. Aunque no es necesario, normalmente querrá especificar un **RetryCount** y **RetryIntervalSec**.

## <a name="see-also"></a>Véase también

- [Configuraciones DSC](configurations.md)
- [Usar dependencias de recursos](resource-depends-on.md)
- [Recursos de DSC](../resources/resources.md)
- [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md)
