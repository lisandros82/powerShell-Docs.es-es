---
title: Parámetros de actividad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251224"
---
# <a name="activity-parameters"></a><span data-ttu-id="b2c0d-102">Parámetros de actividad</span><span class="sxs-lookup"><span data-stu-id="b2c0d-102">Activity Parameters</span></span>

<span data-ttu-id="b2c0d-103">En la tabla siguiente se enumera los nombres recomendados y la funcionalidad para los parámetros de actividad.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-103">The following table lists the recommended names and functionality for activity parameters.</span></span>

|<span data-ttu-id="b2c0d-104">Parámetro</span><span class="sxs-lookup"><span data-stu-id="b2c0d-104">Parameter</span></span>|<span data-ttu-id="b2c0d-105">Funcionalidad</span><span class="sxs-lookup"><span data-stu-id="b2c0d-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="b2c0d-106">**Anexar**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-106">**Append**</span></span><br><span data-ttu-id="b2c0d-107">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-107">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-108">Implemente este parámetro para que el usuario puede agregar contenido al final de un recurso cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-108">Implement this parameter so that the user can add content to the end of a resource when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-109">**CaseSensitive**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-109">**CaseSensitive**</span></span><br><span data-ttu-id="b2c0d-110">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-110">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-111">Implementar este parámetro para que el usuario puede requerir mayúsculas y minúsculas cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-111">Implement this parameter so the user can require case sensitivity when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-112">**Command**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-112">**Command**</span></span><br><span data-ttu-id="b2c0d-113">Tipo de datos: Cadena</span><span class="sxs-lookup"><span data-stu-id="b2c0d-113">Data type: String</span></span>|<span data-ttu-id="b2c0d-114">Implementar este parámetro para que el usuario puede especificar una cadena de comandos para ejecutar.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-114">Implement this parameter so the user can specify a command string to run.</span></span>|
|<span data-ttu-id="b2c0d-115">**CompatibleVersion**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-115">**CompatibleVersion**</span></span><br><span data-ttu-id="b2c0d-116">Tipo de datos: Objeto System.Version</span><span class="sxs-lookup"><span data-stu-id="b2c0d-116">Data type: System.Version object</span></span>|<span data-ttu-id="b2c0d-117">Implementar este parámetro para que el usuario puede especificar la semántica que el cmdlet debe ser compatible con la compatibilidad con versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-117">Implement this parameter so the user can specify the semantics that the cmdlet must be compatible with for compatibility with previous versions.</span></span>|
|<span data-ttu-id="b2c0d-118">**Comprimir**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-118">**Compress**</span></span><br><span data-ttu-id="b2c0d-119">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-119">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-120">Implemente este parámetro para que se emplea la compresión de datos cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-120">Implement this parameter so that data compression is used when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-121">**Comprimir**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-121">**Compress**</span></span><br><span data-ttu-id="b2c0d-122">Tipo de datos: Palabra clave</span><span class="sxs-lookup"><span data-stu-id="b2c0d-122">Data type: Keyword</span></span>|<span data-ttu-id="b2c0d-123">Implemente este parámetro para que el usuario puede especificar el algoritmo que se usará para la compresión de datos.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-123">Implement this parameter so that the user can specify the algorithm to use for data compression.</span></span>|
|<span data-ttu-id="b2c0d-124">**continua**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-124">**Continuous**</span></span><br><span data-ttu-id="b2c0d-125">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-125">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-126">Implemente este parámetro para que se procesan los datos hasta que el usuario finaliza el cmdlet cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-126">Implement this parameter so that data is processed until the user terminates the cmdlet when the parameter is specified.</span></span> <span data-ttu-id="b2c0d-127">Si no se especifica el parámetro, el cmdlet procesa una cantidad predefinida de datos y, a continuación, finaliza la operación.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-127">If the parameter is not specified, the cmdlet processes a predefined amount of data and then terminates the operation.</span></span>|
|<span data-ttu-id="b2c0d-128">**Crear**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-128">**Create**</span></span><br><span data-ttu-id="b2c0d-129">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-129">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-130">Implemente este parámetro para indicar que se crea un recurso si aún no existe cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-130">Implement this parameter to indicate that a resource is created if one does not already exist when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-131">**Delete**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-131">**Delete**</span></span><br><span data-ttu-id="b2c0d-132">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-132">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-133">Implemente este parámetro para que los recursos se eliminan cuando el cmdlet se ha completado su operación cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-133">Implement this parameter so that resources are deleted when the cmdlet has completed its operation when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-134">**Purga**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-134">**Drain**</span></span><br><span data-ttu-id="b2c0d-135">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-135">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-136">Implemente este parámetro para indicar que se procesan los elementos de trabajo pendientes antes de que el cmdlet procesa datos nuevos cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-136">Implement this parameter to indicate that outstanding work items are processed before the cmdlet processes new data when the parameter is specified.</span></span> <span data-ttu-id="b2c0d-137">Si el parámetro no se especifica, se procesan inmediatamente los elementos de trabajo.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-137">If the parameter is not specified, the work items are processed immediately.</span></span>|
|<span data-ttu-id="b2c0d-138">**Borrar**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-138">**Erase**</span></span><br><span data-ttu-id="b2c0d-139">Tipo de datos: Int32</span><span class="sxs-lookup"><span data-stu-id="b2c0d-139">Data type: Int32</span></span>|<span data-ttu-id="b2c0d-140">Implemente este parámetro para que el usuario puede especificar el número de veces que un recurso se borra antes de eliminarla.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-140">Implement this parameter so that the user can specify the number of times a resource is erased before it is deleted.</span></span>|
|<span data-ttu-id="b2c0d-141">**ErrorLevel**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-141">**ErrorLevel**</span></span><br><span data-ttu-id="b2c0d-142">Tipo de datos: Int32</span><span class="sxs-lookup"><span data-stu-id="b2c0d-142">Data type: Int32</span></span>|<span data-ttu-id="b2c0d-143">Implemente este parámetro para que el usuario puede especificar el nivel de errores para informar.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-143">Implement this parameter so that the user can specify the level of errors to report.</span></span>|
|<span data-ttu-id="b2c0d-144">**excluir**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-144">**Exclude**</span></span><br><span data-ttu-id="b2c0d-145">Tipo de datos: String[]</span><span class="sxs-lookup"><span data-stu-id="b2c0d-145">Data type: String[]</span></span>|<span data-ttu-id="b2c0d-146">Implemente este parámetro para que el usuario puede excluir algo de una actividad.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-146">Implement this parameter so that the user can exclude something from an activity.</span></span> <span data-ttu-id="b2c0d-147">Para obtener más información sobre cómo usar los filtros de entrada, consulte [parámetros de filtro de entrada](input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b2c0d-147">For more information about how to use input filters, see [Input Filter Parameters](input-filter-parameters.md).</span></span>|
|<span data-ttu-id="b2c0d-148">**Filter**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-148">**Filter**</span></span><br><span data-ttu-id="b2c0d-149">Tipo de datos: Palabra clave</span><span class="sxs-lookup"><span data-stu-id="b2c0d-149">Data type: Keyword</span></span>|<span data-ttu-id="b2c0d-150">Implemente este parámetro para que el usuario puede especificar un filtro que selecciona los recursos al que se va a realizar la acción de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-150">Implement this parameter so that the user can specify a filter that selects the resources upon which to perform the cmdlet action.</span></span> <span data-ttu-id="b2c0d-151">Para obtener más información sobre cómo usar los filtros de entrada, consulte [parámetros de filtro de entrada](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b2c0d-151">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>|
|<span data-ttu-id="b2c0d-152">**Siga**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-152">**Follow**</span></span><br><span data-ttu-id="b2c0d-153">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-153">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-154">Implemente este parámetro para que se realiza un seguimiento de progreso cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-154">Implement this parameter so that progress is tracked when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-155">**Force**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-155">**Force**</span></span><br><span data-ttu-id="b2c0d-156">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-156">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-157">Implemente este parámetro para indicar que el usuario puede realizar una acción, incluso si se encuentran restricciones cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-157">Implement this parameter to indicate that the user can perform an action even if restrictions are encountered when the parameter is specified.</span></span> <span data-ttu-id="b2c0d-158">El parámetro no admite la seguridad en peligro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-158">The parameter does not allow security to be compromised.</span></span> <span data-ttu-id="b2c0d-159">Por ejemplo, este parámetro permite al usuario sobrescribir un archivo de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-159">For example, this parameter lets a user overwrite a read-only file.</span></span>|
|<span data-ttu-id="b2c0d-160">**Include**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-160">**Include**</span></span><br><span data-ttu-id="b2c0d-161">Tipo de datos: String[]</span><span class="sxs-lookup"><span data-stu-id="b2c0d-161">Data type: String[]</span></span>|<span data-ttu-id="b2c0d-162">Implemente este parámetro para que el usuario puede incluir algo en una actividad.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-162">Implement this parameter so that the user can include something in an activity.</span></span> <span data-ttu-id="b2c0d-163">Para obtener más información sobre cómo usar los filtros de entrada, consulte [parámetros de filtro de entrada](input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b2c0d-163">For more information about how to use input filters, see [Input Filter Parameters](input-filter-parameters.md).</span></span>|
|<span data-ttu-id="b2c0d-164">**Incremental**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-164">**Incremental**</span></span><br><span data-ttu-id="b2c0d-165">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-165">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-166">Implemente este parámetro para indicar que el procesamiento se realiza de forma incremental cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-166">Implement this parameter to indicate that processing is performed incrementally when the parameter is specified.</span></span> <span data-ttu-id="b2c0d-167">Por ejemplo, este parámetro permite al usuario realizar copias de seguridad incrementales para realizar una copia de seguridad de archivos sólo desde la última copia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-167">For example, this parameter lets a user perform incremental backups that back up files only since the last backup.</span></span>|
|<span data-ttu-id="b2c0d-168">**InputObject**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-168">**InputObject**</span></span><br><span data-ttu-id="b2c0d-169">Tipo de datos: Objeto</span><span class="sxs-lookup"><span data-stu-id="b2c0d-169">Data type: Object</span></span>|<span data-ttu-id="b2c0d-170">Implemente este parámetro cuando el cmdlet toma como entrado de otros cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-170">Implement this parameter when the cmdlet takes input from other cmdlets.</span></span> <span data-ttu-id="b2c0d-171">Al definir un **InputObject** parámetro, especifique siempre el **ValueFromPipeline** palabra clave cuando se declara el **parámetro** atributo.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-171">When you define an **InputObject** parameter, always specify the **ValueFromPipeline** keyword when you declare the **Parameter** attribute.</span></span> <span data-ttu-id="b2c0d-172">Para obtener más información sobre el uso de filtros de entrada, consulte [parámetros de filtro de entrada](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b2c0d-172">For more information about using input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>|
|<span data-ttu-id="b2c0d-173">**Insert**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-173">**Insert**</span></span><br><span data-ttu-id="b2c0d-174">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-174">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-175">Implemente este parámetro para que el cmdlet inserta un elemento cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-175">Implement this parameter so that the cmdlet inserts an item when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-176">**Interactive**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-176">**Interactive**</span></span><br><span data-ttu-id="b2c0d-177">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-177">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-178">Implemente este parámetro para que el cmdlet interactivamente funciona con el usuario cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-178">Implement this parameter so that the cmdlet works interactively with the user when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-179">**Interval**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-179">**Interval**</span></span><br><span data-ttu-id="b2c0d-180">Tipo de datos: HashTable</span><span class="sxs-lookup"><span data-stu-id="b2c0d-180">Data type: HashTable</span></span>|<span data-ttu-id="b2c0d-181">Implemente este parámetro para que el usuario puede especificar una tabla de hash de las palabras clave que contiene los valores.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-181">Implement this parameter so that the user can specify a hash table of keywords that contains the values.</span></span> <span data-ttu-id="b2c0d-182">El ejemplo siguiente muestra los valores de ejemplo para el **intervalo** parámetro: `-interval @{ResumeScan=15; Retry=3}`.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-182">The following example shows sample values for the **Interval** parameter: `-interval @{ResumeScan=15; Retry=3}`.</span></span>|
|<span data-ttu-id="b2c0d-183">**Log**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-183">**Log**</span></span><br><span data-ttu-id="b2c0d-184">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-184">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-185">Implemente esta auditoría de parámetro de las acciones del cmdlet cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-185">Implement this parameter audit the actions of the cmdlet when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-186">**NoClobber**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-186">**NoClobber**</span></span><br><span data-ttu-id="b2c0d-187">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-187">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-188">Implemente este parámetro para que el recurso no se sobrescribirá cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-188">Implement this parameter so that the resource will not be overwritten when the parameter is specified.</span></span> <span data-ttu-id="b2c0d-189">Normalmente, este parámetro se aplica a los cmdlets que crean nuevos objetos para que pueden evitar que se sobrescriban los objetos existentes con el mismo nombre.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-189">This parameter generally applies to cmdlets that create new objects so that they can be prevented from overwriting existing objects with the same name.</span></span>|
|<span data-ttu-id="b2c0d-190">**Notificar**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-190">**Notify**</span></span><br><span data-ttu-id="b2c0d-191">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-191">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-192">Implemente este parámetro para que el usuario le notificará que la actividad está completa cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-192">Implement this parameter so that the user will be notified that the activity is complete when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-193">**NotifyAddress**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-193">**NotifyAddress**</span></span><br><span data-ttu-id="b2c0d-194">Tipo de datos: Dirección de correo electrónico</span><span class="sxs-lookup"><span data-stu-id="b2c0d-194">Data type: Email address</span></span>|<span data-ttu-id="b2c0d-195">Implemente este parámetro para que el usuario puede especificar la dirección de correo electrónico a usar para enviar una notificación cuando la **Notify** se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-195">Implement this parameter so that the user can specify the e-mail address to use to send a notification when the **Notify** parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-196">**Sobrescribir**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-196">**Overwrite**</span></span><br><span data-ttu-id="b2c0d-197">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-197">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-198">Implemente este parámetro para que el cmdlet sobrescribe los datos existentes cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-198">Implement this parameter so that the cmdlet overwrites any existing data when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-199">**Prompt**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-199">**Prompt**</span></span><br><span data-ttu-id="b2c0d-200">Tipo de datos: Cadena</span><span class="sxs-lookup"><span data-stu-id="b2c0d-200">Data type: String</span></span>|<span data-ttu-id="b2c0d-201">Implemente este parámetro para que el usuario puede especificar un símbolo del sistema para el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-201">Implement this parameter so that the user can specify a prompt for the cmdlet.</span></span>|
|<span data-ttu-id="b2c0d-202">**Quiet**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-202">**Quiet**</span></span><br><span data-ttu-id="b2c0d-203">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-203">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-204">Implemente este parámetro para que el cmdlet suprime los comentarios de los usuarios durante sus acciones cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-204">Implement this parameter so that the cmdlet suppresses user feedback during its actions when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-205">**Recurse**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-205">**Recurse**</span></span><br><span data-ttu-id="b2c0d-206">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-206">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-207">Implemente este parámetro para que el cmdlet de forma recursiva lleva a cabo sus acciones en los recursos cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-207">Implement this parameter so that the cmdlet recursively performs its actions on resources when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-208">**Reparación**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-208">**Repair**</span></span><br><span data-ttu-id="b2c0d-209">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-209">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-210">Implemente este parámetro para que el cmdlet intentará corregir algo de mal estado cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-210">Implement this parameter so that the cmdlet will attempt to correct something from a broken state when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-211">**RepairString**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-211">**RepairString**</span></span><br><span data-ttu-id="b2c0d-212">Tipo de datos: Cadena</span><span class="sxs-lookup"><span data-stu-id="b2c0d-212">Data type: String</span></span>|<span data-ttu-id="b2c0d-213">Implemente este parámetro para que el usuario puede especificar una cadena para usar cuando el **reparación** se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-213">Implement this parameter so that the user can specify a string to use when the **Repair** parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-214">**Retry**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-214">**Retry**</span></span><br><span data-ttu-id="b2c0d-215">Tipo de datos: Int32</span><span class="sxs-lookup"><span data-stu-id="b2c0d-215">Data type: Int32</span></span>|<span data-ttu-id="b2c0d-216">Implementar este parámetro para que el usuario puede especificar el número de veces que el cmdlet intentará una acción.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-216">Implement this parameter so the user can specify the number of times the cmdlet will attempt an action.</span></span>|
|<span data-ttu-id="b2c0d-217">**Select**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-217">**Select**</span></span><br><span data-ttu-id="b2c0d-218">Tipo de datos: Matriz de palabra clave</span><span class="sxs-lookup"><span data-stu-id="b2c0d-218">Data type: Keyword array</span></span>|<span data-ttu-id="b2c0d-219">Implemente este parámetro para que el usuario puede especificar una matriz de los tipos de elementos.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-219">Implement this parameter so that the user can specify an array of the types of items.</span></span>|
|<span data-ttu-id="b2c0d-220">**Stream**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-220">**Stream**</span></span><br><span data-ttu-id="b2c0d-221">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-221">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-222">Implementar este parámetro para que el usuario puede transmitir a varios objetos de salida a través de la canalización cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-222">Implement this parameter so the user can stream multiple output objects through the pipeline when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-223">**Strict**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-223">**Strict**</span></span><br><span data-ttu-id="b2c0d-224">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-224">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-225">Implemente este parámetro para que todos los errores se tratan como errores de terminación cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-225">Implement this parameter so that all errors are handled as terminating errors when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-226">**TempLocation**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-226">**TempLocation**</span></span><br><span data-ttu-id="b2c0d-227">Tipo de datos: Cadena</span><span class="sxs-lookup"><span data-stu-id="b2c0d-227">Data type: String</span></span>|<span data-ttu-id="b2c0d-228">Implementar este parámetro para que el usuario puede especificar la ubicación de los datos temporales que se usan durante el funcionamiento del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-228">Implement this parameter so the user can specify the location of temporary data that is used during the operation of the cmdlet.</span></span>|
|<span data-ttu-id="b2c0d-229">**Tiempo de espera**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-229">**Timeout**</span></span><br><span data-ttu-id="b2c0d-230">Tipo de datos: Int32</span><span class="sxs-lookup"><span data-stu-id="b2c0d-230">Data type: Int32</span></span>|<span data-ttu-id="b2c0d-231">Implemente este parámetro para que el usuario puede especificar el intervalo de tiempo de espera (en milisegundos).</span><span class="sxs-lookup"><span data-stu-id="b2c0d-231">Implement this parameter so that the user can specify the timeout interval (in milliseconds).</span></span>|
|<span data-ttu-id="b2c0d-232">**truncar**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-232">**Truncate**</span></span><br><span data-ttu-id="b2c0d-233">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-233">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-234">Implemente este parámetro para que el cmdlet truncará sus acciones cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-234">Implement this parameter so that the cmdlet will truncate its actions when the parameter is specified.</span></span> <span data-ttu-id="b2c0d-235">Si no se especifica el parámetro, el cmdlet realiza otra acción.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-235">If the parameter is not specified, the cmdlet performs another action.</span></span>|
|<span data-ttu-id="b2c0d-236">**Verify**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-236">**Verify**</span></span><br><span data-ttu-id="b2c0d-237">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-237">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-238">Implemente este parámetro para que el cmdlet realizará la comprobación para determinar si se ha producido una acción cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-238">Implement this parameter so that the cmdlet will test to determine whether an action has occurred when the parameter is specified.</span></span>|
|<span data-ttu-id="b2c0d-239">**Espere**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-239">**Wait**</span></span><br><span data-ttu-id="b2c0d-240">Tipo de datos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b2c0d-240">Data type: SwitchParameter</span></span>|<span data-ttu-id="b2c0d-241">Implemente este parámetro para que el cmdlet esperará proporcionados por el usuario antes de continuar cuando se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-241">Implement this parameter so that the cmdlet will wait for user input before continuing when the parameter is specified.</span></span>
|<span data-ttu-id="b2c0d-242">**WaitTime**</span><span class="sxs-lookup"><span data-stu-id="b2c0d-242">**WaitTime**</span></span><br><span data-ttu-id="b2c0d-243">Tipo de datos: Int32</span><span class="sxs-lookup"><span data-stu-id="b2c0d-243">Data type: Int32</span></span>|<span data-ttu-id="b2c0d-244">Implemente este parámetro para que el usuario puede especificar la duración (en segundos) que el cmdlet esperará usuario entrada cuando el **espera** se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b2c0d-244">Implement this parameter so that the user can specify the duration (in seconds) that the cmdlet will wait for user input when the **Wait** parameter is specified.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b2c0d-245">Véase también</span><span class="sxs-lookup"><span data-stu-id="b2c0d-245">See Also</span></span>

[<span data-ttu-id="b2c0d-246">Parámetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="b2c0d-246">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="b2c0d-247">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2c0d-247">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="b2c0d-248">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b2c0d-248">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)