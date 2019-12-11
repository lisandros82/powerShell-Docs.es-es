---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Uso de las credenciales con recursos de DSC
ms.openlocfilehash: fea2e3cad8d081c17853e127203f1d40d98c5de2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953982"
---
# <a name="use-credentials-with-dsc-resources"></a>Uso de las credenciales con recursos de DSC

> Se aplica a: Windows PowerShell 5.0, Windows PowerShell 5.1

Puede ejecutar un recurso de DSC en un conjunto de credenciales especificado mediante la propiedad **PsDscRunAsCredential** automática de la configuración. De forma predeterminada, DSC ejecuta cada recurso como la cuenta del sistema. A veces, es necesaria la ejecución como usuario, por ejemplo, al instalar paquetes MSI en un contexto de usuario específico, al configurar claves de registro de un usuario, al acceder a un directorio local específico de usuario o al acceder a un recurso compartido de red. La máquina de destino necesita la propiedad **SeInteractiveLogonRight** para cualquier cuenta que especifique en **PSDSCRunAsCredential**. Para obtener más información, consulte [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants) (Constantes de derechos de cuentas).

Cada recurso de DSC tiene una propiedad **PsDscRunAsCredential** que se puede establecer en cualquier credencial de usuario (un objeto [PSCredential](/dotnet/api/system.management.automation.pscredential)). La credencial puede codificarse de forma rígida como el valor de la propiedad de la configuración, o bien puede establecer el valor en [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), que solicitará al usuario una credencial cuando se compile la configuración (para más información sobre la compilación de configuraciones, vea [Configuraciones](configurations.md)).

> [!NOTE]
> En PowerShell 5.0, no se admite el uso de la propiedad **PsDscRunAsCredential** en configuraciones que llaman a recursos compuestos. En PowerShell 5.1, la propiedad **PsDscRunAsCredential** es compatible con configuraciones que llaman a recursos compuestos. La propiedad **PsDscRunAsCredential** no está disponible en PowerShell 4.0.

En el ejemplo siguiente, `Get-Credential` se usa para solicitar credenciales al usuario. El recurso **Registry** se usa para cambiar la clave del Registro que especifica el color de fondo de la ventana del símbolo del sistema de Windows.

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```

> [!NOTE]
> En este ejemplo se supone que tiene un certificado válido en `C:\publicKeys\targetNode.cer` y que la huella digital del certificado es el valor mostrado. Para obtener más información sobre el cifrado de credenciales en archivos MOF de configuración de DSC, vea [Proteger el archivo MOF](../pull-server/secureMOF.md).
