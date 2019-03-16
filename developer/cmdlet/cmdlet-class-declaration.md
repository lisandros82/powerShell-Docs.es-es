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
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055094"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="9c51c-102">Declaración de clase del cmdlet</span><span class="sxs-lookup"><span data-stu-id="9c51c-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="9c51c-103">Una clase de Microsoft .NET Framework se declara como un cmdlet especificando el **Cmdlet** atributo como metadatos de la clase.</span><span class="sxs-lookup"><span data-stu-id="9c51c-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="9c51c-104">(El **Cmdlet** atributo es el único atributo obligatorio para todos los cmdlets).</span><span class="sxs-lookup"><span data-stu-id="9c51c-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="9c51c-105">Al especificar el **Cmdlet** atributo, debe especificar el par de verbo y sustantivo que identifica el cmdlet para el usuario.</span><span class="sxs-lookup"><span data-stu-id="9c51c-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="9c51c-106">Y debe describir la funcionalidad de Windows PowerShell que es compatible con el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c51c-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="9c51c-107">Para obtener más información sobre la sintaxis de declaración que se usa para especificar el **Cmdlet** atributo, vea [declaración de atributo de Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9c51c-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9c51c-108">El **Cmdlet** atributo está definido por el [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) clase.</span><span class="sxs-lookup"><span data-stu-id="9c51c-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="9c51c-109">Las propiedades de esta clase se corresponden a los parámetros de declaración que se usan cuando se declara el atributo.</span><span class="sxs-lookup"><span data-stu-id="9c51c-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="9c51c-110">Sustantivos</span><span class="sxs-lookup"><span data-stu-id="9c51c-110">Nouns</span></span>

<span data-ttu-id="9c51c-111">El nombre del cmdlet especifica los recursos en el que actúa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c51c-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="9c51c-112">El término marca la diferencia de los cmdlets de otros cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9c51c-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="9c51c-113">Deben ser sustantivos en los nombres de cmdlet específico y en el caso de los nombres genéricos, como *server*, es aconsejable agregar un prefijo corto que diferencia a los recursos de otros recursos similares.</span><span class="sxs-lookup"><span data-stu-id="9c51c-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="9c51c-114">Por ejemplo, es un nombre de cmdlet que incluye un nombre con un prefijo `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="9c51c-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="9c51c-115">La combinación de un sustantivo específico con un verbo más general permite al usuario localizar rápidamente el cmdlet por su acción y, a continuación, identifique el cmdlet por sus recursos al evitar la duplicación de nombre de cmdlet innecesarios.</span><span class="sxs-lookup"><span data-stu-id="9c51c-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="9c51c-116">Para obtener una lista de caracteres especiales que no se puede usar en los nombres de cmdlet, consulte [las instrucciones de desarrollo necesario](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="9c51c-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="9c51c-117">Verbos</span><span class="sxs-lookup"><span data-stu-id="9c51c-117">Verbs</span></span>

<span data-ttu-id="9c51c-118">Cuando se especifica un verbo, las directrices de desarrollo requieren que se use uno de los verbos predefinidos proporcionados por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c51c-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="9c51c-119">Al usar uno de estos verbos predefinidos, garantizará la coherencia entre los cmdlets que escribe y los cmdlets que se escriben por Microsoft y otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="9c51c-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="9c51c-120">Por ejemplo, el verbo "Get" se usa para los cmdlets que recuperar datos.</span><span class="sxs-lookup"><span data-stu-id="9c51c-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="9c51c-121">Para obtener más información acerca de las instrucciones para los verbos, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="9c51c-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="9c51c-122">Para obtener una lista de caracteres especiales que no se puede usar en los nombres de cmdlet, consulte [las instrucciones de desarrollo necesario](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="9c51c-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="9c51c-123">Compatibilidad con la funcionalidad de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c51c-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="9c51c-124">El **Cmdlet** atributo también permite especificar que el cmdlet admite parte de la funcionalidad común proporcionada por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c51c-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="9c51c-125">Esto incluye compatibilidad para funciones comunes como la confirmación de comentarios del usuario (denominado compatibilidad con la característica ShouldProcess) y compatibilidad con transacciones.</span><span class="sxs-lookup"><span data-stu-id="9c51c-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="9c51c-126">(La compatibilidad con las transacciones se introdujo en Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="9c51c-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="9c51c-127">Para obtener más información sobre la sintaxis de declaración que se usa para especificar el **Cmdlet** atributo, vea [declaración de atributo de Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9c51c-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="9c51c-128">Definición de clase de cmdlet</span><span class="sxs-lookup"><span data-stu-id="9c51c-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="9c51c-129">El código siguiente es la definición para una clase de cmdlet GetProc.</span><span class="sxs-lookup"><span data-stu-id="9c51c-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="9c51c-130">Tenga en cuenta que se utilizan mayúsculas y minúsculas de Pascal y que el nombre de la clase incluye el verbo y sustantivo del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c51c-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="9c51c-131">Mayúsculas y minúsculas de Pascal</span><span class="sxs-lookup"><span data-stu-id="9c51c-131">Pascal Casing</span></span>

<span data-ttu-id="9c51c-132">Cuando asigne nombre a los cmdlets, use casillas Pascal mayúsculas y minúsculas.</span><span class="sxs-lookup"><span data-stu-id="9c51c-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="9c51c-133">Por ejemplo, el `Get-Item` y `Get-ItemProperty` cmdlets muestran la manera correcta de utilizar las mayúsculas y minúsculas al asignar nombres a los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9c51c-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c51c-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="9c51c-134">See Also</span></span>

[<span data-ttu-id="9c51c-135">System.Management.Automation.CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="9c51c-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="9c51c-136">Declaración CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="9c51c-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="9c51c-137">Nombres de verbo del cmdlet</span><span class="sxs-lookup"><span data-stu-id="9c51c-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="9c51c-138">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c51c-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="9c51c-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9c51c-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
