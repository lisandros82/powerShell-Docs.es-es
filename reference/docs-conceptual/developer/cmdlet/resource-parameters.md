---
title: Parámetros de recursos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369514"
---
# <a name="resource-parameters"></a><span data-ttu-id="3b303-102">Parámetros de recursos</span><span class="sxs-lookup"><span data-stu-id="3b303-102">Resource Parameters</span></span>

<span data-ttu-id="3b303-103">En la tabla siguiente se enumeran los nombres recomendados y la funcionalidad de los parámetros de recursos.</span><span class="sxs-lookup"><span data-stu-id="3b303-103">The following table lists the recommended names and functionality for resource parameters.</span></span> <span data-ttu-id="3b303-104">Para estos parámetros, los recursos podrían ser el ensamblado que contiene la clase de cmdlet o la aplicación host que está ejecutando el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3b303-104">For these parameters, the resources could be the assembly that contains the cmdlet class or the host application that is running the cmdlet.</span></span>

|<span data-ttu-id="3b303-105">Parámetro</span><span class="sxs-lookup"><span data-stu-id="3b303-105">Parameter</span></span>|<span data-ttu-id="3b303-106">Funcionalidad</span><span class="sxs-lookup"><span data-stu-id="3b303-106">Functionality</span></span>|
|---|---|
|<span data-ttu-id="3b303-107">**Aplicación**</span><span class="sxs-lookup"><span data-stu-id="3b303-107">**Application**</span></span><br><span data-ttu-id="3b303-108">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-108">Data type: String</span></span>|<span data-ttu-id="3b303-109">Implemente este parámetro para que el usuario pueda especificar una aplicación.</span><span class="sxs-lookup"><span data-stu-id="3b303-109">Implement this parameter so that the user can specify an application.</span></span>|
|<span data-ttu-id="3b303-110">**Assembl**</span><span class="sxs-lookup"><span data-stu-id="3b303-110">**Assembly**</span></span><br><span data-ttu-id="3b303-111">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-111">Data type: String</span></span>|<span data-ttu-id="3b303-112">Implemente este parámetro para que el usuario pueda especificar un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="3b303-112">Implement this parameter so that the user can specify an assembly.</span></span>|
|<span data-ttu-id="3b303-113">**Atribui**</span><span class="sxs-lookup"><span data-stu-id="3b303-113">**Attribute**</span></span><br><span data-ttu-id="3b303-114">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-114">Data type: String</span></span>|<span data-ttu-id="3b303-115">Implemente este parámetro para que el usuario pueda especificar un atributo.</span><span class="sxs-lookup"><span data-stu-id="3b303-115">Implement this parameter so that the user can specify an attribute.</span></span>|
|<span data-ttu-id="3b303-116">**Las**</span><span class="sxs-lookup"><span data-stu-id="3b303-116">**Class**</span></span><br><span data-ttu-id="3b303-117">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-117">Data type: String</span></span>|<span data-ttu-id="3b303-118">Implemente este parámetro para que el usuario pueda especificar una clase de marco de Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="3b303-118">Implement this parameter so that the user can specify a Microsoft .NET Framework class.</span></span>|
|<span data-ttu-id="3b303-119">**Por**</span><span class="sxs-lookup"><span data-stu-id="3b303-119">**Cluster**</span></span><br><span data-ttu-id="3b303-120">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-120">Data type: String</span></span>|<span data-ttu-id="3b303-121">Implemente este parámetro para que el usuario pueda especificar un clúster.</span><span class="sxs-lookup"><span data-stu-id="3b303-121">Implement this parameter so that the user can specify a cluster.</span></span>|
|<span data-ttu-id="3b303-122">**Cultivo**</span><span class="sxs-lookup"><span data-stu-id="3b303-122">**Culture**</span></span><br><span data-ttu-id="3b303-123">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-123">Data type: String</span></span>|<span data-ttu-id="3b303-124">Implemente este parámetro para que el usuario pueda especificar la referencia cultural en la que se va a ejecutar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3b303-124">Implement this parameter so that the user can specify the culture in which to run the cmdlet.</span></span>|
|<span data-ttu-id="3b303-125">**Dominio**</span><span class="sxs-lookup"><span data-stu-id="3b303-125">**Domain**</span></span><br><span data-ttu-id="3b303-126">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-126">Data type: String</span></span>|<span data-ttu-id="3b303-127">Implemente este parámetro para que el usuario pueda especificar el nombre de dominio.</span><span class="sxs-lookup"><span data-stu-id="3b303-127">Implement this parameter so that the user can specify the domain name.</span></span>|
|<span data-ttu-id="3b303-128">**Dispositivo**</span><span class="sxs-lookup"><span data-stu-id="3b303-128">**Drive**</span></span><br><span data-ttu-id="3b303-129">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-129">Data type: String</span></span>|<span data-ttu-id="3b303-130">Implemente este parámetro para que el usuario pueda especificar un nombre de unidad.</span><span class="sxs-lookup"><span data-stu-id="3b303-130">Implement this parameter so that the user can specify a drive name.</span></span>|
|<span data-ttu-id="3b303-131">**Ceso**</span><span class="sxs-lookup"><span data-stu-id="3b303-131">**Event**</span></span><br><span data-ttu-id="3b303-132">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-132">Data type: String</span></span>|<span data-ttu-id="3b303-133">Implemente este parámetro para que el usuario pueda especificar un nombre de evento.</span><span class="sxs-lookup"><span data-stu-id="3b303-133">Implement this parameter so that the user can specify an event name.</span></span>|
|<span data-ttu-id="3b303-134">**Interfaz**</span><span class="sxs-lookup"><span data-stu-id="3b303-134">**Interface**</span></span><br><span data-ttu-id="3b303-135">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-135">Data type: String</span></span>|<span data-ttu-id="3b303-136">Implemente este parámetro para que el usuario pueda especificar un nombre de interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="3b303-136">Implement this parameter so that the user can specify a network interface name.</span></span>|
|<span data-ttu-id="3b303-137">**DirIP**</span><span class="sxs-lookup"><span data-stu-id="3b303-137">**IpAddress**</span></span><br><span data-ttu-id="3b303-138">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-138">Data type: String</span></span>|<span data-ttu-id="3b303-139">Implemente este parámetro para que el usuario pueda especificar una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="3b303-139">Implement this parameter so that the user can specify an IP address.</span></span>|
|<span data-ttu-id="3b303-140">**Trabajo**</span><span class="sxs-lookup"><span data-stu-id="3b303-140">**Job**</span></span><br><span data-ttu-id="3b303-141">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-141">Data type: String</span></span>|<span data-ttu-id="3b303-142">Implemente este parámetro para que el usuario pueda especificar un trabajo.</span><span class="sxs-lookup"><span data-stu-id="3b303-142">Implement this parameter so that the user can specify a job.</span></span>|
|<span data-ttu-id="3b303-143">**LiteralPath**</span><span class="sxs-lookup"><span data-stu-id="3b303-143">**LiteralPath**</span></span><br><span data-ttu-id="3b303-144">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-144">Data type: String</span></span>|<span data-ttu-id="3b303-145">Implemente este parámetro para que el usuario pueda especificar la ruta de acceso a un recurso cuando no se admiten caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="3b303-145">Implement this parameter so that the user can specify the path to a resource when wildcard characters are not supported.</span></span> <span data-ttu-id="3b303-146">(Use el parámetro **path** cuando se admitan caracteres comodín).</span><span class="sxs-lookup"><span data-stu-id="3b303-146">(Use the **Path** parameter when wildcard characters are supported.)</span></span>|
|<span data-ttu-id="3b303-147">**Mac**</span><span class="sxs-lookup"><span data-stu-id="3b303-147">**Mac**</span></span><br><span data-ttu-id="3b303-148">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-148">Data type: String</span></span>|<span data-ttu-id="3b303-149">Implemente este parámetro para que el usuario pueda especificar una dirección de controlador de acceso a medios (MAC).</span><span class="sxs-lookup"><span data-stu-id="3b303-149">Implement this parameter so that the user can specify a media access controller (MAC) address.</span></span>|
|<span data-ttu-id="3b303-150">**ParentId**</span><span class="sxs-lookup"><span data-stu-id="3b303-150">**ParentId**</span></span><br><span data-ttu-id="3b303-151">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-151">Data type: String</span></span>|<span data-ttu-id="3b303-152">Implemente este parámetro para que el usuario pueda especificar el identificador primario.</span><span class="sxs-lookup"><span data-stu-id="3b303-152">Implement this parameter so that the user can specify the parent identifier.</span></span>|
|<span data-ttu-id="3b303-153">**Camino**</span><span class="sxs-lookup"><span data-stu-id="3b303-153">**Path**</span></span><br><span data-ttu-id="3b303-154">Tipo de datos: cadena, cadena []</span><span class="sxs-lookup"><span data-stu-id="3b303-154">Data type: String, String[]</span></span>|<span data-ttu-id="3b303-155">Implemente este parámetro para que el usuario pueda indicar las rutas de acceso a un recurso cuando se admitan caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="3b303-155">Implement this parameter so that the user can indicate the paths to a resource when wildcard characters are supported.</span></span> <span data-ttu-id="3b303-156">(Use el parámetro **LiteralPath** cuando no se admiten caracteres comodín). Se recomienda desarrollar este parámetro para que admita la sintaxis completa de `provider:path` utilizada por los proveedores.</span><span class="sxs-lookup"><span data-stu-id="3b303-156">(Use the **LiteralPath** parameter when wildcard characters are not supported.) We recommend that you develop this parameter so that it supports the full `provider:path` syntax used by providers.</span></span> <span data-ttu-id="3b303-157">También se recomienda que lo desarrolle para que funcione con tantos proveedores como sea posible.</span><span class="sxs-lookup"><span data-stu-id="3b303-157">We also recommend that you develop it so that it works with as many providers as possible.</span></span>|
|<span data-ttu-id="3b303-158">**Casilla**</span><span class="sxs-lookup"><span data-stu-id="3b303-158">**Port**</span></span><br><span data-ttu-id="3b303-159">Tipo de datos: entero, cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-159">Data type: Integer, String</span></span>|<span data-ttu-id="3b303-160">Implemente este parámetro para que el usuario pueda especificar un valor entero para redes o un valor de cadena como "BizTalk" para otros tipos de puerto.</span><span class="sxs-lookup"><span data-stu-id="3b303-160">Implement this parameter so that the user can specify an integer value for networking or a string value such as "biztalk" for other types of port.</span></span>|
|<span data-ttu-id="3b303-161">**Imprenta**</span><span class="sxs-lookup"><span data-stu-id="3b303-161">**Printer**</span></span><br><span data-ttu-id="3b303-162">Tipo de datos: entero, cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-162">Data type: Integer, String</span></span>|<span data-ttu-id="3b303-163">Implemente este parámetro para que el usuario pueda especificar la impresora que va a usar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3b303-163">Implement this parameter so that the user can specify the printer for the cmdlet to use.</span></span>|
|<span data-ttu-id="3b303-164">**Ajusta**</span><span class="sxs-lookup"><span data-stu-id="3b303-164">**Size**</span></span><br><span data-ttu-id="3b303-165">Tipo de datos: Int32</span><span class="sxs-lookup"><span data-stu-id="3b303-165">Data type: Int32</span></span>|<span data-ttu-id="3b303-166">Implemente este parámetro para que el usuario pueda especificar un tamaño.</span><span class="sxs-lookup"><span data-stu-id="3b303-166">Implement this parameter so that the user can specify a size.</span></span>|
|<span data-ttu-id="3b303-167">**TID**</span><span class="sxs-lookup"><span data-stu-id="3b303-167">**TID**</span></span><br><span data-ttu-id="3b303-168">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-168">Data type: String</span></span>|<span data-ttu-id="3b303-169">Implemente este parámetro para que el usuario pueda especificar un identificador de transacción (TID) para el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3b303-169">Implement this parameter so that the user can specify a transaction identifier (TID) for the cmdlet.</span></span>|
|<span data-ttu-id="3b303-170">**Automáticamente**</span><span class="sxs-lookup"><span data-stu-id="3b303-170">**Type**</span></span><br><span data-ttu-id="3b303-171">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-171">Data type: String</span></span>|<span data-ttu-id="3b303-172">Implemente este parámetro para que el usuario pueda especificar el tipo de recurso en el que se va a operar.</span><span class="sxs-lookup"><span data-stu-id="3b303-172">Implement this parameter so that the user can specify the type of resource on which to operate.</span></span>|
|<span data-ttu-id="3b303-173">**Dirección**</span><span class="sxs-lookup"><span data-stu-id="3b303-173">**URL**</span></span><br><span data-ttu-id="3b303-174">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-174">Data type: String</span></span>|<span data-ttu-id="3b303-175">Implemente este parámetro para que el usuario pueda especificar un localizador uniforme de recursos (URL).</span><span class="sxs-lookup"><span data-stu-id="3b303-175">Implement this parameter so that the user can specify a Uniform Resource Locator (URL).</span></span>|
|<span data-ttu-id="3b303-176">**Usuario**</span><span class="sxs-lookup"><span data-stu-id="3b303-176">**User**</span></span><br><span data-ttu-id="3b303-177">Tipo de datos: cadena</span><span class="sxs-lookup"><span data-stu-id="3b303-177">Data type: String</span></span>|<span data-ttu-id="3b303-178">Implemente este parámetro para que el usuario pueda especificar su nombre o el nombre de otro usuario.</span><span class="sxs-lookup"><span data-stu-id="3b303-178">Implement this parameter so that the user can specify their name or the name of another user.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3b303-179">Véase también</span><span class="sxs-lookup"><span data-stu-id="3b303-179">See Also</span></span>

[<span data-ttu-id="3b303-180">Parámetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b303-180">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="3b303-181">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b303-181">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="3b303-182">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3b303-182">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)