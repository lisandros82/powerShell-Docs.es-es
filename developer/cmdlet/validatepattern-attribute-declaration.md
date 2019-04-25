---
title: Declaración de atributo ValidatePattern | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067134"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="b2991-102">Declaración de atributo ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="b2991-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="b2991-103">El atributo ValidatePattern especifica un patrón de expresión regular que valide el argumento de un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2991-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="b2991-104">Este atributo también se puede usar las funciones de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2991-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="b2991-105">Cuando se invoca ValidatePattern dentro de un cmdlet, el tiempo de ejecución de Windows PowerShell convierte el argumento del parámetro de cmdlet en una cadena y, a continuación, compara dicha cadena en el patrón proporcionado por el atributo ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="b2991-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="b2991-106">El cmdlet se ejecuta solo si coincide con la representación de cadena convertida del argumento y el patrón proporcionado.</span><span class="sxs-lookup"><span data-stu-id="b2991-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="b2991-107">Si no coinciden, se produce un error por el tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2991-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2991-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b2991-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="b2991-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b2991-109">Parameters</span></span>

<span data-ttu-id="b2991-110">`RegexString` ([System.String](/dotnet/api/System.String)) necesarios.</span><span class="sxs-lookup"><span data-stu-id="b2991-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="b2991-111">Especifica una expresión regular que valide el argumento del parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2991-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="b2991-112">Opciones ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) con el nombre de parámetro opcional.</span><span class="sxs-lookup"><span data-stu-id="b2991-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="b2991-113">Especifica una combinación bit a bit de [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) marcadores que especifican opciones de expresiones regulares.</span><span class="sxs-lookup"><span data-stu-id="b2991-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2991-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b2991-114">Remarks</span></span>

- <span data-ttu-id="b2991-115">Este atributo se puede usar una sola vez por cada parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2991-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="b2991-116">Puede usar el `Option` parámetro del atributo para definir el modelo.</span><span class="sxs-lookup"><span data-stu-id="b2991-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="b2991-117">Por ejemplo, puede hacer que el modelo distingue mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="b2991-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="b2991-118">Si este atributo se aplica a una colección, cada elemento de la colección debe coincidir con el patrón.</span><span class="sxs-lookup"><span data-stu-id="b2991-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="b2991-119">El atributo ValidatePattern está definido por el [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) clase.</span><span class="sxs-lookup"><span data-stu-id="b2991-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2991-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="b2991-120">See Also</span></span>

[<span data-ttu-id="b2991-121">System.Management.Automation.Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="b2991-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="b2991-122">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2991-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
