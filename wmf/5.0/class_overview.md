---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 7eaa4dfb68bc299ad31bce81af96b6a760c4fcc5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="a7040-102">Creación de tipos personalizados mediante clases de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7040-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="a7040-103">Hemos mejorado el lenguaje de PowerShell para la definición de clases y otros tipos definidos por el usuario mediante sintaxis y semántica formales similares a las de otros lenguajes de programación orientados a objetos.</span><span class="sxs-lookup"><span data-stu-id="a7040-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="a7040-104">El objetivo es permitir a los desarrolladores y profesionales de TI adoptar PowerShell para una gama más amplia de casos de uso, simplificar el desarrollo de artefactos de PowerShell (como recursos de DSC) y acelerar la cobertura de las superficies de administración.</span><span class="sxs-lookup"><span data-stu-id="a7040-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="a7040-105">Escenarios admitidos en esta versión</span><span class="sxs-lookup"><span data-stu-id="a7040-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="a7040-106">Definición de recursos de DSC y sus tipos asociados mediante el lenguaje de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7040-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="a7040-107">Definición de tipos personalizados en PowerShell mediante construcciones de programación conocidas orientadas a objetos, tales como clases, propiedades, métodos, etc.</span><span class="sxs-lookup"><span data-stu-id="a7040-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="a7040-108">Compatibilidad de herencia con la clase de PowerShell y el recurso de DSC basado en la clase.</span><span class="sxs-lookup"><span data-stu-id="a7040-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="a7040-109">Depuración de tipos mediante el lenguaje de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7040-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="a7040-110">Generación y control de excepciones mediante mecanismos formales y en el nivel correcto.</span><span class="sxs-lookup"><span data-stu-id="a7040-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>