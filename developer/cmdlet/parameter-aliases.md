---
title: Alias de parámetro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067593"
---
# <a name="parameter-aliases"></a><span data-ttu-id="31668-102">Alias de parámetro</span><span class="sxs-lookup"><span data-stu-id="31668-102">Parameter Aliases</span></span>

<span data-ttu-id="31668-103">Los parámetros de cmdlet pueden tener también alias.</span><span class="sxs-lookup"><span data-stu-id="31668-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="31668-104">Puede usar los alias en lugar de los nombres de parámetro cuando escriba o especifique el parámetro en un comando.</span><span class="sxs-lookup"><span data-stu-id="31668-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="31668-105">Ventajas del uso de alias</span><span class="sxs-lookup"><span data-stu-id="31668-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="31668-106">Agregar alias a parámetros proporciona las siguientes ventajas.</span><span class="sxs-lookup"><span data-stu-id="31668-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="31668-107">Puede proporcionar un acceso directo para que el usuario no tiene que usar el nombre de parámetro completo cuando se llama el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31668-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="31668-108">Por ejemplo, podría utilizar el alias "CN" en lugar del nombre de parámetro "ComputerName".</span><span class="sxs-lookup"><span data-stu-id="31668-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="31668-109">Puede definir varios alias si desea proporcionar distintos nombres para el mismo parámetro.</span><span class="sxs-lookup"><span data-stu-id="31668-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="31668-110">Es posible que desee definir varios alias si tiene que trabajar con varios grupos de usuarios que hacen referencia a los mismos datos de maneras diferentes.</span><span class="sxs-lookup"><span data-stu-id="31668-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="31668-111">Se puede proporcionar compatibilidad hacia atrás para secuencias de comandos existentes si cambia el nombre de un parámetro.</span><span class="sxs-lookup"><span data-stu-id="31668-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="31668-112">Al usar el Alias (atributo) junto con el atributo ValueFromPipelineByName, puede definir un parámetro que permite que el cmdlet enlazar con diferentes tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="31668-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="31668-113">Por ejemplo, supongamos que tuviera dos objetos de distintos tipos y el primer objeto tenía una propiedad de sistema de escritura y el segundo objeto tenía una propiedad del editor.</span><span class="sxs-lookup"><span data-stu-id="31668-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="31668-114">Si su cmdlet tenía un parámetro que tenían los alias de autor y editor y el cmdlet aceptan entrada de la canalización basada en nombres de propiedad, su cmdlet podría enlazar a los objetos mediante los dos alias de parámetro.</span><span class="sxs-lookup"><span data-stu-id="31668-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="31668-115">Para obtener más información sobre los alias que puede usarse con parámetros específicos, consulte [comunes de los nombres de parámetro](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="31668-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="31668-116">Definir los alias de parámetro</span><span class="sxs-lookup"><span data-stu-id="31668-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="31668-117">Para definir un alias para un parámetro, declare el atributo de Alias, como se muestra en la siguiente declaración de parámetro.</span><span class="sxs-lookup"><span data-stu-id="31668-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="31668-118">En este ejemplo, se definen varios alias para el mismo parámetro.</span><span class="sxs-lookup"><span data-stu-id="31668-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="31668-119">(Para obtener más información, consulte[cómo declarar los parámetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="31668-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="31668-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="31668-120">See Also</span></span>

[<span data-ttu-id="31668-121">Nombres de parámetro comunes</span><span class="sxs-lookup"><span data-stu-id="31668-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="31668-122">Cómo declarar los parámetros de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="31668-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="31668-123">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="31668-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
