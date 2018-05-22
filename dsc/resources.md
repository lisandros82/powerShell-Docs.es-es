---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="4070e-103">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="4070e-103">DSC Resources</span></span>

><span data-ttu-id="4070e-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4070e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="4070e-105">Los recursos de la configuración de estado deseado (DSC) ofrecen los bloques de creación para una configuración DSC.</span><span class="sxs-lookup"><span data-stu-id="4070e-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="4070e-106">Un recurso expone las propiedades que se pueden configurar (el esquema) y contiene las funciones de script de PowerShell a las que el administrador de configuración local (LCM) llama para "que sea así".</span><span class="sxs-lookup"><span data-stu-id="4070e-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="4070e-107">Un recurso puede modelar algo tan genérico como un archivo o tan específico como una configuración de servidor IIS.</span><span class="sxs-lookup"><span data-stu-id="4070e-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="4070e-108">Grupos de recursos similares se combinan en un módulo de DSC, que organiza todos los archivos necesarios en una estructura portátil que incluye los metadatos para identificar cómo están diseñados para usarse los recursos.</span><span class="sxs-lookup"><span data-stu-id="4070e-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="4070e-109">En los temas siguientes se describen los recursos de DSC:</span><span class="sxs-lookup"><span data-stu-id="4070e-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="4070e-110">Recursos de DSC integrados</span><span class="sxs-lookup"><span data-stu-id="4070e-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="4070e-111">Crear recursos de DSC personalizados</span><span class="sxs-lookup"><span data-stu-id="4070e-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="4070e-112">Recursos de DSC integrados para Linux</span><span class="sxs-lookup"><span data-stu-id="4070e-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)