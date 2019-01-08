---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Uso de las credenciales con recursos de DSC
ms.openlocfilehash: af54c286ce744cd7db0b0e2d05087f60cdf1a33c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402898"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="72140-103">Uso de las credenciales con recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="72140-103">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="72140-104">Se aplica a: Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="72140-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="72140-105">Puede ejecutar un recurso de DSC en un conjunto de credenciales especificado mediante la propiedad **PsDscRunAsCredential** automática de la configuración.</span><span class="sxs-lookup"><span data-stu-id="72140-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span>
<span data-ttu-id="72140-106">De forma predeterminada, DSC ejecuta cada recurso como la cuenta del sistema.</span><span class="sxs-lookup"><span data-stu-id="72140-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="72140-107">A veces, es necesaria la ejecución como usuario, por ejemplo, al instalar paquetes MSI en un contexto de usuario específico, al configurar claves de registro de un usuario, al acceder a un directorio local específico de usuario o al acceder a un recurso compartido de red.</span><span class="sxs-lookup"><span data-stu-id="72140-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="72140-108">Cada recurso de DSC tiene una propiedad **PsDscRunAsCredential** que se puede establecer en cualquier credencial de usuario (un objeto [PSCredential](/dotnet/api/system.management.automation.pscredential)).</span><span class="sxs-lookup"><span data-stu-id="72140-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span>
<span data-ttu-id="72140-109">La credencial puede codificarse de forma rígida como el valor de la propiedad de la configuración, o bien puede establecer el valor en [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), que solicitará al usuario una credencial cuando se compile la configuración (para más información sobre la compilación de configuraciones, vea [Configuraciones](configurations.md)).</span><span class="sxs-lookup"><span data-stu-id="72140-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="72140-110">En PowerShell 5.0, no se admite el uso de la propiedad **PsDscRunAsCredential** en configuraciones que llaman a recursos compuestos.</span><span class="sxs-lookup"><span data-stu-id="72140-110">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span>
> <span data-ttu-id="72140-111">En PowerShell 5.1, la propiedad **PsDscRunAsCredential** es compatible con configuraciones que llaman a recursos compuestos.</span><span class="sxs-lookup"><span data-stu-id="72140-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>
> <span data-ttu-id="72140-112">La propiedad **PsDscRunAsCredential** no está disponible en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="72140-112">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="72140-113">En el ejemplo siguiente, `Get-Credential` se usa para solicitar credenciales al usuario.</span><span class="sxs-lookup"><span data-stu-id="72140-113">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span>
<span data-ttu-id="72140-114">El recurso **Registry** se usa para cambiar la clave del Registro que especifica el color de fondo de la ventana del símbolo del sistema de Windows.</span><span class="sxs-lookup"><span data-stu-id="72140-114">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
> <span data-ttu-id="72140-115">En este ejemplo se supone que tiene un certificado válido en `C:\publicKeys\targetNode.cer` y que la huella digital del certificado es el valor mostrado.</span><span class="sxs-lookup"><span data-stu-id="72140-115">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
> <span data-ttu-id="72140-116">Para obtener más información sobre el cifrado de credenciales en archivos MOF de configuración de DSC, vea [Proteger el archivo MOF](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="72140-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
