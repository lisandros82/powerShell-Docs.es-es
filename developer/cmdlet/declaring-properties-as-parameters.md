---
title: Declarar propiedades como parámetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861381"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="69b3d-102">Declaración de propiedades como parámetros</span><span class="sxs-lookup"><span data-stu-id="69b3d-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="69b3d-103">En este tema se proporciona información básica que debe comprender antes de declarar los parámetros de un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="69b3d-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="69b3d-104">Para declarar los parámetros de un cmdlet dentro de la clase de cmdlet, definir las propiedades públicas que representan cada parámetro y, a continuación, agregue uno o varios atributos de parámetro para cada propiedad.</span><span class="sxs-lookup"><span data-stu-id="69b3d-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="69b3d-105">El tiempo de ejecución de Windows PowerShell usa los atributos de parámetro para identificar la propiedad como un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="69b3d-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="69b3d-106">La sintaxis básica para declarar el atributo de parámetro es `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="69b3d-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="69b3d-107">Este es un ejemplo de una propiedad definida como un parámetro necesario.</span><span class="sxs-lookup"><span data-stu-id="69b3d-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="69b3d-108">Estas son algunas cosas que recordar acerca de los parámetros.</span><span class="sxs-lookup"><span data-stu-id="69b3d-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="69b3d-109">Un parámetro debe marcarse explícitamente como público.</span><span class="sxs-lookup"><span data-stu-id="69b3d-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="69b3d-110">Parámetros que no están marcados como público predeterminado para interno y no se encontrará el tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69b3d-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="69b3d-111">Los parámetros deben definirse como tipos de Microsoft .NET Framework para proporcionar una mejor validación de parámetros.</span><span class="sxs-lookup"><span data-stu-id="69b3d-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="69b3d-112">Por ejemplo, los parámetros que están restringidos a un valor fuera de un conjunto de valores deben definirse como un tipo de enumeración.</span><span class="sxs-lookup"><span data-stu-id="69b3d-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="69b3d-113">Parámetros que toman un valor de identificador uniforme de recursos (URI) deben ser del tipo [System.Uri](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="69b3d-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="69b3d-114">Evite los parámetros de cadena básicas de las propiedades de todos excepto texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="69b3d-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="69b3d-115">Puede agregar un parámetro a cualquier número de conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="69b3d-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="69b3d-116">Para obtener más información acerca de conjuntos de parámetros, vea [conjuntos de parámetros de Cmdlet](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="69b3d-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="69b3d-117">Windows PowerShell también proporciona un conjunto de parámetros comunes que están disponibles para todos los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="69b3d-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="69b3d-118">Para obtener más información sobre estos parámetros y sus alias, vea [parámetros comunes de Cmdlet](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="69b3d-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="69b3d-119">Véase también</span><span class="sxs-lookup"><span data-stu-id="69b3d-119">See Also</span></span>

[<span data-ttu-id="69b3d-120">Parámetros comunes de cmdlet</span><span class="sxs-lookup"><span data-stu-id="69b3d-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="69b3d-121">Tipos de parámetro de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69b3d-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="69b3d-122">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="69b3d-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
