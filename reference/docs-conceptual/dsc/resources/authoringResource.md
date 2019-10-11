---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Crear recursos de configuración de estado deseado de Windows PowerShell personalizados
ms.openlocfilehash: f0f35e8d0083d302f142f2215c9f28fee411eb07
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952852"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="a52e5-103">Crear recursos de configuración de estado deseado de Windows PowerShell personalizados</span><span class="sxs-lookup"><span data-stu-id="a52e5-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="a52e5-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a52e5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a52e5-105">La configuración de estado deseado (DSC) de Windows PowerShell tiene recursos integrados que puede usar para configurar el entorno.</span><span class="sxs-lookup"><span data-stu-id="a52e5-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="a52e5-106">En este tema se ofrece información general sobre el desarrollo de recursos y vínculos a temas con información específica y ejemplos.</span><span class="sxs-lookup"><span data-stu-id="a52e5-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="a52e5-107">Componentes de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="a52e5-107">DSC resource components</span></span>

<span data-ttu-id="a52e5-108">Un recurso de DSC es un módulo de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a52e5-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="a52e5-109">El módulo contiene el esquema (la definición de las propiedades configurables) y la implementación (el código que realiza el trabajo real especificado por una configuración) del recurso.</span><span class="sxs-lookup"><span data-stu-id="a52e5-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="a52e5-110">Un esquema de recursos de DSC se puede definir en un archivo MOF y la implementación se realiza mediante un módulo de script.</span><span class="sxs-lookup"><span data-stu-id="a52e5-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="a52e5-111">A partir de la compatibilidad de las clases de PowerShell de la versión 5, tanto el esquema como la implementación se pueden definir en una clase.</span><span class="sxs-lookup"><span data-stu-id="a52e5-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="a52e5-112">En los temas siguientes se describe con más detalle cómo crear recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="a52e5-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="a52e5-113">Escribir un recurso de DSC personalizado con MOF</span><span class="sxs-lookup"><span data-stu-id="a52e5-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="a52e5-114">Implementación de un recurso de DSC en C#</span><span class="sxs-lookup"><span data-stu-id="a52e5-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="a52e5-115">Escribir un recurso de DSC personalizado con clases de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a52e5-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="a52e5-116">Recursos compuestos: uso de una configuración DSC como un recurso</span><span class="sxs-lookup"><span data-stu-id="a52e5-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="a52e5-117">Uso de la herramienta Diseñador de recursos</span><span class="sxs-lookup"><span data-stu-id="a52e5-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)
