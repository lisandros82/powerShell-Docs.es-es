---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Uso de recursos con varias versiones
ms.openlocfilehash: 6400d6506106657ba28fa1f9c83d9f8ee1c93ba3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187017"
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="4d1c3-103">Uso de recursos con varias versiones</span><span class="sxs-lookup"><span data-stu-id="4d1c3-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="4d1c3-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4d1c3-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4d1c3-105">En PowerShell 5.0, los recursos de DSC pueden tener varias versiones, y las versiones pueden instalarse en un equipo en paralelo.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="4d1c3-106">Esto se implementa mediante varias versiones de un módulo de recursos que están contenidas en la misma carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="4d1c3-107">Instalación de varias versiones de recursos en paralelo</span><span class="sxs-lookup"><span data-stu-id="4d1c3-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="4d1c3-108">Puede usar los parámetros **MinimumVersion**, **MaximumVersion** y **RequiredVersion** del cmdlet [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) para especificar la versión de un módulo que se va a instalar.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="4d1c3-109">Llamar a **Install-Module** sin especificar una versión instala la versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="4d1c3-110">Por ejemplo, hay varias versiones del módulo **xFailOverCluster**, cada una de las cuales contiene un recurso **xCluster**.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="4d1c3-111">El resultado de llamar a **Install-Module** sin especificar el número de versión es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="4d1c3-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="4d1c3-112">Ahora, si se vuelve a llamar a **Install-Module**, pero se especifica una **RequiredVersion** de 1.1.0.0, se obtiene el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="4d1c3-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="4d1c3-113">Especificación de una versión de recursos en una configuración</span><span class="sxs-lookup"><span data-stu-id="4d1c3-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="4d1c3-114">Si tiene varios recursos instalados en un equipo, debe especificar la versión de ese recurso cuando lo usa en una configuración.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="4d1c3-115">Esto se hace mediante la especificación del parámetro **ModuleVersion** de la palabra clave **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="4d1c3-116">Si tiene instaladas varias versiones de un recurso y no especifica la versión del módulo de recursos que quiere usar, la configuración generará un error.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="4d1c3-117">La configuración siguiente muestra cómo especificar la versión del recurso al que se va a llamar:</span><span class="sxs-lookup"><span data-stu-id="4d1c3-117">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

><span data-ttu-id="4d1c3-118">Nota: el parámetro ModuleVersion de Import-DscResource no está disponible en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="4d1c3-119">En PowerShell 4.0, puede especificar una versión de módulo pasando un objeto de especificación de módulo al parámetro ModuleName de Import-DscResource.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="4d1c3-120">Un objeto de especificación de módulo es una tabla hash que contiene las claves ModuleName y RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="4d1c3-121">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4d1c3-121">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

<span data-ttu-id="4d1c3-122">Esto también funcionará en PowerShell 5.0, pero se recomienda que use el parámetro **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d1c3-123">Vea también</span><span class="sxs-lookup"><span data-stu-id="4d1c3-123">See also</span></span>
* [<span data-ttu-id="4d1c3-124">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="4d1c3-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="4d1c3-125">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="4d1c3-125">DSC Resources</span></span>](resources.md)