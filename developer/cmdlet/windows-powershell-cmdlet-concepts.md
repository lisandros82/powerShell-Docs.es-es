---
title: Conceptos de Cmdlet de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067088"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="14543-102">Conceptos del cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="14543-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="14543-103">En esta sección se describe cómo funcionan los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="14543-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="14543-104">En esta sección</span><span class="sxs-lookup"><span data-stu-id="14543-104">In This Section</span></span>

<span data-ttu-id="14543-105">Esta sección incluye los temas siguientes.</span><span class="sxs-lookup"><span data-stu-id="14543-105">This section includes the following topics.</span></span>

<span data-ttu-id="14543-106">[Las instrucciones de desarrollo de cmdlet](./cmdlet-development-guidelines.md) este tema proporciona directrices de desarrollo que pueden usarse para generar los cmdlets de formato correcto.</span><span class="sxs-lookup"><span data-stu-id="14543-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="14543-107">[Declaración de clase de cmdlet](./cmdlet-class-declaration.md) este tema describe la declaración de clase de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="14543-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="14543-108">[Aprobado verbos para comandos de Windows PowerShell](./approved-verbs-for-windows-powershell-commands.md) en este tema se enumera los verbos de cmdlet predefinidos que puede usar cuando se declara una clase de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="14543-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="14543-109">[Métodos de procesamiento de entrada cmdlet](./cmdlet-input-processing-methods.md) en este tema se describe los métodos que permiten un cmdlet para realizar operaciones de preproceso, las operaciones de procesamiento de entrada y registrar las operaciones de procesamiento.</span><span class="sxs-lookup"><span data-stu-id="14543-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="14543-110">[Los parámetros de cmdlet](./cmdlet-parameters.md) esta sección describen los distintos tipos de parámetros que se pueden agregar a los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="14543-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="14543-111">[Atributos de cmdlet](./cmdlet-attributes.md) en esta sección se describe los atributos que se usan para declarar clases de .NET Framework como cmdlets, para declarar campos como parámetros de cmdlet y declarar las reglas de validación de entrada para los parámetros.</span><span class="sxs-lookup"><span data-stu-id="14543-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="14543-112">[Alias de cmdlet](./cmdlet-aliases.md) en este tema se describe los alias de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="14543-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="14543-113">[Salida del cmdlet](./cmdlet-output.md) en esta sección se describe el tipo de salida devueltos por los cmdlets y cómo definir y mostrar los objetos que se devuelven los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="14543-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="14543-114">[Registrar Cmdlets](./modules-and-snap-ins.md) en esta sección se describe cómo registrar los cmdlets con los módulos y complementos.</span><span class="sxs-lookup"><span data-stu-id="14543-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="14543-115">[Solicitar confirmación](./requesting-confirmation-from-cmdlets.md) en esta sección se describe cómo los cmdlets de solicitar confirmación de un usuario antes de realizar un cambio en el sistema.</span><span class="sxs-lookup"><span data-stu-id="14543-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="14543-116">[Informe de errores de Windows PowerShell](./error-reporting-concepts.md) en esta sección se describe cómo los cmdlets informan de errores de terminación y errores de no terminación y describe cómo interpretar los registros de errores.</span><span class="sxs-lookup"><span data-stu-id="14543-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="14543-117">[Trabajos en segundo plano](./background-jobs.md) este tema describe cómo cmdlets puede llevar a cabo su trabajo en trabajos en segundo plano que no interfieren con los comandos que se ejecutan en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="14543-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="14543-118">[Invocación de Cmdlets y Scripts dentro de un Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) este tema describe cómo los cmdlets pueden invocar otros cmdlets y scripts desde su métodos de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="14543-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="14543-119">[Cmdlet establece](./cmdlet-sets.md) en este tema describe el uso de clases base para crear conjuntos de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="14543-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="14543-120">[Estado de sesión de Windows PowerShell](./windows-powershell-session-state.md) este tema describe el estado de sesión de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14543-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
