---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: f3c218fc668e35fa50047459d8031d77cdf985a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="reporting-on-jea"></a><span data-ttu-id="73636-102">Generación de informes en JEA</span><span class="sxs-lookup"><span data-stu-id="73636-102">Reporting on JEA</span></span>
<span data-ttu-id="73636-103">Para informar sobre el estado de la configuración de JEA, puede usar:</span><span class="sxs-lookup"><span data-stu-id="73636-103">In order to report on the state of your JEA configuration, you can use:</span></span>
1.  <span data-ttu-id="73636-104">**Get-PSSessionConfiguration** para devolver una lista de todos los puntos de conexión registrados en una máquina determinada.</span><span class="sxs-lookup"><span data-stu-id="73636-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2.  <span data-ttu-id="73636-105">**Get-PSSessionCapability** para informar de las funcionalidades que cualquier usuario determinado tiene en un punto de conexión concreto.</span><span class="sxs-lookup"><span data-stu-id="73636-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="73636-106">Este es un ejemplo de **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="73636-106">Here’s an example of **Get-PSSessionCapability**:</span></span>
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source           
-----------     ----                                               -------    ------           
Alias           clear -> Clear-Host                                                            
Alias           cls -> Clear-Host                                                              
Alias           exsn -> Exit-PSSession                                                         
Alias           gcm -> Get-Command                                                             
Alias           measure -> Measure-Object                                                      
Alias           select -> Select-Object                                                        
Function        Clear-Host                                                                     
Function        Exit-PSSession                                                                 
Function        Get-Command                                                                    
Function        Get-FormatData                                                                 
Function        Get-Help                                                                       
Function        Get-UserInfo                                                                   
Function        Measure-Object                                                                 
Function        Out-Default                                                                    
Function        Select-Object                                                                  
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

<span data-ttu-id="73636-107">Para informar sobre las _acciones_ que los usuarios emprendieron durante una sesión de JEA, puede hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="73636-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="73636-108">Habilitar las transcripciones de "consentimiento temporal" para ese punto de conexión de JEA y consulte el directorio de transcripción para obtener un registro completo de las acciones de cada usuario</span><span class="sxs-lookup"><span data-stu-id="73636-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="73636-109">Active el registro del módulo de PowerShell e inspeccione los registros de eventos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73636-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>

