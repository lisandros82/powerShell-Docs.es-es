---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Introducción a la configuración de estado deseado de PowerShell
ms.openlocfilehash: b5aff5008db5a5e45b77d8094b0e48ad98dc63fa
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="77e27-103">Introducción a la configuración de estado deseado de PowerShell</span><span class="sxs-lookup"><span data-stu-id="77e27-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="77e27-104">En esta guía se describe cómo empezar a crear documentos de configuración de estado deseado de PowerShell y aplicarlos a las máquinas.</span><span class="sxs-lookup"><span data-stu-id="77e27-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="77e27-105">Supone una familiarización básica con los cmdlets, módulos y funciones de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77e27-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span>


## <a name="create-a-configuration"></a><span data-ttu-id="77e27-106">Crear una configuración</span><span class="sxs-lookup"><span data-stu-id="77e27-106">Create a Configuration</span></span> ##

<span data-ttu-id="77e27-107">Las [**configuraciones**](https://msdn.microsoft.com/powershell/dsc/configurations) son documentos que describen un entorno.</span><span class="sxs-lookup"><span data-stu-id="77e27-107">[**Configurations**](https://msdn.microsoft.com/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="77e27-108">Los entornos constan de elementos "**nodo**", que normalmente son máquinas físicas o virtuales.</span><span class="sxs-lookup"><span data-stu-id="77e27-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span>

<span data-ttu-id="77e27-109">Las configuraciones pueden presentarse de diversas formas.</span><span class="sxs-lookup"><span data-stu-id="77e27-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="77e27-110">La manera más fácil de crear una nueva configuración es crear un archivo .ps1 (script de PowerShell).</span><span class="sxs-lookup"><span data-stu-id="77e27-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="77e27-111">Para hacerlo, abra el editor que prefiera.</span><span class="sxs-lookup"><span data-stu-id="77e27-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="77e27-112">PowerShell ISE es una buena opción, ya que entiende DSC de forma nativa.</span><span class="sxs-lookup"><span data-stu-id="77e27-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="77e27-113">Guarde lo siguiente como un archivo PS1:</span><span class="sxs-lookup"><span data-stu-id="77e27-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }

    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="77e27-114">Partes de una configuración</span><span class="sxs-lookup"><span data-stu-id="77e27-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="77e27-115">**Configuration** es una palabra clave que se agregó a PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="77e27-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="77e27-116">Indica un tipo especial de función de PowerShell que utiliza la configuración de estado deseado.</span><span class="sxs-lookup"><span data-stu-id="77e27-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="77e27-117">En este ejemplo, la función se denomina myFirstConfiguration.</span><span class="sxs-lookup"><span data-stu-id="77e27-117">In this example, the function is named myFirstConfiguration.</span></span>

<span data-ttu-id="77e27-118">La siguiente línea es una instrucción import, similar a la importación de un módulo.</span><span class="sxs-lookup"><span data-stu-id="77e27-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="77e27-119">Se explicará más adelante.</span><span class="sxs-lookup"><span data-stu-id="77e27-119">It will be discussed later on.</span></span>

<span data-ttu-id="77e27-120">"Node" define el nombre de la máquina en que actuará esta configuración.</span><span class="sxs-lookup"><span data-stu-id="77e27-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="77e27-121">Aunque esta configuración se modifica localmente, las configuraciones pueden llegar a los nodos remotos y configurarlos.</span><span class="sxs-lookup"><span data-stu-id="77e27-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span>

<span data-ttu-id="77e27-122">Los nodos pueden ser los nombres de máquinas o direcciones IP.</span><span class="sxs-lookup"><span data-stu-id="77e27-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="77e27-123">Puede tener varios nodos en un documento de configuración único.</span><span class="sxs-lookup"><span data-stu-id="77e27-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="77e27-124">Mediante [datos de configuración](https://msdn.microsoft.com/powershell/dsc/configdata), también puede hacer que se aplique la misma configuración a varios nodos.</span><span class="sxs-lookup"><span data-stu-id="77e27-124">Using [configuration data](https://msdn.microsoft.com/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="77e27-125">En este caso, el nodo es "localhost", que significa el equipo local.</span><span class="sxs-lookup"><span data-stu-id="77e27-125">In this case, the node is "localhost" - which means the local computer.</span></span>

<span data-ttu-id="77e27-126">El elemento siguiente es un [**recurso**](https://msdn.microsoft.com/powershell/dsc/resources).</span><span class="sxs-lookup"><span data-stu-id="77e27-126">The next item is a [**resource**](https://msdn.microsoft.com/powershell/dsc/resources).</span></span> <span data-ttu-id="77e27-127">Los recursos son bloques de creación de configuraciones.</span><span class="sxs-lookup"><span data-stu-id="77e27-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="77e27-128">Cada recurso es un módulo que define la lógica de implementación de un único aspecto de una máquina.</span><span class="sxs-lookup"><span data-stu-id="77e27-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="77e27-129">Puede ver todos los recursos en su máquina si ejecuta **Get-DscResource** en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77e27-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="77e27-130">Los recursos deben estar presentes en la máquina local y haberse importado antes de que se puedan utilizar en una configuración con **Import-DscResource**, que se encuentra en la segunda línea de esta configuración.</span><span class="sxs-lookup"><span data-stu-id="77e27-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span>

<span data-ttu-id="77e27-131">**Establecer una configuración**</span><span class="sxs-lookup"><span data-stu-id="77e27-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="77e27-132">Si el script anterior se guarda y se ejecuta, no se producirá ningún resultado.</span><span class="sxs-lookup"><span data-stu-id="77e27-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="77e27-133">Esto se debe a que una configuración es simplemente una función y el script anterior ha definido la función, pero aún no la ha ejecutado.</span><span class="sxs-lookup"><span data-stu-id="77e27-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="77e27-134">Después de definir la función, se debe invocar:</span><span class="sxs-lookup"><span data-stu-id="77e27-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="77e27-135">Cuando se ejecuta, las funciones de configuración validan que la configuración sea válida.</span><span class="sxs-lookup"><span data-stu-id="77e27-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="77e27-136">No debe tener errores de sintaxis, los recursos deben tener todos los parámetros obligatorios definidos y todos los recursos deben importarse antes de la ejecución.</span><span class="sxs-lookup"><span data-stu-id="77e27-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="77e27-137">Cuando se ejecuta la configuración, crea una carpeta con el nombre de la configuración que contiene un **archivo .MOF** para cada uno de los nodos de la configuración.</span><span class="sxs-lookup"><span data-stu-id="77e27-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="77e27-138">El archivo .MOF es un formato de administración basado en estándares que utiliza la DSC de PowerShell para comunicarse a través de la red.</span><span class="sxs-lookup"><span data-stu-id="77e27-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="77e27-139">Para establecer la configuración:</span><span class="sxs-lookup"><span data-stu-id="77e27-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="77e27-140">Esto crea un trabajo de PowerShell que llega a los nodos de la configuración y los configura.</span><span class="sxs-lookup"><span data-stu-id="77e27-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="77e27-141">Para ver la salida del trabajo, use -Wait.</span><span class="sxs-lookup"><span data-stu-id="77e27-141">To see the output of the job, use -Wait.</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```