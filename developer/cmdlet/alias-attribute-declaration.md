---
title: La declaración de atributo alias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855051"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="373e5-102">Declaración de atributo de alias</span><span class="sxs-lookup"><span data-stu-id="373e5-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="373e5-103">Alias (atributo) permite al usuario especificar nombres distintos para un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="373e5-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="373e5-104">Alias pueden utilizarse para proporcionar accesos directos de un nombre de parámetro, o estas pueden proporcionar nombres diferentes que son adecuados para diferentes escenarios.</span><span class="sxs-lookup"><span data-stu-id="373e5-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="373e5-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="373e5-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="373e5-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="373e5-106">Parameters</span></span>

<span data-ttu-id="373e5-107">`aliasName` (String[]) Obligatorio.</span><span class="sxs-lookup"><span data-stu-id="373e5-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="373e5-108">Especifica un conjunto de alias separados por comas de nombres para el parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="373e5-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="373e5-109">Observaciones</span><span class="sxs-lookup"><span data-stu-id="373e5-109">Remarks</span></span>

- <span data-ttu-id="373e5-110">El atributo de Alias se utiliza con el atributo de parámetro cuando se especifica un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="373e5-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="373e5-111">Para obtener más información acerca de cómo declarar estos atributos, vea [cómo declarar los parámetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="373e5-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="373e5-112">Cada nombre de alias debe ser único dentro de un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="373e5-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="373e5-113">Windows PowerShell no comprueba los nombres de alias duplicados.</span><span class="sxs-lookup"><span data-stu-id="373e5-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="373e5-114">El atributo de Alias se usa una vez para cada parámetro en un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="373e5-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="373e5-115">Alias (atributo) se define mediante el [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) clase.</span><span class="sxs-lookup"><span data-stu-id="373e5-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="373e5-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="373e5-116">See Also</span></span>

[<span data-ttu-id="373e5-117">Alias de parámetro</span><span class="sxs-lookup"><span data-stu-id="373e5-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="373e5-118">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="373e5-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
