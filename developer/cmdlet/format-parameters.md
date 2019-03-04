---
title: Dar formato a los parámetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251190"
---
# <a name="format-parameters"></a><span data-ttu-id="e490d-102">Parámetros de formato</span><span class="sxs-lookup"><span data-stu-id="e490d-102">Format Parameters</span></span>

<span data-ttu-id="e490d-103">En la tabla siguiente enumera los nombres recomendados y la funcionalidad para los parámetros que se usan para dar formato o para generar datos.</span><span class="sxs-lookup"><span data-stu-id="e490d-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="e490d-104">Parámetro</span><span class="sxs-lookup"><span data-stu-id="e490d-104">Parameter</span></span>|<span data-ttu-id="e490d-105">Funcionalidad</span><span class="sxs-lookup"><span data-stu-id="e490d-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="e490d-106">**como**</span><span class="sxs-lookup"><span data-stu-id="e490d-106">**As**</span></span><br><span data-ttu-id="e490d-107">Tipo de datos: Palabra clave</span><span class="sxs-lookup"><span data-stu-id="e490d-107">Data type: Keyword</span></span>|<span data-ttu-id="e490d-108">Implemente este parámetro para especificar el formato de salida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e490d-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="e490d-109">Por ejemplo, los valores posibles podrían ser texto o un Script.</span><span class="sxs-lookup"><span data-stu-id="e490d-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="e490d-110">**archivo binario**</span><span class="sxs-lookup"><span data-stu-id="e490d-110">**Binary**</span></span><br><span data-ttu-id="e490d-111">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e490d-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="e490d-112">Implemente este parámetro para indicar que el cmdlet controla los valores binarios.</span><span class="sxs-lookup"><span data-stu-id="e490d-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="e490d-113">**Codificación**</span><span class="sxs-lookup"><span data-stu-id="e490d-113">**Encoding**</span></span><br><span data-ttu-id="e490d-114">Tipo de datos: Palabra clave</span><span class="sxs-lookup"><span data-stu-id="e490d-114">Data type: Keyword</span></span>|<span data-ttu-id="e490d-115">Implemente este parámetro para especificar el tipo de codificación que se admite.</span><span class="sxs-lookup"><span data-stu-id="e490d-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="e490d-116">Por ejemplo, podrían ser los posibles valores ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, bytes y cadena.</span><span class="sxs-lookup"><span data-stu-id="e490d-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="e490d-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="e490d-117">**NewLine**</span></span><br><span data-ttu-id="e490d-118">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e490d-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="e490d-119">Implemente este parámetro para que se admiten los caracteres de nueva línea cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="e490d-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="e490d-120">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="e490d-120">**ShortName**</span></span><br><span data-ttu-id="e490d-121">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e490d-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="e490d-122">Implemente este parámetro para que se admiten nombres cortos cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="e490d-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="e490d-123">**Width**</span><span class="sxs-lookup"><span data-stu-id="e490d-123">**Width**</span></span><br><span data-ttu-id="e490d-124">Tipo de datos: Int32</span><span class="sxs-lookup"><span data-stu-id="e490d-124">Data type: Int32</span></span>|<span data-ttu-id="e490d-125">Implemente este parámetro para que el usuario puede especificar el ancho del dispositivo de salida.</span><span class="sxs-lookup"><span data-stu-id="e490d-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="e490d-126">**Wrap**</span><span class="sxs-lookup"><span data-stu-id="e490d-126">**Wrap**</span></span><br><span data-ttu-id="e490d-127">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e490d-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="e490d-128">Implemente este parámetro para que se admite el ajuste de texto cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="e490d-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="e490d-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="e490d-129">See Also</span></span>

[<span data-ttu-id="e490d-130">Parámetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e490d-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="e490d-131">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e490d-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="e490d-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e490d-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
