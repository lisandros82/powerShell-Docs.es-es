---
title: Parámetros de formato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369754"
---
# <a name="format-parameters"></a><span data-ttu-id="21326-102">Parámetros de formato</span><span class="sxs-lookup"><span data-stu-id="21326-102">Format Parameters</span></span>

<span data-ttu-id="21326-103">En la tabla siguiente se enumeran los nombres recomendados y la funcionalidad de los parámetros que se usan para dar formato o generar datos.</span><span class="sxs-lookup"><span data-stu-id="21326-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="21326-104">Parámetro</span><span class="sxs-lookup"><span data-stu-id="21326-104">Parameter</span></span>|<span data-ttu-id="21326-105">Funcionalidad</span><span class="sxs-lookup"><span data-stu-id="21326-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="21326-106">**Aplicar**</span><span class="sxs-lookup"><span data-stu-id="21326-106">**As**</span></span><br><span data-ttu-id="21326-107">Tipo de datos: palabra clave</span><span class="sxs-lookup"><span data-stu-id="21326-107">Data type: Keyword</span></span>|<span data-ttu-id="21326-108">Implemente este parámetro para especificar el formato de salida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="21326-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="21326-109">Por ejemplo, los valores posibles pueden ser texto o script.</span><span class="sxs-lookup"><span data-stu-id="21326-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="21326-110">**Binario**</span><span class="sxs-lookup"><span data-stu-id="21326-110">**Binary**</span></span><br><span data-ttu-id="21326-111">Tipo de datos: Parámetrodemodificador</span><span class="sxs-lookup"><span data-stu-id="21326-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="21326-112">Implemente este parámetro para indicar que el cmdlet controla los valores binarios.</span><span class="sxs-lookup"><span data-stu-id="21326-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="21326-113">**Codificación**</span><span class="sxs-lookup"><span data-stu-id="21326-113">**Encoding**</span></span><br><span data-ttu-id="21326-114">Tipo de datos: palabra clave</span><span class="sxs-lookup"><span data-stu-id="21326-114">Data type: Keyword</span></span>|<span data-ttu-id="21326-115">Implemente este parámetro para especificar el tipo de codificación que se admite.</span><span class="sxs-lookup"><span data-stu-id="21326-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="21326-116">Por ejemplo, los valores posibles pueden ser ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, byte y String.</span><span class="sxs-lookup"><span data-stu-id="21326-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="21326-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="21326-117">**NewLine**</span></span><br><span data-ttu-id="21326-118">Tipo de datos: Parámetrodemodificador</span><span class="sxs-lookup"><span data-stu-id="21326-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="21326-119">Implemente este parámetro para que se admitan los caracteres de nueva línea cuando se especifique el parámetro.</span><span class="sxs-lookup"><span data-stu-id="21326-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="21326-120">**Corto**</span><span class="sxs-lookup"><span data-stu-id="21326-120">**ShortName**</span></span><br><span data-ttu-id="21326-121">Tipo de datos: Parámetrodemodificador</span><span class="sxs-lookup"><span data-stu-id="21326-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="21326-122">Implemente este parámetro para que se admitan nombres cortos cuando se especifique el parámetro.</span><span class="sxs-lookup"><span data-stu-id="21326-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="21326-123">**Ancho**</span><span class="sxs-lookup"><span data-stu-id="21326-123">**Width**</span></span><br><span data-ttu-id="21326-124">Tipo de datos: Int32</span><span class="sxs-lookup"><span data-stu-id="21326-124">Data type: Int32</span></span>|<span data-ttu-id="21326-125">Implemente este parámetro para que el usuario pueda especificar el ancho del dispositivo de salida.</span><span class="sxs-lookup"><span data-stu-id="21326-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="21326-126">**Concluir**</span><span class="sxs-lookup"><span data-stu-id="21326-126">**Wrap**</span></span><br><span data-ttu-id="21326-127">Tipo de datos: Parámetrodemodificador</span><span class="sxs-lookup"><span data-stu-id="21326-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="21326-128">Implemente este parámetro para que se admita el ajuste de texto cuando se especifique el parámetro.</span><span class="sxs-lookup"><span data-stu-id="21326-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="21326-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="21326-129">See Also</span></span>

[<span data-ttu-id="21326-130">Parámetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="21326-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="21326-131">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="21326-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="21326-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="21326-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)