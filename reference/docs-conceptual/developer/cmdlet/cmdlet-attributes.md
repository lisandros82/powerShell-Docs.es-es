---
title: Atributos de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369964"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="0f276-102">Atributos del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0f276-102">Cmdlet Attributes</span></span>

<span data-ttu-id="0f276-103">Windows PowerShell define varios atributos que puede usar para agregar una funcionalidad común a los cmdlets sin necesidad de implementar esa funcionalidad en su propio código.</span><span class="sxs-lookup"><span data-stu-id="0f276-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="0f276-104">Esto incluye el atributo de cmdlet que identifica una clase de Microsoft .NET Framework como una clase de cmdlet, el atributo OutputType que especifica los tipos de .NET Framework devueltos por el cmdlet, el atributo Parameter que identifica las propiedades públicas como cmdlet y mucho más.</span><span class="sxs-lookup"><span data-stu-id="0f276-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0f276-105">En esta sección</span><span class="sxs-lookup"><span data-stu-id="0f276-105">In This Section</span></span>

<span data-ttu-id="0f276-106">[Atributos del código de cmdlet](./attributes-in-cmdlet-code.md) Describe la ventaja de usar atributos en el código del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0f276-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="0f276-107">[Tipos de atributos](./attribute-types.md) Describe los diferentes atributos que pueden decorar una clase de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0f276-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="0f276-108">[Declaración de atributo de alias](./alias-attribute-declaration.md) Describe cómo definir alias para un nombre de parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0f276-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="0f276-109">[Declaración de atributo de cmdlet](./cmdlet-attribute-declaration.md) Describe cómo definir una clase .NET Framework como un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0f276-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="0f276-110">[Declaración de atributos de credenciales](./credential-attribute-declaration.md) Describe cómo agregar compatibilidad para convertir la entrada de cadena en un objeto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) .</span><span class="sxs-lookup"><span data-stu-id="0f276-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="0f276-111">[OutputType (declaración de atributo](./outputtype-attribute-declaration.md) ) Describe cómo especificar los tipos de .NET Framework devueltos por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0f276-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="0f276-112">[Declaración de atributo de parámetro](./parameter-attribute-declaration.md) Describe cómo definir los parámetros de un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0f276-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="0f276-113">[Declaración de atributos de ValidateCount](./validatecount-attribute-declaration.md) Describe cómo definir el número de argumentos permitidos para un parámetro.</span><span class="sxs-lookup"><span data-stu-id="0f276-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="0f276-114">[Declaración de atributos de ValidateLength](./validatelength-attribute-declaration.md) Describe cómo definir la longitud (en caracteres) de un argumento de parámetro.</span><span class="sxs-lookup"><span data-stu-id="0f276-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="0f276-115">[Declaración de atributos de ValidatePattern](./validatepattern-attribute-declaration.md) Describe cómo definir los patrones válidos para un argumento de parámetro.</span><span class="sxs-lookup"><span data-stu-id="0f276-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="0f276-116">[Declaración de atributos de ValidateRange](./validaterange-attribute-declaration.md) Describe cómo definir el intervalo válido para un argumento de parámetro.</span><span class="sxs-lookup"><span data-stu-id="0f276-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="0f276-117">[Declaración de atributos de ValidateSet](./validateset-attribute-declaration.md) Describe cómo definir los valores posibles para un argumento de parámetro.</span><span class="sxs-lookup"><span data-stu-id="0f276-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="0f276-118">Referencia</span><span class="sxs-lookup"><span data-stu-id="0f276-118">Reference</span></span>

[<span data-ttu-id="0f276-119">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f276-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
