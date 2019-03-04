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
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853921"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="f2fe0-102">Atributos del cmdlet</span><span class="sxs-lookup"><span data-stu-id="f2fe0-102">Cmdlet Attributes</span></span>

<span data-ttu-id="f2fe0-103">Windows PowerShell define varios atributos que puede usar para agregar funcionalidad común a los cmdlets sin necesidad de implementar esa funcionalidad dentro de su propio código.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="f2fe0-104">Esto incluye el atributo de Cmdlet que identifica una clase de Microsoft .NET Framework como una clase de cmdlet, el atributo OutputType que especifica los tipos de .NET Framework devueltos por el cmdlet, el atributo de parámetro que identifica las propiedades públicas como el cmdlet los parámetros y mucho más.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f2fe0-105">En esta sección</span><span class="sxs-lookup"><span data-stu-id="f2fe0-105">In This Section</span></span>

<span data-ttu-id="f2fe0-106">[Atributos en el código del Cmdlet](./attributes-in-cmdlet-code.md) describe la ventaja de uso de atributos en el código del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="f2fe0-107">[Tipos de atributo](./attribute-types.md) se describen los atributos diferentes que pueden decorar una clase de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="f2fe0-108">[La declaración de atributo alias](./alias-attribute-declaration.md) se describe cómo definir los alias para un nombre de parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="f2fe0-109">[Declaración de atributo de cmdlet](./cmdlet-attribute-declaration.md) se describe cómo definir una clase de .NET Framework como un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="f2fe0-110">[Declaración de atributo de credenciales](./credential-attribute-declaration.md) se describe cómo agregar compatibilidad para convertir la entrada de cadena en un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="f2fe0-111">[Atributo OutputType declaración](./outputtype-attribute-declaration.md) describe cómo especificar los tipos de .NET Framework devueltos por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="f2fe0-112">[Declaración de atributo de parámetro](./parameter-attribute-declaration.md) se describe cómo definir los parámetros de un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="f2fe0-113">[Declaración de atributo ValidateCount](./validatecount-attribute-declaration.md) se describe cómo definir cuántos argumentos están permitidos para un parámetro.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="f2fe0-114">[Declaración de atributo ValidateLength](./validatelength-attribute-declaration.md) se describe cómo definir la longitud (en caracteres) de un argumento de parámetro.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="f2fe0-115">[Declaración de atributo ValidatePattern](./validatepattern-attribute-declaration.md) se describe cómo definir los patrones válidos para un argumento de parámetro.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="f2fe0-116">[Declaración de atributo ValidateRange](./validaterange-attribute-declaration.md) se describe cómo definir el intervalo válido para un argumento de parámetro.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="f2fe0-117">[Declaración de atributo ValidateSet](./validateset-attribute-declaration.md) se describe cómo definir los valores posibles para un argumento de parámetro.</span><span class="sxs-lookup"><span data-stu-id="f2fe0-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="f2fe0-118">Referencia</span><span class="sxs-lookup"><span data-stu-id="f2fe0-118">Reference</span></span>

[<span data-ttu-id="f2fe0-119">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2fe0-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
