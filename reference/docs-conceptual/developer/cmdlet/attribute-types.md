---
title: Tipos de atributos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364584"
---
# <a name="attribute-types"></a><span data-ttu-id="ca2f1-102">Tipos de atributo</span><span class="sxs-lookup"><span data-stu-id="ca2f1-102">Attribute Types</span></span>

<span data-ttu-id="ca2f1-103">Los atributos de cmdlet se pueden agrupar por funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="ca2f1-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="ca2f1-104">En las secciones siguientes se describen los atributos disponibles y se describe lo que hace el motor en tiempo de ejecución cuando se invoca el atributo.</span><span class="sxs-lookup"><span data-stu-id="ca2f1-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="ca2f1-105">Atributos del cmdlet</span><span class="sxs-lookup"><span data-stu-id="ca2f1-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="ca2f1-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ca2f1-106">Cmdlet</span></span>

<span data-ttu-id="ca2f1-107">Identifica una clase .NET Framework como un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca2f1-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="ca2f1-108">Este es el atributo base necesario.</span><span class="sxs-lookup"><span data-stu-id="ca2f1-108">This is the required base attribute.</span></span>
<span data-ttu-id="ca2f1-109">Para obtener más información, vea [declaración de atributos de cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ca2f1-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="ca2f1-110">Atributos de parámetro</span><span class="sxs-lookup"><span data-stu-id="ca2f1-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="ca2f1-111">Parámetro</span><span class="sxs-lookup"><span data-stu-id="ca2f1-111">Parameter</span></span>

<span data-ttu-id="ca2f1-112">Identifica una propiedad pública de la clase de cmdlet como un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca2f1-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="ca2f1-113">Para obtener más información, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ca2f1-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="ca2f1-114">Alias</span><span class="sxs-lookup"><span data-stu-id="ca2f1-114">Alias</span></span>

<span data-ttu-id="ca2f1-115">Especifica uno o varios alias para un parámetro.</span><span class="sxs-lookup"><span data-stu-id="ca2f1-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="ca2f1-116">Para obtener más información, vea [declaración de atributo de alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ca2f1-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="ca2f1-117">Atributos de validación de argumentos</span><span class="sxs-lookup"><span data-stu-id="ca2f1-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="ca2f1-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="ca2f1-118">ValidateCount</span></span>

<span data-ttu-id="ca2f1-119">Especifica el número mínimo y máximo de argumentos permitidos para un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca2f1-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="ca2f1-120">Para obtener más información, vea [declaración de atributos de ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ca2f1-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="ca2f1-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="ca2f1-121">ValidateLength</span></span>

<span data-ttu-id="ca2f1-122">Especifica un número mínimo y máximo de caracteres para un argumento de parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca2f1-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="ca2f1-123">Para obtener más información, vea [declaración de atributos de ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ca2f1-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="ca2f1-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="ca2f1-124">ValidatePattern</span></span>

<span data-ttu-id="ca2f1-125">Especifica un patrón de expresión regular que el argumento de parámetro de cmdlet debe coincidir.</span><span class="sxs-lookup"><span data-stu-id="ca2f1-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="ca2f1-126">Para obtener más información, vea [declaración de atributos de ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ca2f1-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="ca2f1-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="ca2f1-127">ValidateRange</span></span>

<span data-ttu-id="ca2f1-128">Especifica los valores mínimo y máximo para un argumento de parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca2f1-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="ca2f1-129">Para obtener más información, vea [declaración de atributos de ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ca2f1-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="ca2f1-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="ca2f1-130">ValidateSet</span></span>

<span data-ttu-id="ca2f1-131">Especifica un conjunto de valores válidos para el argumento del parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca2f1-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="ca2f1-132">Para obtener más información, vea [declaración de atributos de ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ca2f1-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca2f1-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="ca2f1-133">See Also</span></span>

[<span data-ttu-id="ca2f1-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ca2f1-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
