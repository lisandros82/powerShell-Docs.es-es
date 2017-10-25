---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC de ejecución con las credenciales de usuario"
ms.openlocfilehash: f15b2e4bfb888e2f3646a33cc0191e33a7ebb8ab
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="running-dsc-with-user-credentials"></a>DSC de ejecución con las credenciales de usuario 

> Se aplica a: Windows PowerShell 5.0, Windows PowerShell 5.1

Puede ejecutar un recurso de DSC en un conjunto de credenciales especificado mediante la propiedad **PsDscRunAsCredential** automática de la configuración. De forma predeterminada, DSC ejecuta cada recurso como la cuenta del sistema.
A veces, es necesaria la ejecución como usuario, por ejemplo, al instalar paquetes MSI en un contexto de usuario específico, al configurar claves de registro de un usuario, al acceder a un directorio local específico de usuario o al acceder a un recurso compartido de red.

Cada recurso de DSC tiene una propiedad **PsDscRunAsCredential** que se puede establecer en cualquier credencial de usuario (un objeto [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx)).
La credencial puede codificarse de forma rígida como el valor de la propiedad de la configuración, o bien puede establecer el valor en [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx), que solicitará al usuario una credencial cuando se compile la configuración (para más información sobre la compilación de configuraciones, vea [Configuraciones](configurations.md)).

>**Nota:** En PowerShell 5.0, no se admite el uso de la propiedad **PsDscRunAsCredential** en configuraciones que llaman a recursos compuestos. 
>En PowerShell 5.1, la propiedad **PsDscRunAsCredential** es compatible con configuraciones que llaman a recursos compuestos.

>**Nota:** La propiedad **PsDscRunAsCredential** no está disponible en PowerShell 4.0.

En el ejemplo siguiente, **Get-Credential** se usa para solicitar credenciales al usuario. El recurso [Registry](registryResource.md) se usa para cambiar la clave del Registro que especifica el color de fondo de la ventana del símbolo del sistema de Windows.

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
>**Nota:** En este ejemplo se supone que tiene un certificado válido en `C:\publicKeys\targetNode.cer` y que la huella digital del certificado es el valor mostrado.
>Para obtener más información sobre el cifrado de credenciales en archivos MOF de configuración de DSC, vea [Proteger el archivo MOF](secureMOF.md).

