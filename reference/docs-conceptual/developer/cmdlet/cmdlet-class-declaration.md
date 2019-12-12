---
title: Declaración de clase de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 979025ad5c34ab73dcc23d0e38ffb9acc431f15a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363524"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="8d287-102">Declaración de clase del cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d287-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="8d287-103">Una clase de marco de Microsoft .NET se declara como un cmdlet especificando el atributo del **cmdlet** como metadatos para la clase.</span><span class="sxs-lookup"><span data-stu-id="8d287-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="8d287-104">(El atributo **cmdlet** es el único atributo necesario para todos los cmdlets).</span><span class="sxs-lookup"><span data-stu-id="8d287-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="8d287-105">Al especificar el atributo del **cmdlet** , debe especificar el par verbo-y-sustantivo que identifica el cmdlet para el usuario.</span><span class="sxs-lookup"><span data-stu-id="8d287-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="8d287-106">Además, debe describir la funcionalidad de Windows PowerShell que admite el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d287-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="8d287-107">Para obtener más información sobre la sintaxis de declaración que se usa para especificar el atributo de **cmdlet** , vea [declaración de atributo de cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8d287-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8d287-108">El atributo **cmdlet** se define mediante la clase [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="8d287-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="8d287-109">Las propiedades de esta clase corresponden a los parámetros de declaración que se utilizan al declarar el atributo.</span><span class="sxs-lookup"><span data-stu-id="8d287-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="8d287-110">Sustantivos</span><span class="sxs-lookup"><span data-stu-id="8d287-110">Nouns</span></span>

<span data-ttu-id="8d287-111">El nombre del cmdlet especifica los recursos en los que actúa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d287-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="8d287-112">El nombre diferencia los cmdlets de otros cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8d287-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="8d287-113">Los nombres de los nombres de cmdlet deben ser específicos y, en el caso de nombres genéricos, como *Server*, es mejor agregar un prefijo corto que diferencie el recurso de otros recursos similares.</span><span class="sxs-lookup"><span data-stu-id="8d287-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="8d287-114">Por ejemplo, un nombre de cmdlet que incluye un sustantivo con un prefijo es `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="8d287-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="8d287-115">La combinación de un sustantivo específico con un verbo más general permite al usuario localizar rápidamente el cmdlet por su acción y, a continuación, identificar el cmdlet por su recurso y evitar la duplicación de nombres de cmdlets innecesarios.</span><span class="sxs-lookup"><span data-stu-id="8d287-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="8d287-116">Para obtener una lista de los caracteres especiales que no se pueden usar en los nombres de cmdlet, consulte las [directrices de desarrollo necesarias](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="8d287-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="8d287-117">Verbos</span><span class="sxs-lookup"><span data-stu-id="8d287-117">Verbs</span></span>

<span data-ttu-id="8d287-118">Cuando se especifica un verbo, las instrucciones de desarrollo requieren el uso de uno de los verbos predefinidos proporcionados por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d287-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="8d287-119">Al usar uno de estos verbos predefinidos, se garantiza la coherencia entre los cmdlets que se escriben y los cmdlets escritos por Microsoft y por otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="8d287-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="8d287-120">Por ejemplo, el verbo "Get" se usa para los cmdlets que recuperan datos.</span><span class="sxs-lookup"><span data-stu-id="8d287-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="8d287-121">Para obtener más información sobre las directrices para los verbos, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="8d287-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="8d287-122">Para obtener una lista de los caracteres especiales que no se pueden usar en los nombres de cmdlet, consulte las [directrices de desarrollo necesarias](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="8d287-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="8d287-123">Compatibilidad con la funcionalidad de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d287-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="8d287-124">El atributo **cmdlet** también le permite especificar que el cmdlet admite parte de la funcionalidad común proporcionada por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d287-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="8d287-125">Esto incluye compatibilidad con la funcionalidad común, como la confirmación de comentarios de usuario (denominada compatibilidad con la característica ShouldProcess) y la compatibilidad con transacciones.</span><span class="sxs-lookup"><span data-stu-id="8d287-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="8d287-126">(La compatibilidad con transacciones se presentó en Windows PowerShell 2,0).</span><span class="sxs-lookup"><span data-stu-id="8d287-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="8d287-127">Para obtener más información sobre la sintaxis de declaración que se usa para especificar el atributo de **cmdlet** , vea [declaración de atributo de cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8d287-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="8d287-128">Definición de la clase de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d287-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="8d287-129">El código siguiente es la definición de una clase de cmdlet de GetProc.</span><span class="sxs-lookup"><span data-stu-id="8d287-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="8d287-130">Observe que se usa la grafía Pascal y que el nombre de la clase incluye el verbo y el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d287-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="8d287-131">Mayúsculas y minúsculas Pascal</span><span class="sxs-lookup"><span data-stu-id="8d287-131">Pascal Casing</span></span>

<span data-ttu-id="8d287-132">Cuando asigne nombre a los cmdlets, utilice la grafía Pascal.</span><span class="sxs-lookup"><span data-stu-id="8d287-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="8d287-133">Por ejemplo, los cmdlets `Get-Item` y `Get-ItemProperty` muestran la manera correcta de usar las mayúsculas y minúsculas al asignar nombres a los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8d287-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d287-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="8d287-134">See Also</span></span>

[<span data-ttu-id="8d287-135">System. Management. Automation. CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="8d287-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="8d287-136">Declaración de CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="8d287-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="8d287-137">Nombres de verbo de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d287-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="8d287-138">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d287-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="8d287-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8d287-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
