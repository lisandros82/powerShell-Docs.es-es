---
title: Windows PowerShell conceptos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: c4b13518ad6452a39ca49e897e1d3e353818d332
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081043"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="3257d-102">Conceptos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3257d-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="3257d-103">Esta sección contiene información conceptual que le ayudará a entender Windows PowerShell desde el punto de vista de un desarrollador.</span><span class="sxs-lookup"><span data-stu-id="3257d-103">This section contains conceptual information that will help you understand Windows PowerShell from the viewpoint of a developer.</span></span>

|<span data-ttu-id="3257d-104">Nombre del tema</span><span class="sxs-lookup"><span data-stu-id="3257d-104">Topic Name</span></span>|<span data-ttu-id="3257d-105">Descripción</span><span class="sxs-lookup"><span data-stu-id="3257d-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="3257d-106">Proveedores de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3257d-106">Windows PowerShell Providers</span></span>](http://msdn.microsoft.com/en-us/a65c5c75-1131-4ade-90d3-a613dbe620e9)|<span data-ttu-id="3257d-107">Almacena una discusión sobre los proveedores de Windows PowerShell que se usan para tener acceso a datos.</span><span class="sxs-lookup"><span data-stu-id="3257d-107">A discussion about Windows PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="3257d-108">Complementos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3257d-108">Windows PowerShell Snap-ins</span></span>](http://msdn.microsoft.com/en-us/20e081a9-522c-48bf-9f21-faaf8cca2e82)|<span data-ttu-id="3257d-109">Un mecanismo para registrar los cmdlets y proveedores.</span><span class="sxs-lookup"><span data-stu-id="3257d-109">A mechanism for registering cmdlets and providers.</span></span> <span data-ttu-id="3257d-110">(Vea también, [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).)</span><span class="sxs-lookup"><span data-stu-id="3257d-110">(See also, [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).)</span></span>|
|[<span data-ttu-id="3257d-111">Tiempo de ejecución de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3257d-111">Windows PowerShell Runtime</span></span>](http://msdn.microsoft.com/en-us/949f06e8-0224-4cd3-bbad-a0cebbb5dec8)|<span data-ttu-id="3257d-112">La instancia actual de espacio de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3257d-112">The current instance of the Windows PowerShell runspace.</span></span>|
|[<span data-ttu-id="3257d-113">Espacios de ejecución de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3257d-113">Windows PowerShell Runspaces</span></span>](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9)|<span data-ttu-id="3257d-114">Los entornos operativos que se procesan los comandos.</span><span class="sxs-lookup"><span data-stu-id="3257d-114">The operating environments where commands are processed.</span></span>|
|[<span data-ttu-id="3257d-115">Espacios de nombres de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3257d-115">Windows PowerShell Namespaces</span></span>](http://msdn.microsoft.com/en-us/04bd2841-e90c-47d2-8a1f-3aeb3df35176)|<span data-ttu-id="3257d-116">Información general de los espacios de nombres de la API de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3257d-116">Overview of Windows PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="3257d-117">Ayuda de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3257d-117">Windows PowerShell Help</span></span>](http://msdn.microsoft.com/en-us/097b7c1c-a056-4b36-9c86-65b2ee702fc7)|<span data-ttu-id="3257d-118">Una discusión sobre cómo escribir ayuda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3257d-118">A discussion about writing cmdlet Help.</span></span>|
|[<span data-ttu-id="3257d-119">Solicitar confirmación</span><span class="sxs-lookup"><span data-stu-id="3257d-119">Requesting Confirmation</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="3257d-120">Se toma una discusión acerca de cómo los cmdlets y proveedores de solicitan comentarios al usuario antes de una acción.</span><span class="sxs-lookup"><span data-stu-id="3257d-120">A discussion about how cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="3257d-121">Conceptos de objeto de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="3257d-121">Windows PowerShell Object Concepts</span></span>](http://msdn.microsoft.com/en-us/a1449178-b6fd-4ca8-a5e1-d747c2c54181)|<span data-ttu-id="3257d-122">Cómo Windows PowerShell administra los objetos.</span><span class="sxs-lookup"><span data-stu-id="3257d-122">How Windows PowerShell handles objects.</span></span>|
|[<span data-ttu-id="3257d-123">PowerShell de Windows extendido (ETS) del sistema de tipos</span><span class="sxs-lookup"><span data-stu-id="3257d-123">Windows PowerShell Extended Type System (ETS)</span></span>](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353)|<span data-ttu-id="3257d-124">Ampliación mediante programación de objetos.</span><span class="sxs-lookup"><span data-stu-id="3257d-124">Programmatically extending objects.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3257d-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="3257d-125">See Also</span></span>

[<span data-ttu-id="3257d-126">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3257d-126">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)