---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Implementación y mantenimiento de varias máquinas"
ms.technology: powershell
ms.openlocfilehash: 8117d0d12c062b460cb7117b54c138c8db5a1d0c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="multi-machine-deployment-and-maintenance"></a><span data-ttu-id="5b52f-103">Implementación y mantenimiento de varias máquinas</span><span class="sxs-lookup"><span data-stu-id="5b52f-103">Multi-machine Deployment and Maintenance</span></span>
<span data-ttu-id="5b52f-104">En este momento, ha implementado JEA en sistemas locales varias veces.</span><span class="sxs-lookup"><span data-stu-id="5b52f-104">At this point, you have deployed JEA to local systems several times.</span></span>
<span data-ttu-id="5b52f-105">Dado que su entorno de producción probablemente esté formado por más de una máquina, es importante que siga los pasos fundamentales del proceso de implementación que deben repetirse en cada máquina.</span><span class="sxs-lookup"><span data-stu-id="5b52f-105">Because your production environment probably consists of more than one machine, it's important to walk through the critical steps in the deployment process that must be repeated on each machine.</span></span>

## <a name="high-level-steps"></a><span data-ttu-id="5b52f-106">Pasos de alto nivel:</span><span class="sxs-lookup"><span data-stu-id="5b52f-106">High Level Steps:</span></span>
1.  <span data-ttu-id="5b52f-107">Copie los módulos (con funcionalidades de rol) en cada nodo.</span><span class="sxs-lookup"><span data-stu-id="5b52f-107">Copy your modules (with Role Capabilities) to each node.</span></span>
2.  <span data-ttu-id="5b52f-108">Copie los archivos de configuración de sesión en cada nodo.</span><span class="sxs-lookup"><span data-stu-id="5b52f-108">Copy your session configuration files to each node.</span></span>
3.  <span data-ttu-id="5b52f-109">Ejecute `Register-PSSessionConfiguration` con la configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="5b52f-109">Run `Register-PSSessionConfiguration` with your session configuration.</span></span>
4.  <span data-ttu-id="5b52f-110">Conserve una copia de la configuración de sesión y de los kits de herramientas en una ubicación segura.</span><span class="sxs-lookup"><span data-stu-id="5b52f-110">Keep a copy of your session configuration and toolkits in a secure location.</span></span>
<span data-ttu-id="5b52f-111">Como realizará modificaciones, es conveniente tener un "origen único de verdad."</span><span class="sxs-lookup"><span data-stu-id="5b52f-111">As you make modifications, it's good to have a "single source of truth."</span></span>

## <a name="example-script"></a><span data-ttu-id="5b52f-112">Script de ejemplo</span><span class="sxs-lookup"><span data-stu-id="5b52f-112">Example Script</span></span>
<span data-ttu-id="5b52f-113">A continuación se muestra un script de ejemplo para la implementación.</span><span class="sxs-lookup"><span data-stu-id="5b52f-113">Here's an example script for deployment.</span></span>
<span data-ttu-id="5b52f-114">Para usarlo en su entorno, deberá usar los nombres o las rutas de acceso de recursos compartidos de archivos y módulos reales.</span><span class="sxs-lookup"><span data-stu-id="5b52f-114">To use it in your environment, you'll have to use the names/paths of real file shares and modules.</span></span>
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## <a name="modifying-capabilities"></a><span data-ttu-id="5b52f-115">Modificar funcionalidades</span><span class="sxs-lookup"><span data-stu-id="5b52f-115">Modifying Capabilities</span></span>
<span data-ttu-id="5b52f-116">Cuando se trabaja con varias máquinas, es importante que las modificaciones se implementen de forma coherente.</span><span class="sxs-lookup"><span data-stu-id="5b52f-116">When dealing with many machines, it's important that modifications are rolled out in a consistent manner.</span></span>
<span data-ttu-id="5b52f-117">Una vez que JEA tenga un recurso de DSC, podrá asegurarse más fácilmente de que el entorno esté sincronizado.</span><span class="sxs-lookup"><span data-stu-id="5b52f-117">Once JEA has a DSC Resource, this will help ensure your environment is in sync.</span></span>
<span data-ttu-id="5b52f-118">Hasta ese momento, se recomienda que conserve una copia maestra de las configuraciones de sesión y que vuelva a implementarla cada vez que realice una modificación.</span><span class="sxs-lookup"><span data-stu-id="5b52f-118">Until that time, we highly recommend you keep a master copy of your session configurations and re-deploy each time you make a modification.</span></span>

## <a name="removing-capabilities"></a><span data-ttu-id="5b52f-119">Quitar funcionalidades</span><span class="sxs-lookup"><span data-stu-id="5b52f-119">Removing Capabilities</span></span>
<span data-ttu-id="5b52f-120">Para quitar la configuración de JEA de sus sistemas, use el comando siguiente en cada máquina:</span><span class="sxs-lookup"><span data-stu-id="5b52f-120">To remove your JEA configuration from your systems, use the following command on each machine:</span></span>
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```

