---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Solucionar problemas con cmdlets
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352113"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="22331-103">Solucionar problemas con cmdlets</span><span class="sxs-lookup"><span data-stu-id="22331-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="22331-104">Cómo resolver el problema "WARNING: Package 'your package name' failed to download" ("ADVERTENCIA: No se pudo descargar el paquete 'nombre del paquete'")</span><span class="sxs-lookup"><span data-stu-id="22331-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="22331-105">Se notifica que a veces se produce un error de `Install-Module` o `Update-Module` en algunos equipos.</span><span class="sxs-lookup"><span data-stu-id="22331-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="22331-106">Según nuestras investigaciones, este problema está relacionado con la conexión de red.</span><span class="sxs-lookup"><span data-stu-id="22331-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="22331-107">Hemos actualizado recientemente el proveedor de NuGet para que pueda descargar paquetes de forma confiable.</span><span class="sxs-lookup"><span data-stu-id="22331-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="22331-108">Puede seguir las instrucciones siguientes para instalar la compilación más reciente del proveedor de NuGet y, después, instalar o actualizar el módulo.</span><span class="sxs-lookup"><span data-stu-id="22331-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="22331-109">En este ejemplo se usa el módulo "Azure".</span><span class="sxs-lookup"><span data-stu-id="22331-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="22331-110">Puntos de conexión de red necesarios</span><span class="sxs-lookup"><span data-stu-id="22331-110">Required network endpoints</span></span>

<span data-ttu-id="22331-111">Los cmdlets de instalación y actualización requieren acceso a Internet para conectarse a los puntos de conexión de red que usa la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22331-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="22331-112">Asegúrese de que las directivas de acceso a la red le permitan conectarse a los puntos de conexión siguientes.</span><span class="sxs-lookup"><span data-stu-id="22331-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="22331-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="22331-113">oneget.org</span></span>
- <span data-ttu-id="22331-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="22331-114">go.microsoft.com</span></span>
- <span data-ttu-id="22331-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="22331-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="22331-116">[www.powershellgallery.com](www.powershellgallery.com)</span><span class="sxs-lookup"><span data-stu-id="22331-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="22331-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="22331-117">devopsgallerystorage.blob.core.windows.net</span></span>
