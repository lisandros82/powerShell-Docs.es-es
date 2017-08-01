---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "creación de un controlador de dominio"
ms.technology: powershell
ms.openlocfilehash: 80b957ed666ca626c6083041cf99c263e2e0dc27
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
### <a name="creating-a-domain-controller"></a><span data-ttu-id="aaf92-103">Creación de un controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="aaf92-103">Creating a Domain Controller</span></span>

<span data-ttu-id="aaf92-104">Este documento da por supuesto que la máquina está unida al dominio.</span><span class="sxs-lookup"><span data-stu-id="aaf92-104">This document assumes that your machine is domain joined.</span></span>
<span data-ttu-id="aaf92-105">Si actualmente no tiene un dominio al que unirse, esta sección puede ayudarle a crear rápidamente un controlador de dominio con DSC.</span><span class="sxs-lookup"><span data-stu-id="aaf92-105">If you currently don't have a domain to join, this section can help you quickly stand up a domain controller using DSC.</span></span>

#### <a name="prerequisites"></a><span data-ttu-id="aaf92-106">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="aaf92-106">Prerequisites</span></span>

1.  <span data-ttu-id="aaf92-107">La máquina se encuentra en una red interna.</span><span class="sxs-lookup"><span data-stu-id="aaf92-107">The machine is on an internal network</span></span>
2.  <span data-ttu-id="aaf92-108">La máquina no está unida a un dominio existente.</span><span class="sxs-lookup"><span data-stu-id="aaf92-108">The machine is not joined to an existing domain</span></span>
3.  <span data-ttu-id="aaf92-109">La máquina ejecuta Windows Server 2016 o tiene instalado WMF 5.0.</span><span class="sxs-lookup"><span data-stu-id="aaf92-109">The machine is running Windows Server 2016 or has WMF 5.0 installed</span></span>

#### <a name="install-xactivedirectory"></a><span data-ttu-id="aaf92-110">Instalación de xActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="aaf92-110">Install xActiveDirectory</span></span>
<span data-ttu-id="aaf92-111">Si la máquina tiene una conexión a Internet activa, ejecute el comando siguiente en una ventana de PowerShell con privilegios elevados:</span><span class="sxs-lookup"><span data-stu-id="aaf92-111">If your machine has an active internet connection, run the following command in an elevated PowerShell window:</span></span>
```PowerShell
Install-Module xActiveDirectory -Force
```
<span data-ttu-id="aaf92-112">Si no tiene una conexión a Internet, instale xActiveDirectory en otra máquina y, después, copie la carpeta xActiveDirectory en la carpeta "C:\Archivos de programa\WindowsPowerShell\Modules" en su equipo.</span><span class="sxs-lookup"><span data-stu-id="aaf92-112">If you do not have an internet connection, install xActiveDirectory to another machine and then copy the xActiveDirectory folder to the "C:\Program Files\WindowsPowerShell\Modules" folder on your machine.</span></span>

<span data-ttu-id="aaf92-113">Para confirmar que la instalación se ha realizado correctamente, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="aaf92-113">To confirm the installation succeeded, run the following command:</span></span>
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### <a name="set-up-a-domain-with-dsc"></a><span data-ttu-id="aaf92-114">Configurar un dominio con DSC</span><span class="sxs-lookup"><span data-stu-id="aaf92-114">Set up a domain with DSC</span></span>
<span data-ttu-id="aaf92-115">Copie el script siguiente en PowerShell para hacer que la máquina sea el controlador de dominio de un dominio nuevo.</span><span class="sxs-lookup"><span data-stu-id="aaf92-115">Copy the following script in PowerShell to make your machine a Domain Controller in a new domain.</span></span>
<span data-ttu-id="aaf92-116">**NOTA DEL AUTOR: HAY UN PROBLEMA CONOCIDO CON LAS CREDENCIALES PROPORCIONADAS SI NO SE USAN.  PARA QUE SEAN SEGURAS, NO OLVIDE LA CONTRASEÑA DE ADMINISTRADOR LOCAL.**</span><span class="sxs-lookup"><span data-stu-id="aaf92-116">**AUTHOR'S NOTE: THERE IS A KNOWN ISSUE WITH THE CREDENTIALS PROVIDED NOT BEING USED.  TO BE SAFE, DON'T FORGET YOUR LOCAL ADMIN PASSWORD.**</span></span>

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }

}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
<span data-ttu-id="aaf92-117">La máquina se reiniciará varias veces.</span><span class="sxs-lookup"><span data-stu-id="aaf92-117">Your machine will restart a few times.</span></span>
<span data-ttu-id="aaf92-118">Sabrá que el proceso se ha completado cuando vea un archivo denominado "C:\temp.txt" con el texto "Domain has been created" (Se ha creado el dominio).</span><span class="sxs-lookup"><span data-stu-id="aaf92-118">You will know the process is complete once you see a file called "C:\temp.txt" containing "Domain has been created."</span></span>

#### <a name="set-up-users-and-groups"></a><span data-ttu-id="aaf92-119">Configurar usuarios y grupos</span><span class="sxs-lookup"><span data-stu-id="aaf92-119">Set up Users and Groups</span></span>
<span data-ttu-id="aaf92-120">Los comandos siguientes configurarán un grupo de operadores y departamento de soporte técnico en su dominio y un usuario correspondiente sin privilegios de administrador que es miembro de ese grupo.</span><span class="sxs-lookup"><span data-stu-id="aaf92-120">The following commands will set up an Operator and Helpdesk group in your domain and a corresponding non-administrator user who is a member of that group.</span></span>
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

