---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC de ejecución con las credenciales de usuario"
ms.openlocfilehash: 11c13d852b506be3e202b798d135eba73d84cfe0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="043eb-103">DSC de ejecución con las credenciales de usuario</span><span class="sxs-lookup"><span data-stu-id="043eb-103">Running DSC with user credentials</span></span> 

> <span data-ttu-id="043eb-104">Se aplica a: Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="043eb-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="043eb-105">Puede ejecutar un recurso de DSC en un conjunto de credenciales especificado mediante la propiedad **PsDscRunAsCredential** automática de la configuración.</span><span class="sxs-lookup"><span data-stu-id="043eb-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="043eb-106">De forma predeterminada, DSC ejecuta cada recurso como la cuenta del sistema.</span><span class="sxs-lookup"><span data-stu-id="043eb-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="043eb-107">A veces, es necesaria la ejecución como usuario, por ejemplo, al instalar paquetes MSI en un contexto de usuario específico, al configurar claves de registro de un usuario, al acceder a un directorio local específico de usuario o al acceder a un recurso compartido de red.</span><span class="sxs-lookup"><span data-stu-id="043eb-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="043eb-108">Cada recurso de DSC tiene una propiedad **PsDscRunAsCredential** que se puede establecer en cualquier credencial de usuario (un objeto [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx)).</span><span class="sxs-lookup"><span data-stu-id="043eb-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) object).</span></span>
<span data-ttu-id="043eb-109">La credencial puede codificarse de forma rígida como el valor de la propiedad de la configuración, o bien puede establecer el valor en [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), que solicitará al usuario una credencial cuando se compile la configuración (para más información sobre la compilación de configuraciones, vea [Configuraciones](configurations.md)).</span><span class="sxs-lookup"><span data-stu-id="043eb-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

><span data-ttu-id="043eb-110">**Nota:** En PowerShell 5.0, no se admite el uso de la propiedad **PsDscRunAsCredential** en configuraciones que llaman a recursos compuestos.</span><span class="sxs-lookup"><span data-stu-id="043eb-110">**Note:** In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> 
><span data-ttu-id="043eb-111">En PowerShell 5.1, la propiedad **PsDscRunAsCredential** es compatible con configuraciones que llaman a recursos compuestos.</span><span class="sxs-lookup"><span data-stu-id="043eb-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>

><span data-ttu-id="043eb-112">**Nota:** La propiedad **PsDscRunAsCredential** no está disponible en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="043eb-112">**Note:** The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="043eb-113">En el ejemplo siguiente, **Get-Credential** se usa para solicitar credenciales al usuario.</span><span class="sxs-lookup"><span data-stu-id="043eb-113">In the following example, **Get-Credential** is used to prompt the user for credentials.</span></span> <span data-ttu-id="043eb-114">El recurso [Registry](registryResource.md) se usa para cambiar la clave del Registro que especifica el color de fondo de la ventana del símbolo del sistema de Windows.</span><span class="sxs-lookup"><span data-stu-id="043eb-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
><span data-ttu-id="043eb-115">**Nota:** En este ejemplo se supone que tiene un certificado válido en `C:\publicKeys\targetNode.cer` y que la huella digital del certificado es el valor mostrado.</span><span class="sxs-lookup"><span data-stu-id="043eb-115">**Note:** This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
><span data-ttu-id="043eb-116">Para obtener más información sobre el cifrado de credenciales en archivos MOF de configuración de DSC, vea [Proteger el archivo MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="043eb-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>

