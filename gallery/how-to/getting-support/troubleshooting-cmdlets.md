---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Solucionar problemas con cmdlets
ms.openlocfilehash: e8890cb6bbe661b8524d83cabf91483acbde8095
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219834"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="7c31d-103">Solucionar problemas con cmdlets</span><span class="sxs-lookup"><span data-stu-id="7c31d-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="7c31d-104">Cómo resolver el problema "WARNING: Package 'your package name' failed to download" (ADVERTENCIA: No se pudo descargar el paquete 'nombre del paquete'")</span><span class="sxs-lookup"><span data-stu-id="7c31d-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="7c31d-105">Se ha notificado que a veces se produce un error en Install-Module o Update-Module en algunos equipos.</span><span class="sxs-lookup"><span data-stu-id="7c31d-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="7c31d-106">Según nuestras investigaciones, este problema está relacionado con la conexión de red.</span><span class="sxs-lookup"><span data-stu-id="7c31d-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="7c31d-107">Hemos actualizado recientemente el proveedor de NuGet para que pueda descargar paquetes de forma confiable.</span><span class="sxs-lookup"><span data-stu-id="7c31d-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="7c31d-108">Puede seguir las instrucciones siguientes para instalar la compilación más reciente del proveedor de NuGet y, después, instalar o actualizar el módulo.</span><span class="sxs-lookup"><span data-stu-id="7c31d-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="7c31d-109">En este ejemplo se usa el módulo "Azure".</span><span class="sxs-lookup"><span data-stu-id="7c31d-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```