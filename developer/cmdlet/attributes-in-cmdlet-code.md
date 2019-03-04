---
title: Atributos en el código del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853791"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="2a22f-102">Atributos en el código del cmdlet</span><span class="sxs-lookup"><span data-stu-id="2a22f-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="2a22f-103">Para usar la funcionalidad común proporcionada por Windows PowerShell, las clases y propiedades públicas definidas en el código del cmdlet se decoran con atributos.</span><span class="sxs-lookup"><span data-stu-id="2a22f-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="2a22f-104">Por ejemplo, la definición de clase siguiente utiliza el atributo de Cmdlet para identificar la clase Microsoft .NET Framework en el que el **Get-Proc** cmdlet se implementa.</span><span class="sxs-lookup"><span data-stu-id="2a22f-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="2a22f-105">(Este cmdlet se usa como un ejemplo de este documento y es similar a la `Get-Process` cmdlet proporcionado por Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="2a22f-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="2a22f-106">Estos atributos se consideran los metadatos porque su implementación es independiente de la implementación del código del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2a22f-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="2a22f-107">Cuando el tiempo de ejecución de Windows PowerShell ejecuta el cmdlet, reconoce los atributos y, a continuación, realiza la acción adecuada para cada atributo.</span><span class="sxs-lookup"><span data-stu-id="2a22f-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="2a22f-108">Aunque es posible que desee implementar su propia versión de la funcionalidad proporcionada por estos atributos, el diseño de una buena cmdlet utiliza estas funcionalidades comunes.</span><span class="sxs-lookup"><span data-stu-id="2a22f-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="2a22f-109">Para obtener más información sobre los atributos diferentes que se pueden declarar en los cmdlets, consulte [tipos de atributo](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="2a22f-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a22f-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="2a22f-110">See Also</span></span>

[<span data-ttu-id="2a22f-111">Tipos de atributos</span><span class="sxs-lookup"><span data-stu-id="2a22f-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="2a22f-112">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a22f-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
