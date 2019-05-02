---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5ac9566979e1b761249f5cc7c62ed44047a2b9f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058019"
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="1b298-102">Registrar un repositorio de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b298-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="1b298-103">Puede configurar PowerShellGet para operar en repositorios internos.</span><span class="sxs-lookup"><span data-stu-id="1b298-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="1b298-104">Esto se realiza mediante las siguientes adiciones:</span><span class="sxs-lookup"><span data-stu-id="1b298-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="1b298-105">Register-PSRepository: registra un repositorio del usuario actual.</span><span class="sxs-lookup"><span data-stu-id="1b298-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="1b298-106">Unregister-PSRepository: quita un repositorio registrado del usuario actual.</span><span class="sxs-lookup"><span data-stu-id="1b298-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="1b298-107">Set-PSRepository: establece los valores de un repositorio registrado.</span><span class="sxs-lookup"><span data-stu-id="1b298-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="1b298-108">Get-PSRepository: obtiene todos los repositorios registrados del usuario actual.</span><span class="sxs-lookup"><span data-stu-id="1b298-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="1b298-109">Una vez registrado un repositorio, puede usar Find-Module e Install-Module para trabajar con él.</span><span class="sxs-lookup"><span data-stu-id="1b298-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```
