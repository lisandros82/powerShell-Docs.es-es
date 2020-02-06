---
ms.date: 02/03/2020
keywords: powershell,core
title: Historial de versiones de módulos y cmdlets
ms.openlocfilehash: e421201d74da2cc74b1bd57529fb3c3e5245ecae
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995439"
---
# <a name="release-history-of-modules-and-cmdlets"></a>Historial de versiones de módulos y cmdlets

En este artículo se muestran los módulos y cmdlets que se suministran con diversas versiones de PowerShell. Este es un resumen de la información encontrada en las notas de la versión. Puede encontrar información más detallada en las notas de la versión:

- [Novedades de PowerShell Core 6.2](what-s-new-in-powershell-core-62.md)
- [Novedades de PowerShell Core 6.1](what-s-new-in-powershell-core-61.md)
- [Novedades de PowerShell Core 6.0](what-s-new-in-powershell-core-60.md)
- [Cambios importantes en PowerShell Core 6.0](breaking-changes-ps6.md)
- [Problemas conocidos en PowerShell Core 6.0](known-issues-ps6.md)

Se trata de un trabajo en curso. Ayúdenos a mantener esta información actualizada.

## <a name="module-release-history"></a>Historial de lanzamiento de módulos

|         Nombre del módulo/versión PS          |   5,1   |   6.x   |   7.0   |   7.1   |     Nota:     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlets                                | &check; | &check; | &check; | &check; | Solo Windows |
| ISE (introducido en 2.0)                   | &check; |         |         |         | Solo Windows |
| Microsoft.PowerShell.Archive              | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Core                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Diagnostics          | &check; | &check; | &check; | &check; | Solo Windows |
| Microsoft.PowerShell.Host                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.LocalAccounts        | &check; |         |         |         | Solo Windows |
| Microsoft.PowerShell.Management           | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.ODataUtils           | &check; |         |         |         | Solo Windows |
| Microsoft.PowerShell.Operation.Validation | &check; |         |         |         | Solo Windows |
| Microsoft.PowerShell.Security             | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Utility              | &check; | &check; | &check; | &check; |              |
| Microsoft.WSMan.Management                | &check; | &check; | &check; | &check; | Solo Windows |
| PackageManagement                         | &check; | &check; | &check; | &check; |              |
| PowershellGet                             | &check; | &check; | &check; | &check; |              |
| PSDesiredStateConfiguration               | &check; | &check; | &check; | &check; |              |
| PSDiagnostics                             | &check; | &check; | &check; | &check; | Solo Windows |
| PSReadline 1.x                            | &check; |         |         |         | Solo Windows |
| PSReadline 2.x                            |         | &check; | &check; | &check; |              |
| PSScheduledJob                            | &check; |         |         |         | Solo Windows |
| PSWorkflow                                | &check; |         |         |         | Solo Windows |
| PSWorkflowUtility                         | &check; |         |         |         | Solo Windows |
| ThreadJob                                 |         | &check; | &check; | &check; |              |

## <a name="cmdlet-release-history"></a>Historial de versiones de cmdlets

### <a name="cimcmdlets"></a>CimCmdlets

|         Nombre del cmdlet         |   5,1   |   6.x   |   7.0   |   7.1   |     Nota:     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-BinaryMiLog          | &check; | &check; | &check; | &check; | Solo Windows |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | Solo Windows |
| Get-CimClass                | &check; | &check; | &check; | &check; | Solo Windows |
| Get-CimInstance             | &check; | &check; | &check; | &check; | Solo Windows |
| Get-CimSession              | &check; | &check; | &check; | &check; | Solo Windows |
| Import-BinaryMiLog          | &check; | &check; | &check; | &check; | Solo Windows |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | Solo Windows |
| New-CimInstance             | &check; | &check; | &check; | &check; | Solo Windows |
| New-CimSession              | &check; | &check; | &check; | &check; | Solo Windows |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | Solo Windows |
| Register-CimIndicationEvent | &check; | &check; | &check; | &check; | Solo Windows |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | Solo Windows |
| Remove-CimSession           | &check; | &check; | &check; | &check; | Solo Windows |
| Set-CimInstance             | &check; | &check; | &check; | &check; | Solo Windows |

### <a name="ise-introduced-in-20"></a>ISE (introducido en 2.0)

|    Nombre del cmdlet    |   5,1   | 6.x  |  7.0  |  7.1  |     Nota:     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | Solo Windows |
| Import-IseSnippet | &check; |      |       |       | Solo Windows |
| New-IseSnippet    | &check; |      |       |       | Solo Windows |


### <a name="microsoftpowershellarchive"></a>Microsoft.PowerShell.Archive

|   Nombre del cmdlet    |   5,1   |   6.x   |   7.0   |   7.1   | Nota: |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Compress-Archive | &check; | &check; | &check; | &check; |      |
| Expand-Archive   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Microsoft.PowerShell.Core

|            Nombre del cmdlet            |   5,1   |   6.x   |   7.0   |   7.1   |            Nota:            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Add-History                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | Solo Windows               |
| Clear-History                     | &check; | &check; | &check; | &check; |                            |
| Clear-Host                        | &check; | &check; | &check; | &check; |                            |
| Connect-PSSession                 | &check; | &check; | &check; | &check; | Solo Windows               |
| Debug-Job                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6.2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | Solo Windows               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | Solo Windows               |
| Disconnect-PSSession              | &check; | &check; | &check; | &check; | Solo Windows               |
| Enable-ExperimentalFeature        |         |   6.2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | Solo Windows               |
| Enable-PSSessionConfiguration     | &check; | &check; | &check; | &check; | Solo Windows               |
| Enter-PSHostProcess               | &check; | &check; | &check; | &check; | Compatibilidad agregada con Linux en 6.2 |
| Enter-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Exit-PSHostProcess                | &check; | &check; | &check; | &check; | Compatibilidad agregada con Linux en 6.2 |
| Exit-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Export-Console                    | &check; |         |         |         | Solo Windows               |
| Export-ModuleMember               | &check; | &check; | &check; | &check; |                            |
| ForEach-Object                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6.2   | &check; | &check; |                            |
| Get-Help                          | &check; | &check; | &check; | &check; |                            |
| Get-History                       | &check; | &check; | &check; | &check; |                            |
| Get-Job                           | &check; | &check; | &check; | &check; |                            |
| Get-Module                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | Compatibilidad agregada con Linux en 6.2 |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | Solo Windows               |
| Get-Verb                          | &check; |         |         |         | Solo Windows               |
| Import-Module                     | &check; | &check; | &check; | &check; |                            |
| Invoke-Command                    | &check; | &check; | &check; | &check; |                            |
| Invoke-History                    | &check; | &check; | &check; | &check; |                            |
| New-Module                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | Solo Windows               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Out-Default                       | &check; | &check; | &check; | &check; |                            |
| Out-Host                          | &check; | &check; | &check; | &check; |                            |
| Out-Null                          | &check; | &check; | &check; | &check; |                            |
| Receive-Job                       | &check; | &check; | &check; | &check; |                            |
| Receive-PSSession                 | &check; | &check; | &check; | &check; | Solo Windows               |
| Register-ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| Register-PSSessionConfiguration   | &check; | &check; | &check; | &check; | Solo Windows               |
| Remove-Job                        | &check; | &check; | &check; | &check; |                            |
| Remove-Module                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | Solo Windows               |
| Resume-Job                        | &check; |         |         |         |                            |
| Save-Help                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | Solo Windows               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Start-Job                         | &check; | &check; | &check; | &check; |                            |
| Stop-Job                          | &check; | &check; | &check; | &check; |                            |
| Suspend-Job                       | &check; |         |         |         | Solo Windows               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | Solo Windows               |
| Unregister-PSSessionConfiguration | &check; | &check; | &check; | &check; | Solo Windows               |
| Update-Help                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-Object                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Microsoft.PowerShell.Diagnostics

|  Nombre del cmdlet   |   5,1   |   6.x   |   7.0   |   7.1   |     Nota:     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-Counter | &check; |         |         |         | Solo Windows |
| Get-Counter    | &check; |         | &check; | &check; | Solo Windows |
| Get-WinEvent   | &check; | &check; | &check; | &check; | Solo Windows |
| Import-Counter | &check; |         |         |         | Solo Windows |
| New-WinEvent   | &check; | &check; | &check; | &check; | Solo Windows |

### <a name="microsoftpowershellhost"></a>Microsoft.PowerShell.Host

|   Nombre del cmdlet    |   5,1   |   6.x   |   7.0   |   7.1   | Nota: |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-Transcript | &check; | &check; | &check; | &check; |      |
| Stop-Transcript  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

|       Nombre del cmdlet       |   5,1   | 6.x  |  7.0  |  7.1  |     Nota:     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | Solo Windows |
| Disable-LocalUser       | &check; |      |       |       | Solo Windows |
| Enable-LocalUser        | &check; |      |       |       | Solo Windows |
| Get-LocalGroup          | &check; |      |       |       | Solo Windows |
| Get-LocalGroupMember    | &check; |      |       |       | Solo Windows |
| Get-LocalUser           | &check; |      |       |       | Solo Windows |
| New-LocalGroup          | &check; |      |       |       | Solo Windows |
| New-LocalUser           | &check; |      |       |       | Solo Windows |
| Remove-LocalGroup       | &check; |      |       |       | Solo Windows |
| Remove-LocalGroupMember | &check; |      |       |       | Solo Windows |
| Remove-LocalUser        | &check; |      |       |       | Solo Windows |
| Rename-LocalGroup       | &check; |      |       |       | Solo Windows |
| Rename-LocalUser        | &check; |      |       |       | Solo Windows |
| Set-LocalGroup          | &check; |      |       |       | Solo Windows |
| Set-LocalUser           | &check; |      |       |       | Solo Windows |

### <a name="microsoftpowershellmanagement"></a>Microsoft.PowerShell.Management

|          Nombre del cmdlet          |   5,1   |   6.x   |   7.0   |   7.1   |               Nota:               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Add-Computer                  | &check; |         |         |         | Solo Windows                     |
| Add-Content                   | &check; | &check; | &check; | &check; |                                  |
| Checkpoint-Computer           | &check; |         |         |         | Solo Windows                     |
| Clear-Content                 | &check; | &check; | &check; | &check; |                                  |
| Clear-EventLog                | &check; |         |         |         | Solo Windows                     |
| Clear-Item                    | &check; | &check; | &check; | &check; |                                  |
| Clear-ItemProperty            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | Solo Windows                     |
| Complete-Transaction          | &check; |         |         |         | Solo Windows                     |
| Convert-Path                  | &check; | &check; | &check; | &check; |                                  |
| Copy-Item                     | &check; | &check; | &check; | &check; |                                  |
| Copy-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| Debug-Process                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | Solo Windows                     |
| Enable-ComputerRestore        | &check; |         |         |         | Solo Windows                     |
| Get-ChildItem                 | &check; | &check; | &check; | &check; |                                  |
| Get-Clipboard                 | &check; |         | &check; | &check; | No se admite en macOS           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; |                                  |
| Get-ComputerRestorePoint      | &check; |         |         |         | Solo Windows                     |
| Get-Content                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | Solo Windows                     |
| Get-EventLog                  | &check; |         |         |         | Solo Windows                     |
| Get-HotFix                    | &check; |         | &check; | &check; | Solo Windows                     |
| Get-Item                      | &check; | &check; | &check; | &check; |                                  |
| Get-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-Location                  | &check; | &check; | &check; | &check; |                                  |
| Get-Process                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-Service                   | &check; | &check; | &check; | &check; | Solo Windows                     |
| Get-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Get-Transaction               | &check; |         |         |         | Solo Windows                     |
| Get-WmiObject                 | &check; |         |         |         | Solo Windows                     |
| Invoke-Item                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | Solo Windows                     |
| Join-Path                     | &check; | &check; | &check; | &check; |                                  |
| Limit-EventLog                | &check; |         |         |         | Solo Windows                     |
| Move-Item                     | &check; | &check; | &check; | &check; |                                  |
| Move-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| New-EventLog                  | &check; |         |         |         | Solo Windows                     |
| New-Item                      | &check; | &check; | &check; | &check; |                                  |
| New-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| New-Service                   | &check; | &check; | &check; | &check; | Solo Windows                     |
| New-WebServiceProxy           | &check; |         |         |         | Solo Windows                     |
| Pop-Location                  | &check; | &check; | &check; | &check; |                                  |
| Push-Location                 | &check; | &check; | &check; | &check; |                                  |
| Register-WmiEvent             | &check; |         |         |         | Solo Windows                     |
| Remove-Computer               | &check; |         |         |         | Solo Windows                     |
| Remove-EventLog               | &check; |         |         |         | Solo Windows                     |
| Remove-Item                   | &check; | &check; | &check; | &check; |                                  |
| Remove-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Remove-Service                |         | &check; | &check; | &check; | Solo Windows                     |
| Remove-WmiObject              | &check; |         |         |         | Solo Windows                     |
| Rename-Computer               | &check; | &check; | &check; | &check; |                                  |
| Rename-Item                   | &check; | &check; | &check; | &check; |                                  |
| Rename-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Reset-ComputerMachinePassword | &check; |         |         |         | Solo Windows                     |
| Resolve-Path                  | &check; | &check; | &check; | &check; |                                  |
| Restart-Computer              | &check; | &check; | &check; | &check; |                                  |
| Restart-Service               | &check; | &check; | &check; | &check; | Solo Windows                     |
| Restore-Computer              | &check; |         |         |         | Solo Windows                     |
| Resume-Service                | &check; | &check; | &check; | &check; | Solo Windows                     |
| Set-Clipboard                 | &check; |         | &check; | &check; |                                  |
| Set-Content                   | &check; | &check; | &check; | &check; |                                  |
| Set-Item                      | &check; | &check; | &check; | &check; |                                  |
| Set-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Set-Location                  | &check; | &check; | &check; | &check; |                                  |
| Set-Service                   | &check; | &check; | &check; | &check; | Solo Windows                     |
| Set-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Set-WmiInstance               | &check; |         |         |         | Solo Windows                     |
| Show-ControlPanelItem         | &check; |         |         |         | Solo Windows                     |
| Show-EventLog                 | &check; |         |         |         | Solo Windows                     |
| Split-Path                    | &check; | &check; | &check; | &check; |                                  |
| Start-Process                 | &check; | &check; | &check; | &check; |                                  |
| Start-Service                 | &check; | &check; | &check; | &check; | Solo Windows                     |
| Start-Transaction             | &check; |         |         |         | Solo Windows                     |
| Stop-Computer                 | &check; | &check; | &check; | &check; | Compatibilidad agregada con Linux/macOS en 7.0 |
| Stop-Process                  | &check; | &check; | &check; | &check; |                                  |
| Stop-Service                  | &check; | &check; | &check; | &check; | Solo Windows                     |
| Suspend-Service               | &check; | &check; | &check; | &check; | Solo Windows                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | Solo Windows                     |
| Test-Connection               | &check; | &check; | &check; | &check; |                                  |
| Test-Path                     | &check; | &check; | &check; | &check; |                                  |
| Undo-Transaction              | &check; |         |         |         | Solo Windows                     |
| Use-Transaction               | &check; |         |         |         | Solo Windows                     |
| Wait-Process                  | &check; | &check; | &check; | &check; | No funciona en Linux/macOS     |
| Write-EventLog                | &check; |         |         |         | Solo Windows                     |

### <a name="microsoftpowershellodatautils"></a>Microsoft.PowerShell.ODataUtils

|        Nombre del cmdlet        |   5,1   | 6.x  |  7.0  |  7.1  |     Nota:     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Export-ODataEndpointProxy | &check; |      |       |       | Solo Windows |

### <a name="microsoftpowershelloperationvalidation"></a>Microsoft.PowerShell.Operation.Validation

|        Nombre del cmdlet         |   5,1   | 6.x  |  7.0  |  7.1  |     Nota:     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | Solo Windows |
| Invoke-OperationValidation | &check; |      |       |       | Solo Windows |

### <a name="microsoftpowershellsecurity"></a>Microsoft.PowerShell.Security

|        Nombre del cmdlet        |   5,1   |   6.x   |   7.0   |   7.1   |                  Nota:                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom-SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo-SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-Acl                   | &check; | &check; | &check; | &check; | Solo Windows                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | Solo Windows                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | Solo Windows                            |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-ExecutionPolicy       | &check; | &check; | &check; | &check; | Devuelve **Unrestricted** en Linux/macOS |
| Get-PfxCertificate        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | Solo Windows                            |
| Protect-CmsMessage        | &check; | &check; | &check; | &check; | Solo Windows                            |
| Set-Acl                   | &check; | &check; | &check; | &check; | Solo Windows                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | Solo Windows                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | No hace nada en Linux/macOS             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | Solo Windows                            |
| Unprotect-CmsMessage      | &check; | &check; | &check; | &check; | Solo Windows                            |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Nombre del cmdlet        |   5,1   |   6.x   |   7.0   |   7.1   |                   Nota:                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Add-Member                | &check; | &check; | &check; | &check; |                                           |
| Add-Type                  | &check; | &check; | &check; | &check; |                                           |
| Clear-Variable            | &check; | &check; | &check; | &check; |                                           |
| Compare-Object            | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Csv           | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Json          | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Markdown      |         |   6.1   | &check; | &check; |                                           |
| ConvertFrom-SddlString    | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-String        | &check; |         |         |         |                                           |
| ConvertFrom-StringData    | &check; | &check; | &check; | &check; |                                           |
| Convert-String            | &check; |         |         |         |                                           |
| ConvertTo-Csv             | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Html            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Json            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Xml             | &check; | &check; | &check; | &check; |                                           |
| Debug-Runspace            | &check; | &check; | &check; | &check; |                                           |
| Disable-PSBreakpoint      | &check; | &check; | &check; | &check; |                                           |
| Disable-RunspaceDebug     | &check; | &check; | &check; | &check; |                                           |
| Enable-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Enable-RunspaceDebug      | &check; | &check; | &check; | &check; |                                           |
| Export-Alias              | &check; | &check; | &check; | &check; |                                           |
| Export-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Export-Csv                | &check; | &check; | &check; | &check; |                                           |
| Export-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Export-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Get-Culture               | &check; | &check; | &check; | &check; |                                           |
| Get-Date                  | &check; | &check; | &check; | &check; |                                           |
| Get-Error                 |         |         | &check; | &check; |                                           |
| Get-Event                 | &check; | &check; | &check; | &check; | Ningún origen del evento disponible en Linux/macOS |
| Get-EventSubscriber       | &check; | &check; | &check; | &check; |                                           |
| Get-FileHash              | &check; | &check; | &check; | &check; |                                           |
| Get-FormatData            | &check; | &check; | &check; | &check; |                                           |
| Get-Host                  | &check; | &check; | &check; | &check; |                                           |
| Get-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Get-Member                | &check; | &check; | &check; | &check; |                                           |
| Get-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Get-PSCallStack           | &check; | &check; | &check; | &check; |                                           |
| Get-Random                | &check; | &check; | &check; | &check; |                                           |
| Get-Runspace              | &check; | &check; | &check; | &check; |                                           |
| Get-RunspaceDebug         | &check; | &check; | &check; | &check; |                                           |
| Get-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Get-TypeData              | &check; | &check; | &check; | &check; |                                           |
| Get-UICulture             | &check; | &check; | &check; | &check; |                                           |
| Get-Unique                | &check; | &check; | &check; | &check; |                                           |
| Get-Uptime                |         | &check; | &check; | &check; |                                           |
| Get-Variable              | &check; | &check; | &check; | &check; |                                           |
| Get-Verb                  |         | &check; | &check; | &check; |                                           |
| Group-Object              | &check; | &check; | &check; | &check; |                                           |
| Import-Alias              | &check; | &check; | &check; | &check; |                                           |
| Import-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Import-Csv                | &check; | &check; | &check; | &check; |                                           |
| Import-LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Import-PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Import-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-Expression         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Invoke-WebRequest         | &check; | &check; | &check; | &check; |                                           |
| Join-String               |         | &check; | &check; | &check; |                                           |
| Measure-Command           | &check; | &check; | &check; | &check; |                                           |
| Measure-Object            | &check; | &check; | &check; | &check; |                                           |
| New-Alias                 | &check; | &check; | &check; | &check; |                                           |
| New-Event                 | &check; | &check; | &check; | &check; | Ningún origen del evento disponible en Linux/macOS |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| New-Object                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| New-TimeSpan              | &check; | &check; | &check; | &check; |                                           |
| New-Variable              | &check; | &check; | &check; | &check; |                                           |
| Out-File                  | &check; | &check; | &check; | &check; |                                           |
| Out-Gridview              | &check; |         | &check; | &check; |                                           |
| Out-Printer               | &check; |         | &check; | &check; |                                           |
| Out-String                | &check; | &check; | &check; | &check; |                                           |
| Read-Host                 | &check; | &check; | &check; | &check; |                                           |
| Register-EngineEvent      | &check; | &check; | &check; | &check; | Ningún origen del evento disponible en Linux/macOS |
| Register-ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Remove-Alias              |         | &check; | &check; | &check; |                                           |
| Remove-Event              | &check; | &check; | &check; | &check; | Ningún origen del evento disponible en Linux/macOS |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Remove-Variable           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Select-String             | &check; | &check; | &check; | &check; |                                           |
| Select-Xml                | &check; | &check; | &check; | &check; |                                           |
| Send-MailMessage          | &check; | &check; | &check; | &check; |                                           |
| Set-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Set-Date                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-Variable              | &check; | &check; | &check; | &check; |                                           |
| Show-Command              | &check; |         | &check; | &check; |                                           |
| Show-Markdown             |         |   6.1   | &check; | &check; |                                           |
| Sort-Object               | &check; | &check; | &check; | &check; |                                           |
| Start-Sleep               | &check; | &check; | &check; | &check; |                                           |
| Tee-Object                | &check; | &check; | &check; | &check; |                                           |
| Test-Json                 |         | &check; | &check; | &check; |                                           |
| Trace-Command             | &check; | &check; | &check; | &check; |                                           |
| Unblock-File              | &check; | &check; | &check; | &check; | Compatibilidad agregada con macOS en 7.0            |
| Unregister-Event          | &check; | &check; | &check; | &check; | Ningún origen del evento disponible en Linux/macOS |
| Update-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-List               | &check; |         | &check; | &check; |                                           |
| Update-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Wait-Debugger             | &check; | &check; | &check; | &check; |                                           |
| Wait-Event                | &check; | &check; | &check; | &check; |                                           |
| Write-Debug               | &check; | &check; | &check; | &check; |                                           |
| Write-Error               | &check; | &check; | &check; | &check; |                                           |
| Write-Host                | &check; | &check; | &check; | &check; |                                           |
| Write-Information         | &check; | &check; | &check; | &check; |                                           |
| Write-Output              | &check; | &check; | &check; | &check; |                                           |
| Write-Progress            | &check; | &check; | &check; | &check; |                                           |
| Write-Verbose             | &check; | &check; | &check; | &check; |                                           |
| Write-Warning             | &check; | &check; | &check; | &check; |                                           |

### <a name="microsoftwsmanmanagement"></a>Microsoft.WSMan.Management

|      Nombre del cmdlet       |   5,1   |   6.x   |   7.0   |   7.1   |     Nota:     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Connect-WSMan          | &check; | &check; | &check; | &check; | Solo Windows |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | Solo Windows |
| Disconnect-WSMan       | &check; | &check; | &check; | &check; | Solo Windows |
| Enable-WSManCredSSP    | &check; | &check; | &check; | &check; | Solo Windows |
| Get-WSManCredSSP       | &check; | &check; | &check; | &check; | Solo Windows |
| Get-WSManInstance      | &check; | &check; | &check; | &check; | Solo Windows |
| Invoke-WSManAction     | &check; | &check; | &check; | &check; | Solo Windows |
| New-WSManInstance      | &check; | &check; | &check; | &check; | Solo Windows |
| New-WSManSessionOption | &check; | &check; | &check; | &check; | Solo Windows |
| Remove-WSManInstance   | &check; | &check; | &check; | &check; | Solo Windows |
| Set-WSManInstance      | &check; | &check; | &check; | &check; | Solo Windows |
| Set-WSManQuickConfig   | &check; | &check; | &check; | &check; | Solo Windows |
| Test-WSMan             | &check; | &check; | &check; | &check; | Solo Windows |

### <a name="packagemanagement"></a>PackageManagement

|       Nombre del cmdlet        |   5,1   |   6.x   |   7.0   |   7.1   | Nota: |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Package             | &check; | &check; | &check; | &check; |      |
| Find-PackageProvider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Import-PackageProvider   | &check; | &check; | &check; | &check; |      |
| Install-Package          | &check; | &check; | &check; | &check; |      |
| Install-PackageProvider  | &check; | &check; | &check; | &check; |      |
| Register-PackageSource   | &check; | &check; | &check; | &check; |      |
| Save-Package             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Uninstall-Package        | &check; | &check; | &check; | &check; |      |
| Unregister-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Nombre del cmdlet           |   5,1   |   6.x   |   7.0   |   7.1   | Nota: |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Command                    | &check; | &check; | &check; | &check; |      |
| Find-DscResource                | &check; | &check; | &check; | &check; |      |
| Find-Module                     | &check; | &check; | &check; | &check; |      |
| Find-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Find-Script                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Install-Module                  | &check; | &check; | &check; | &check; |      |
| Install-Script                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publish-Module                  | &check; | &check; | &check; | &check; |      |
| Publish-Script                  | &check; | &check; | &check; | &check; |      |
| Register-PSRepository           | &check; | &check; | &check; | &check; |      |
| Save-Module                     | &check; | &check; | &check; | &check; |      |
| Save-Script                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Uninstall-Module                | &check; | &check; | &check; | &check; |      |
| Uninstall-Script                | &check; | &check; | &check; | &check; |      |
| Unregister-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-Module                   | &check; | &check; | &check; | &check; |      |
| Update-ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Update-Script                   | &check; | &check; | &check; | &check; |      |
| Update-ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Nombre del cmdlet                 |   5,1   |   6.x   |   7.0   |   7.1   |     Nota:     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Add-NodeKeys                               |         | &check; |         |         |              |
| ConvertTo-MOFInstance                      |         | &check; |         |         |              |
| Disable-DscDebug                           | &check; |         |         |         | Solo Windows |
| Enable-DscDebug                            | &check; |         |         |         | Solo Windows |
| Generate-VersionInfo                       |         | &check; |         |         |              |
| Get-CompatibleVersionAddtionaPropertiesStr |         | &check; |         |         |              |
| Get-ComplexResourceQualifier               |         | &check; |         |         |              |
| Get-ConfigurationErrorCount                |         | &check; |         |         |              |
| Get-DscConfiguration                       | &check; |         |         |         | Solo Windows |
| Get-DscConfigurationStatus                 | &check; |         |         |         | Solo Windows |
| Get-DscLocalConfigurationManager           | &check; |         |         |         | Solo Windows |
| Get-DscResource                            | &check; | &check; | &check; | &check; |              |
| Get-DSCResourceModules                     |         | &check; |         |         |              |
| Get-EncryptedPassword                      |         | &check; |         |         |              |
| Get-InnerMostErrorRecord                   |         | &check; |         |         |              |
| Get-MofInstanceName                        |         | &check; |         |         |              |
| Get-MofInstanceText                        |         | &check; |         |         |              |
| Get-PositionInfo                           |         | &check; |         |         |              |
| Get-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Get-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Get-PSMetaConfigDocumentInstVersionInfo    |         | &check; |         |         |              |
| Get-PSMetaConfigurationProcessed           |         | &check; |         |         |              |
| Get-PSTopConfigurationName                 |         | &check; |         |         |              |
| Get-PublicKeyFromFile                      |         | &check; |         |         |              |
| Get-PublicKeyFromStore                     |         | &check; |         |         |              |
| Initialize-ConfigurationRuntimeState       |         | &check; |         |         |              |
| Invoke-DscResource                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publish-DscConfiguration                   | &check; |         |         |         | Solo Windows |
| Remove-DscConfigurationDocument            | &check; |         |         |         | Solo Windows |
| Restore-DscConfiguration                   | &check; |         |         |         | Solo Windows |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | Solo Windows |
| Set-NodeExclusiveResources                 |         | &check; |         |         |              |
| Set-NodeManager                            |         | &check; |         |         |              |
| Set-NodeResources                          |         | &check; |         |         |              |
| Set-NodeResourceSource                     |         | &check; |         |         |              |
| Set-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Set-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Set-PSMetaConfigDocInsProcessedBeforeMeta  |         | &check; |         |         |              |
| Set-PSMetaConfigVersionInfoV2              |         | &check; |         |         |              |
| Set-PSTopConfigurationName                 |         | &check; |         |         |              |
| Start-DscConfiguration                     | &check; |         |         |         | Solo Windows |
| Stop-DscConfiguration                      | &check; |         |         |         | Solo Windows |
| Test-ConflictingResources                  |         | &check; |         |         |              |
| Test-DscConfiguration                      | &check; |         |         |         | Solo Windows |
| Test-ModuleReloadRequired                  |         | &check; |         |         |              |
| Test-MofInstanceText                       |         | &check; |         |         |              |
| Test-NodeManager                           |         | &check; |         |         |              |
| Test-NodeResources                         |         | &check; |         |         |              |
| Test-NodeResourceSource                    |         | &check; |         |         |              |
| Update-ConfigurationDocumentRef            |         | &check; |         |         |              |
| Update-ConfigurationErrorCount             |         | &check; |         |         |              |
| Update-DependsOn                           |         | &check; |         |         |              |
| Update-DscConfiguration                    | &check; |         |         |         | Solo Windows |
| Update-LocalConfigManager                  |         | &check; |         |         |              |
| Update-ModuleVersion                       |         | &check; |         |         |              |
| ValidateUpdate-ConfigurationData           |         | &check; |         |         |              |
| Write-Log                                  |         | &check; |         |         |              |
| Write-MetaConfigFile                       |         | &check; |         |         |              |
| Write-NodeMOFFile                          |         | &check; |         |         |              |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Nombre del cmdlet          |   5,1   |   6.x   |   7.0   |   7.1   |     Nota:     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6.2   | &check; | &check; | Solo Windows |
| Disable-PSWSManCombinedTrace | &check; |   6.2   | &check; | &check; | Solo Windows |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | Solo Windows |
| Enable-PSTrace               | &check; | &check; | &check; | &check; | Solo Windows |
| Enable-PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | Solo Windows |
| Enable-WSManTrace            | &check; |   6.2   | &check; | &check; | Solo Windows |
| Get-LogProperties            | &check; |   6.2   | &check; | &check; | Solo Windows |
| Set-LogProperties            | &check; |   6.2   | &check; | &check; | Solo Windows |
| Start-Trace                  | &check; |   6.2   | &check; | &check; | Solo Windows |
| Stop-Trace                   | &check; |   6.2   | &check; | &check; | Solo Windows |

### <a name="psreadline"></a>PSReadline

|         Nombre del cmdlet         |   5,1   |   6.x   |   7.0   |   7.1   | Nota: |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Get-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Get-PSReadlineOption        | &check; | &check; | &check; | &check; |      |
| PSConsoleHostReadline       | &check; | &check; | &check; | &check; |      |
| Remove-PSReadlineKeyHandler | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineOption        | &check; | &check; | &check; | &check; |      |

### <a name="psscheduledjob"></a>PSScheduledJob

|       Nombre del cmdlet       |   5,1   | 6.x  |  7.0  |  7.1  |     Nota:     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-JobTrigger          | &check; |      |       |       | Solo Windows |
| Disable-JobTrigger      | &check; |      |       |       | Solo Windows |
| Disable-ScheduledJob    | &check; |      |       |       | Solo Windows |
| Enable-JobTrigger       | &check; |      |       |       | Solo Windows |
| Enable-ScheduledJob     | &check; |      |       |       | Solo Windows |
| Get-JobTrigger          | &check; |      |       |       | Solo Windows |
| Get-ScheduledJob        | &check; |      |       |       | Solo Windows |
| Get-ScheduledJobOption  | &check; |      |       |       | Solo Windows |
| New-JobTrigger          | &check; |      |       |       | Solo Windows |
| New-ScheduledJobOption  | &check; |      |       |       | Solo Windows |
| Register-ScheduledJob   | &check; |      |       |       | Solo Windows |
| Remove-JobTrigger       | &check; |      |       |       | Solo Windows |
| Set-JobTrigger          | &check; |      |       |       | Solo Windows |
| Set-ScheduledJob        | &check; |      |       |       | Solo Windows |
| Set-ScheduledJobOption  | &check; |      |       |       | Solo Windows |
| Unregister-ScheduledJob | &check; |      |       |       | Solo Windows |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow y PSWorkflowUtility

|          Nombre del cmdlet          |   5,1   | 6.x  |  7.0  |  7.1  |     Nota:     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-PSWorkflowExecutionOption | &check; |      |       |       | Solo Windows |
| New-PSWorkflowSession         | &check; |      |       |       | Solo Windows |
| Invoke-AsWorkflow             | &check; |      |       |       | Solo Windows |

### <a name="threadjob"></a>ThreadJob

|   Nombre del cmdlet   |  5,1  |   6.x   |   7.0   |   7.1   | Nota: |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; |      |
