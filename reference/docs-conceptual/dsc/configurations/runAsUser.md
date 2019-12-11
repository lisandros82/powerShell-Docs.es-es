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
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="a599c-103">Uso de las credenciales con recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="a599c-103">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="a599c-104">Se aplica a: Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="a599c-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="a599c-105">Puede ejecutar un recurso de DSC en un conjunto de credenciales especificado mediante la propiedad **PsDscRunAsCredential** automática de la configuración.</span><span class="sxs-lookup"><span data-stu-id="a599c-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="a599c-106">De forma predeterminada, DSC ejecuta cada recurso como la cuenta del sistema.</span><span class="sxs-lookup"><span data-stu-id="a599c-106">By default, DSC runs each resource as the system account.</span></span> <span data-ttu-id="a599c-107">A veces, es necesaria la ejecución como usuario, por ejemplo, al instalar paquetes MSI en un contexto de usuario específico, al configurar claves de registro de un usuario, al acceder a un directorio local específico de usuario o al acceder a un recurso compartido de red.</span><span class="sxs-lookup"><span data-stu-id="a599c-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span> <span data-ttu-id="a599c-108">La máquina de destino necesita la propiedad **SeInteractiveLogonRight** para cualquier cuenta que especifique en **PSDSCRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="a599c-108">The **SeInteractiveLogonRight** is required, by the target machine, for any account you specify to **PSDSCRunAsCredential**.</span></span> <span data-ttu-id="a599c-109">Para obtener más información, consulte [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants) (Constantes de derechos de cuentas).</span><span class="sxs-lookup"><span data-stu-id="a599c-109">For more information, see [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants).</span></span>

<span data-ttu-id="a599c-110">Cada recurso de DSC tiene una propiedad **PsDscRunAsCredential** que se puede establecer en cualquier credencial de usuario (un objeto [PSCredential](/dotnet/api/system.management.automation.pscredential)).</span><span class="sxs-lookup"><span data-stu-id="a599c-110">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span> <span data-ttu-id="a599c-111">La credencial puede codificarse de forma rígida como el valor de la propiedad de la configuración, o bien puede establecer el valor en [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), que solicitará al usuario una credencial cuando se compile la configuración (para más información sobre la compilación de configuraciones, vea [Configuraciones](configurations.md)).</span><span class="sxs-lookup"><span data-stu-id="a599c-111">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a599c-112">En PowerShell 5.0, no se admite el uso de la propiedad **PsDscRunAsCredential** en configuraciones que llaman a recursos compuestos.</span><span class="sxs-lookup"><span data-stu-id="a599c-112">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> <span data-ttu-id="a599c-113">En PowerShell 5.1, la propiedad **PsDscRunAsCredential** es compatible con configuraciones que llaman a recursos compuestos.</span><span class="sxs-lookup"><span data-stu-id="a599c-113">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span> <span data-ttu-id="a599c-114">La propiedad **PsDscRunAsCredential** no está disponible en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="a599c-114">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="a599c-115">En el ejemplo siguiente, `Get-Credential` se usa para solicitar credenciales al usuario.</span><span class="sxs-lookup"><span data-stu-id="a599c-115">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span> <span data-ttu-id="a599c-116">El recurso **Registry** se usa para cambiar la clave del Registro que especifica el color de fondo de la ventana del símbolo del sistema de Windows.</span><span class="sxs-lookup"><span data-stu-id="a599c-116">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
> <span data-ttu-id="a599c-117">En este ejemplo se supone que tiene un certificado válido en `C:\publicKeys\targetNode.cer` y que la huella digital del certificado es el valor mostrado.</span><span class="sxs-lookup"><span data-stu-id="a599c-117">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span> <span data-ttu-id="a599c-118">Para obtener más información sobre el cifrado de credenciales en archivos MOF de configuración de DSC, vea [Proteger el archivo MOF](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="a599c-118">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
