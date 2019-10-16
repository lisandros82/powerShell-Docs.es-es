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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365754"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="e480b-102">Declaración de propiedades como parámetros</span><span class="sxs-lookup"><span data-stu-id="e480b-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="e480b-103">En este tema se proporciona información básica que debe conocer antes de declarar los parámetros de un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e480b-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="e480b-104">Para declarar los parámetros de un cmdlet dentro de la clase de cmdlet, defina las propiedades públicas que representan cada parámetro y, a continuación, agregue uno o varios atributos de parámetro a cada propiedad.</span><span class="sxs-lookup"><span data-stu-id="e480b-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="e480b-105">El tiempo de ejecución de Windows PowerShell usa los atributos de parámetro para identificar la propiedad como un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e480b-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="e480b-106">La sintaxis básica para declarar el atributo de parámetro es `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="e480b-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="e480b-107">Este es un ejemplo de una propiedad definida como parámetro necesario.</span><span class="sxs-lookup"><span data-stu-id="e480b-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="e480b-108">Estas son algunas de las cosas que debe recordar sobre los parámetros.</span><span class="sxs-lookup"><span data-stu-id="e480b-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="e480b-109">Un parámetro debe marcarse explícitamente como Public.</span><span class="sxs-lookup"><span data-stu-id="e480b-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="e480b-110">Los parámetros que no están marcados como públicos de forma predeterminada son internos y el tiempo de ejecución de Windows PowerShell no los encontrará.</span><span class="sxs-lookup"><span data-stu-id="e480b-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="e480b-111">Los parámetros se deben definir como tipos de Microsoft .NET Framework para proporcionar una mejor validación de parámetros.</span><span class="sxs-lookup"><span data-stu-id="e480b-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="e480b-112">Por ejemplo, los parámetros que están restringidos a un valor de un conjunto de valores deben definirse como un tipo de enumeración.</span><span class="sxs-lookup"><span data-stu-id="e480b-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="e480b-113">Los parámetros que toman un valor de identificador uniforme de recursos (URI) deben ser del tipo [System. Uri](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="e480b-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="e480b-114">Evite los parámetros de cadena básicos para todas las propiedades de texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="e480b-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="e480b-115">Puede Agregar un parámetro a cualquier número de conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="e480b-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="e480b-116">Para obtener más información sobre los conjuntos de parámetros, vea [conjuntos de parámetros de cmdlet](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e480b-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="e480b-117">Windows PowerShell también proporciona un conjunto de parámetros comunes que están disponibles automáticamente para cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e480b-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="e480b-118">Para obtener más información acerca de estos parámetros y sus alias, consulte [parámetros comunes de cmdlet](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="e480b-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e480b-119">Véase también</span><span class="sxs-lookup"><span data-stu-id="e480b-119">See Also</span></span>

[<span data-ttu-id="e480b-120">Parámetros comunes de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e480b-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="e480b-121">Tipos de parámetro de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e480b-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="e480b-122">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e480b-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
