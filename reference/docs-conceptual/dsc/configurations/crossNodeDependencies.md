---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Especificación de dependencias entre nodos
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954112"
---
# <a name="specifying-cross-node-dependencies"></a>Especificación de dependencias entre nodos

> Se aplica a: Windows PowerShell 5.0

DSC proporciona recursos especiales, **WaitForAll**, **WaitForAny** y **WaitForSome**, que se pueden usar en configuraciones para especificar las dependencias en configuraciones de otros nodos. El comportamiento de estos recursos es el siguiente:

- **WaitForAll**: se ejecuta si el recurso especificado está en el estado deseado en todos los nodos de destino definidos en la propiedad **NodeName**.
- **WaitForAny**: se ejecuta si el recurso especificado está en el estado deseado en al menos uno de los nodos de destino definidos en la propiedad **NodeName**.
- **WaitForSome**: especifica una propiedad **NodeCount** además de **NodeName**. El recurso se ejecuta si está en el estado deseado en un número mínimo de nodos (especificado por **NodeCount**) definido por la propiedad **NodeName**.

## <a name="syntax"></a>Sintaxis

Los recursos **WaitForAll** y **WaitForAny** comparten la misma sintaxis. Reemplace \<ResourceType\> en el ejemplo siguiente por **WaitForAny** o **WaitForAll**.
Al igual que la palabra clave **DependsOn**, el nombre debe presentar el formato"[ResourceType]ResourceName". Si el recurso pertenece a otra [configuración](configurations.md), incluya el valor de **ConfigurationName** en la cadena con formato "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]". El **NodeName** es el equipo, o nodo, en el que debe esperar el recurso actual.

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

El recurso **WaitForSome** tiene una sintaxis similar al ejemplo anterior, pero agrega la clave **NodeCount**. **NodeCount** indica cuántos nodos debe esperar el recurso actual.

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

Todos los valores de **WaitForXXXX** comparten las claves de la sintaxis siguiente.

|Propiedad|  Descripción   |
|---------|---------------------|
| RetryIntervalSec| El número de segundos antes de reintentar la operación. El valor mínimo es 1.|
| RetryCount| El número máximo de reintentos.|
| ThrottleLimit| El número de máquinas que se pueden conectar de forma simultánea. El valor predeterminado es `New-CimSession`.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Para obtener más información, vea [DependsOn](resource-depends-on.md)|
| PsDscRunAsCredential | Consulte el artículo sobre el [uso de DSC con credenciales de usuario](./runAsUser.md) |

## <a name="using-waitforxxxx-resources"></a>Uso de recursos WaitForXXXX

Cada recurso **WaitForXXXX** espera a que se completen los recursos especificados en el nodo especificado.
Otros recursos de la misma configuración pueden entonces *depender* del recurso **WaitForXXXX**  usando la clave **DependsOn**.

Por ejemplo, en la configuración siguiente, el nodo de destino está esperando que el recurso **xADDomain** finalice en el nodo **MyDC** con un número máximo de 30 reintentos, a intervalos de 15 segundos, antes de que el nodo de destino pueda unirse al dominio.

De manera predeterminada, los recursos de **WaitForXXX** lo intentan una vez y después se produce un error. Aunque no es necesario, normalmente la intención será especificar un valor para **RetryCount** y otro para **RetryIntervalSec**.

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

Cuando se compila la configuración, se generan dos archivos ".mof". Aplique ambos archivos ".mof" a los nodos de destino mediante el cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)

> [!NOTE]
> Los recursos **WaitForXXX** usan Administración remota de Windows para comprobar el estado de otros nodos.
> Para obtener más información sobre los requisitos de seguridad y puerto de WinRM, vea [Consideraciones de seguridad de comunicación remota de PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="see-also"></a>Véase también

- [Configuraciones DSC](configurations.md)
- [Dependencias de los recursos](resource-depends-on.md)
- [Recursos de DSC](../resources/resources.md)
- [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md)
