---
title: Parámetros de propiedad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369584"
---
# <a name="property-parameters"></a><span data-ttu-id="b0a4e-102">Parámetros de propiedad</span><span class="sxs-lookup"><span data-stu-id="b0a4e-102">Property Parameters</span></span>

<span data-ttu-id="b0a4e-103">En la tabla siguiente se enumeran los nombres recomendados y la funcionalidad de los parámetros de propiedad.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-103">The following table lists the recommended names and functionality for property parameters.</span></span>

|<span data-ttu-id="b0a4e-104">Parámetro</span><span class="sxs-lookup"><span data-stu-id="b0a4e-104">Parameter</span></span>|<span data-ttu-id="b0a4e-105">Funcionalidad</span><span class="sxs-lookup"><span data-stu-id="b0a4e-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="b0a4e-106">**Contabiliza**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-106">**Count**</span></span><br><span data-ttu-id="b0a4e-107">Tipo de datos: Int32</span><span class="sxs-lookup"><span data-stu-id="b0a4e-107">Data type: Int32</span></span>|<span data-ttu-id="b0a4e-108">Implemente este parámetro para que el usuario pueda especificar el número de objetos que se van a procesar.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-108">Implement this parameter so that the user can specify the number of objects to be processed.</span></span>|
|<span data-ttu-id="b0a4e-109">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-109">**Description**</span></span><br><span data-ttu-id="b0a4e-110">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="b0a4e-110">Data type: String</span></span>|<span data-ttu-id="b0a4e-111">Implemente este parámetro para que el usuario pueda especificar una descripción de un recurso.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-111">Implement this parameter so that the user can specify a description for a resource.</span></span>|
|<span data-ttu-id="b0a4e-112">**De**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-112">**From**</span></span><br><span data-ttu-id="b0a4e-113">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="b0a4e-113">Data type: String</span></span>|<span data-ttu-id="b0a4e-114">Implemente este parámetro para que el usuario pueda especificar el objeto de referencia del que se va a obtener información.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-114">Implement this parameter so that the user can specify the reference object to get information from.</span></span>|
|<span data-ttu-id="b0a4e-115">**Sesión**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-115">**Id**</span></span><br><span data-ttu-id="b0a4e-116">Tipo de datos: dependiente del recurso</span><span class="sxs-lookup"><span data-stu-id="b0a4e-116">Data type: Resource dependent</span></span>|<span data-ttu-id="b0a4e-117">Implemente este parámetro para que el usuario pueda especificar el identificador de un recurso.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-117">Implement this parameter so that the user can specify the identifier of a resource.</span></span>|
|<span data-ttu-id="b0a4e-118">**Entradas**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-118">**Input**</span></span><br><span data-ttu-id="b0a4e-119">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="b0a4e-119">Data type: String</span></span>|<span data-ttu-id="b0a4e-120">Implemente este parámetro para que el usuario pueda especificar la especificación del archivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-120">Implement this parameter so that the user can specify the input file specification.</span></span>|
|<span data-ttu-id="b0a4e-121">**Ubicación**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-121">**Location**</span></span><br><span data-ttu-id="b0a4e-122">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="b0a4e-122">Data type: String</span></span>|<span data-ttu-id="b0a4e-123">Implemente este parámetro para que el usuario pueda especificar la ubicación del recurso.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-123">Implement this parameter so that the user can specify the location of the resource.</span></span>|
|<span data-ttu-id="b0a4e-124">**LogName**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-124">**LogName**</span></span><br><span data-ttu-id="b0a4e-125">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="b0a4e-125">Data type: String</span></span>|<span data-ttu-id="b0a4e-126">Implemente este parámetro para que el usuario pueda especificar el nombre del archivo de registro que se va a procesar o usar.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-126">Implement this parameter so that the user can specify the name of the log file to process or use.</span></span>|
|<span data-ttu-id="b0a4e-127">**Name**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-127">**Name**</span></span><br><span data-ttu-id="b0a4e-128">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="b0a4e-128">Data type: String</span></span>|<span data-ttu-id="b0a4e-129">Implemente este parámetro para que el usuario pueda especificar el nombre del recurso.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-129">Implement this parameter so that the user can specify the name of the resource.</span></span>|
|<span data-ttu-id="b0a4e-130">**Genere**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-130">**Output**</span></span><br><span data-ttu-id="b0a4e-131">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="b0a4e-131">Data type: String</span></span>|<span data-ttu-id="b0a4e-132">Implemente este parámetro para que el usuario pueda especificar el archivo de salida.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-132">Implement this parameter so that the user can specify the output file.</span></span>|
|<span data-ttu-id="b0a4e-133">**Propietario**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-133">**Owner**</span></span><br><span data-ttu-id="b0a4e-134">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="b0a4e-134">Data type: String</span></span>|<span data-ttu-id="b0a4e-135">Implemente este parámetro para que el usuario pueda especificar el nombre del propietario del recurso.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-135">Implement this parameter so that the user can specify the name of the owner of the resource.</span></span>|
|<span data-ttu-id="b0a4e-136">**Propiedad**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-136">**Property**</span></span><br><span data-ttu-id="b0a4e-137">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="b0a4e-137">Data type: String</span></span>|<span data-ttu-id="b0a4e-138">Implemente este parámetro para que el usuario pueda especificar el nombre o los nombres de las propiedades que se van a utilizar.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-138">Implement this parameter so that the user can specify the name or the names of the properties to use.</span></span>|
|<span data-ttu-id="b0a4e-139">**Debido**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-139">**Reason**</span></span><br><span data-ttu-id="b0a4e-140">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="b0a4e-140">Data type: String</span></span>|<span data-ttu-id="b0a4e-141">Implemente este parámetro para que el usuario pueda especificar por qué se invoca este cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-141">Implement this parameter so that the user can specify why this cmdlet is being invoked.</span></span>|
|<span data-ttu-id="b0a4e-142">**Regular**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-142">**Regex**</span></span><br><span data-ttu-id="b0a4e-143">Tipo de datos: Parámetrodemodificador</span><span class="sxs-lookup"><span data-stu-id="b0a4e-143">Data type: SwitchParameter</span></span>|<span data-ttu-id="b0a4e-144">Implemente este parámetro para que se usen expresiones regulares cuando se especifique el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-144">Implement this parameter so that regular expressions are used when the parameter is specified.</span></span> <span data-ttu-id="b0a4e-145">Cuando se especifica este parámetro, no se resuelven los caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-145">When this parameter is specified, wildcard characters are not resolved.</span></span>|
|<span data-ttu-id="b0a4e-146">**Rápidas**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-146">**Speed**</span></span><br><span data-ttu-id="b0a4e-147">Tipo de datos: Int32</span><span class="sxs-lookup"><span data-stu-id="b0a4e-147">Data type: Int32</span></span>|<span data-ttu-id="b0a4e-148">Implemente este parámetro para que el usuario pueda especificar la velocidad en baudios.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-148">Implement this parameter so that the user can specify the baud rate.</span></span> <span data-ttu-id="b0a4e-149">El usuario establece este parámetro en la velocidad del recurso.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-149">The user sets this parameter to the speed of the resource.</span></span>|
|<span data-ttu-id="b0a4e-150">**State**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-150">**State**</span></span><br><span data-ttu-id="b0a4e-151">Tipo de datos: palabra clave array</span><span class="sxs-lookup"><span data-stu-id="b0a4e-151">Data type: Keyword array</span></span>|<span data-ttu-id="b0a4e-152">Implemente este parámetro para que el usuario pueda especificar los nombres de los Estados, como KEYDOWN.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-152">Implement this parameter so that the user can specify the names of states, such as KEYDOWN.</span></span>|
|<span data-ttu-id="b0a4e-153">**Valor**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-153">**Value**</span></span><br><span data-ttu-id="b0a4e-154">Tipo de datos: objeto</span><span class="sxs-lookup"><span data-stu-id="b0a4e-154">Data type: Object</span></span>|<span data-ttu-id="b0a4e-155">Implemente este parámetro para que el usuario pueda especificar un valor para proporcionar al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-155">Implement this parameter so that the user can  specify a value to provide to the cmdlet.</span></span>|
|<span data-ttu-id="b0a4e-156">**Versión**</span><span class="sxs-lookup"><span data-stu-id="b0a4e-156">**Version**</span></span><br><span data-ttu-id="b0a4e-157">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="b0a4e-157">Data type: String</span></span>|<span data-ttu-id="b0a4e-158">Implemente este parámetro para que el usuario pueda especificar la versión de la propiedad.</span><span class="sxs-lookup"><span data-stu-id="b0a4e-158">Implement this parameter so that the user can specify the version of the property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b0a4e-159">Véase también</span><span class="sxs-lookup"><span data-stu-id="b0a4e-159">See Also</span></span>

[<span data-ttu-id="b0a4e-160">Parámetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="b0a4e-160">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="b0a4e-161">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0a4e-161">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="b0a4e-162">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b0a4e-162">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)