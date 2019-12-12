---
title: Conceptos de cmdlets de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369124"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="cd802-102">Conceptos del cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd802-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="cd802-103">En esta sección se describe cómo funcionan los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="cd802-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cd802-104">En esta sección</span><span class="sxs-lookup"><span data-stu-id="cd802-104">In This Section</span></span>

<span data-ttu-id="cd802-105">Esta sección incluye los temas siguientes.</span><span class="sxs-lookup"><span data-stu-id="cd802-105">This section includes the following topics.</span></span>

<span data-ttu-id="cd802-106">[Instrucciones para el desarrollo de cmdlets](./cmdlet-development-guidelines.md) En este tema se proporcionan instrucciones de desarrollo que se pueden usar para generar cmdlets correctos.</span><span class="sxs-lookup"><span data-stu-id="cd802-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="cd802-107">[Declaración de clase de cmdlet](./cmdlet-class-declaration.md) En este tema se describe la declaración de clase de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cd802-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="cd802-108">[Verbos aprobados para comandos de Windows PowerShell](./approved-verbs-for-windows-powershell-commands.md) En este tema se enumeran los verbos de cmdlet predefinidos que se pueden usar cuando se declara una clase de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cd802-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="cd802-109">[Métodos de procesamiento de entrada de cmdlet](./cmdlet-input-processing-methods.md) En este tema se describen los métodos que permiten a un cmdlet realizar operaciones de preprocesamiento, operaciones de procesamiento de entrada y operaciones posteriores al procesamiento.</span><span class="sxs-lookup"><span data-stu-id="cd802-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="cd802-110">[Parámetros de cmdlet](./cmdlet-parameters.md) En esta sección se describen los diferentes tipos de parámetros que se pueden agregar a los cmdlets de.</span><span class="sxs-lookup"><span data-stu-id="cd802-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="cd802-111">[Atributos de cmdlet](./cmdlet-attributes.md) En esta sección se describen los atributos que se usan para declarar .NET Framework clases como cmdlets, para declarar campos como parámetros de cmdlet y para declarar reglas de validación de entrada para parámetros.</span><span class="sxs-lookup"><span data-stu-id="cd802-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="cd802-112">[Alias de cmdlet](./cmdlet-aliases.md) En este tema se describen los alias de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="cd802-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="cd802-113">[Salida del cmdlet](./cmdlet-output.md) En esta sección se describe el tipo de salida que pueden devolver los cmdlets y cómo definir y mostrar los objetos que devuelven los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="cd802-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="cd802-114">[Registrar cmdlets](./modules-and-snap-ins.md) En esta sección se describe cómo registrar cmdlets mediante módulos y complementos.</span><span class="sxs-lookup"><span data-stu-id="cd802-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="cd802-115">[Solicitud de confirmación](./requesting-confirmation-from-cmdlets.md) En esta sección se describe cómo los cmdlets solicitan la confirmación de un usuario antes de que realicen un cambio en el sistema.</span><span class="sxs-lookup"><span data-stu-id="cd802-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="cd802-116">[Informe de errores de Windows PowerShell](./error-reporting-concepts.md) En esta sección se describe cómo los cmdlets notifican los errores de terminación y los errores de no terminación, y se describe cómo interpretar los registros de errores.</span><span class="sxs-lookup"><span data-stu-id="cd802-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="cd802-117">[Trabajos en segundo plano](./background-jobs.md) En este tema se describe cómo los cmdlets pueden realizar su trabajo en los trabajos en segundo plano que no interfieren con los comandos que se ejecutan en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="cd802-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="cd802-118">[Invocar cmdlets y scripts dentro de un cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) En este tema se describe cómo los cmdlets pueden invocar otros cmdlets y scripts desde sus métodos de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="cd802-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="cd802-119">[Conjuntos de cmdlets](./cmdlet-sets.md) En este tema se describe el uso de clases base para crear conjuntos de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="cd802-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="cd802-120">[Estado de sesión de Windows PowerShell](./windows-powershell-session-state.md) En este tema se describe el estado de sesión de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd802-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
