---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC
ms.openlocfilehash: 62bf352b929d661e585e145e5aab0f44f13010a1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-resources"></a><span data-ttu-id="89392-103">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="89392-103">DSC Resources</span></span>

><span data-ttu-id="89392-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="89392-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="89392-105">Los recursos de la configuración de estado deseado (DSC) ofrecen los bloques de creación para una configuración DSC.</span><span class="sxs-lookup"><span data-stu-id="89392-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="89392-106">Un recurso expone las propiedades que se pueden configurar (el esquema) y contiene las funciones de script de PowerShell a las que el administrador de configuración local (LCM) llama para "que sea así".</span><span class="sxs-lookup"><span data-stu-id="89392-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="89392-107">Un recurso puede modelar algo tan genérico como un archivo o tan específico como una configuración de servidor IIS.</span><span class="sxs-lookup"><span data-stu-id="89392-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="89392-108">Grupos de recursos similares se combinan en un módulo de DSC, que organiza todos los archivos necesarios en una estructura portátil que incluye los metadatos para identificar cómo están diseñados para usarse los recursos.</span><span class="sxs-lookup"><span data-stu-id="89392-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>  

<span data-ttu-id="89392-109">En los temas siguientes se describen los recursos de DSC:</span><span class="sxs-lookup"><span data-stu-id="89392-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="89392-110">Recursos de DSC integrados</span><span class="sxs-lookup"><span data-stu-id="89392-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="89392-111">Crear recursos de DSC personalizados</span><span class="sxs-lookup"><span data-stu-id="89392-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="89392-112">Recursos de DSC integrados para Linux</span><span class="sxs-lookup"><span data-stu-id="89392-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)

