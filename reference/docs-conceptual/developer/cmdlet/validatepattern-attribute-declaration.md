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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369164"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="947b8-102">Declaración de atributo ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="947b8-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="947b8-103">El atributo ValidatePattern especifica un patrón de expresión regular que valida el argumento de un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="947b8-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="947b8-104">Este atributo también se puede usar en las funciones de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="947b8-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="947b8-105">Cuando se invoca ValidatePattern dentro de un cmdlet, el tiempo de ejecución de Windows PowerShell convierte el argumento del parámetro de cmdlet en una cadena y, a continuación, compara esa cadena con el patrón proporcionado por el atributo ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="947b8-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="947b8-106">El cmdlet se ejecuta solo si la representación de cadena convertida del argumento y el patrón proporcionado coinciden.</span><span class="sxs-lookup"><span data-stu-id="947b8-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="947b8-107">Si no coinciden, el tiempo de ejecución de Windows PowerShell produce un error.</span><span class="sxs-lookup"><span data-stu-id="947b8-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="947b8-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="947b8-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="947b8-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="947b8-109">Parameters</span></span>

<span data-ttu-id="947b8-110">se requiere `RegexString` ([System. String](/dotnet/api/System.String)).</span><span class="sxs-lookup"><span data-stu-id="947b8-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="947b8-111">Especifica una expresión regular que valida el argumento del parámetro.</span><span class="sxs-lookup"><span data-stu-id="947b8-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="947b8-112">Options ([System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) opcional parámetro con nombre.</span><span class="sxs-lookup"><span data-stu-id="947b8-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="947b8-113">Especifica una combinación bit a bit de las marcas [System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) que especifican las opciones de expresión regular.</span><span class="sxs-lookup"><span data-stu-id="947b8-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="947b8-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="947b8-114">Remarks</span></span>

- <span data-ttu-id="947b8-115">Este atributo solo se puede usar una vez por parámetro.</span><span class="sxs-lookup"><span data-stu-id="947b8-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="947b8-116">Puede usar el parámetro `Option` del atributo para definir más el modelo.</span><span class="sxs-lookup"><span data-stu-id="947b8-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="947b8-117">Por ejemplo, puede hacer que el patrón distinga mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="947b8-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="947b8-118">Si este atributo se aplica a una colección, cada elemento de la colección debe coincidir con el patrón.</span><span class="sxs-lookup"><span data-stu-id="947b8-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="947b8-119">La clase [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) define el atributo ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="947b8-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="947b8-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="947b8-120">See Also</span></span>

[<span data-ttu-id="947b8-121">System. Management. Automation. Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="947b8-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="947b8-122">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="947b8-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
