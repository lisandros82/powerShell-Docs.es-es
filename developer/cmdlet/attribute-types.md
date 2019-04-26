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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068668"
---
# <a name="attribute-types"></a><span data-ttu-id="8d205-102">Tipos de atributo</span><span class="sxs-lookup"><span data-stu-id="8d205-102">Attribute Types</span></span>

<span data-ttu-id="8d205-103">Atributos de cmdlet se pueden agrupar según su funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="8d205-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="8d205-104">Las siguientes secciones describen los atributos disponibles y describen lo que hace el tiempo de ejecución cuando se invoca el atributo.</span><span class="sxs-lookup"><span data-stu-id="8d205-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="8d205-105">Atributos del cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d205-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="8d205-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d205-106">Cmdlet</span></span>

<span data-ttu-id="8d205-107">Identifica una clase de .NET Framework como un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d205-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="8d205-108">Este es el atributo base necesario.</span><span class="sxs-lookup"><span data-stu-id="8d205-108">This is the required base attribute.</span></span>
<span data-ttu-id="8d205-109">Para obtener más información, consulte [declaración de atributo de Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8d205-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="8d205-110">Atributos de parámetro</span><span class="sxs-lookup"><span data-stu-id="8d205-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="8d205-111">Parámetro</span><span class="sxs-lookup"><span data-stu-id="8d205-111">Parameter</span></span>

<span data-ttu-id="8d205-112">Identifica una propiedad pública de la clase de cmdlet como un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d205-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="8d205-113">Para obtener más información, consulte [declaración de atributo de parámetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8d205-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="8d205-114">Alias</span><span class="sxs-lookup"><span data-stu-id="8d205-114">Alias</span></span>

<span data-ttu-id="8d205-115">Especifica uno o varios alias para un parámetro.</span><span class="sxs-lookup"><span data-stu-id="8d205-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="8d205-116">Para obtener más información, consulte [la declaración de atributo Alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8d205-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="8d205-117">Atributos de validación de argumento</span><span class="sxs-lookup"><span data-stu-id="8d205-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="8d205-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="8d205-118">ValidateCount</span></span>

<span data-ttu-id="8d205-119">Especifica el número mínimo y máximo de argumentos que se permiten para un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d205-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="8d205-120">Para obtener más información, consulte [ValidateCount la declaración de atributo](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8d205-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="8d205-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="8d205-121">ValidateLength</span></span>

<span data-ttu-id="8d205-122">Especifica un número mínimo y máximo de caracteres para un argumento de parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d205-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="8d205-123">Para obtener más información, consulte [declaración de atributo ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8d205-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="8d205-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="8d205-124">ValidatePattern</span></span>

<span data-ttu-id="8d205-125">Especifica un patrón de expresión regular que debe coincidir con el argumento del parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d205-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="8d205-126">Para obtener más información, consulte [ValidatePattern la declaración de atributo](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8d205-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="8d205-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="8d205-127">ValidateRange</span></span>

<span data-ttu-id="8d205-128">Especifica los valores mínimos y máximo para un argumento de parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d205-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="8d205-129">Para obtener más información, consulte [ValidateRange la declaración de atributo](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8d205-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="8d205-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="8d205-130">ValidateSet</span></span>

<span data-ttu-id="8d205-131">Especifica un conjunto de valores válidos para el argumento del parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d205-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="8d205-132">Para obtener más información, consulte [ValidateSet la declaración de atributo](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8d205-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d205-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="8d205-133">See Also</span></span>

[<span data-ttu-id="8d205-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8d205-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
