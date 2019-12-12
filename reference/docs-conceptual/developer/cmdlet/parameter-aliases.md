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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369594"
---
# <a name="parameter-aliases"></a><span data-ttu-id="c4e53-102">Alias de parámetro</span><span class="sxs-lookup"><span data-stu-id="c4e53-102">Parameter Aliases</span></span>

<span data-ttu-id="c4e53-103">Los parámetros de cmdlet pueden tener también alias.</span><span class="sxs-lookup"><span data-stu-id="c4e53-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="c4e53-104">Puede usar los alias en lugar de los nombres de parámetro al escribir o especificar el parámetro en un comando.</span><span class="sxs-lookup"><span data-stu-id="c4e53-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="c4e53-105">Ventajas del uso de alias</span><span class="sxs-lookup"><span data-stu-id="c4e53-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="c4e53-106">Agregar alias a parámetros proporciona las siguientes ventajas.</span><span class="sxs-lookup"><span data-stu-id="c4e53-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="c4e53-107">Puede proporcionar un acceso directo para que el usuario no tenga que usar el nombre de parámetro completo cuando se llame al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c4e53-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="c4e53-108">Por ejemplo, puede usar el alias "CN" en lugar del nombre de parámetro "ComputerName".</span><span class="sxs-lookup"><span data-stu-id="c4e53-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="c4e53-109">Puede definir varios alias si desea proporcionar nombres diferentes para el mismo parámetro.</span><span class="sxs-lookup"><span data-stu-id="c4e53-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="c4e53-110">Es posible que desee definir varios alias si tiene que trabajar con varios grupos de usuarios que hacen referencia a los mismos datos de maneras diferentes.</span><span class="sxs-lookup"><span data-stu-id="c4e53-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="c4e53-111">Puede proporcionar compatibilidad con versiones anteriores de los scripts existentes si cambia el nombre de un parámetro.</span><span class="sxs-lookup"><span data-stu-id="c4e53-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="c4e53-112">Mediante el atributo alias junto con el atributo ValueFromPipelineByName, puede definir un parámetro que permita que el cmdlet se enlace a tipos de objeto diferentes.</span><span class="sxs-lookup"><span data-stu-id="c4e53-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="c4e53-113">Por ejemplo, suponga que tiene dos objetos de tipos diferentes y el primer objeto tenía una propiedad Writer y el segundo objeto tenía una propiedad editor.</span><span class="sxs-lookup"><span data-stu-id="c4e53-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="c4e53-114">Si el cmdlet tenía un parámetro que tenía los alias del escritor y del editor y el cmdlet aceptó la entrada de canalización en función de los nombres de propiedad, el cmdlet podría enlazarse a ambos objetos mediante los dos alias de parámetro.</span><span class="sxs-lookup"><span data-stu-id="c4e53-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="c4e53-115">Para obtener más información acerca de los alias que se pueden usar con parámetros específicos, vea [nombres de parámetros comunes](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="c4e53-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="c4e53-116">Definir los alias de parámetro</span><span class="sxs-lookup"><span data-stu-id="c4e53-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="c4e53-117">Para definir un alias para un parámetro, declare el atributo alias, tal como se muestra en la siguiente declaración de parámetro.</span><span class="sxs-lookup"><span data-stu-id="c4e53-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="c4e53-118">En este ejemplo, se definen varios alias para el mismo parámetro.</span><span class="sxs-lookup"><span data-stu-id="c4e53-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="c4e53-119">(Para obtener más información, vea[cómo declarar parámetros de cmdlet](./how-to-declare-cmdlet-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="c4e53-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c4e53-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="c4e53-120">See Also</span></span>

[<span data-ttu-id="c4e53-121">Nombres de parámetros comunes</span><span class="sxs-lookup"><span data-stu-id="c4e53-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="c4e53-122">Cómo declarar parámetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="c4e53-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="c4e53-123">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4e53-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
