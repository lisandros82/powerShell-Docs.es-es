---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854161"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="23b9a-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="23b9a-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="23b9a-103">En este ejemplo se muestra cómo declarar una clase de proveedor que derive directamente de la [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="23b9a-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="23b9a-104">Se incluye aquí solo por cuestiones de integridad.</span><span class="sxs-lookup"><span data-stu-id="23b9a-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="23b9a-105">Demostraciones</span><span class="sxs-lookup"><span data-stu-id="23b9a-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23b9a-106">La clase de proveedor se más probable es que se derive de una de las siguientes clases y posiblemente implementar otras interfaces de proveedor:</span><span class="sxs-lookup"><span data-stu-id="23b9a-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="23b9a-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="23b9a-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="23b9a-108">Consulte [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="23b9a-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="23b9a-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="23b9a-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="23b9a-110">Consulte [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="23b9a-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="23b9a-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="23b9a-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="23b9a-112">Consulte [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="23b9a-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="23b9a-113">Para obtener más información acerca de cómo elegir qué clase de proveedor para derivar según las características del proveedor, consulte [diseñar su proveedor de Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="23b9a-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="23b9a-114">Este ejemplo muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="23b9a-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="23b9a-115">Declarar el `CmdletProvider` atributo.</span><span class="sxs-lookup"><span data-stu-id="23b9a-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="23b9a-116">Definir una clase de proveedor que derive directamente de la [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="23b9a-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="23b9a-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="23b9a-117">Example</span></span>

<span data-ttu-id="23b9a-118">Este ejemplo muestra cómo definir una clase de proveedor y cómo se declara el `CmdletProvider` atributo.</span><span class="sxs-lookup"><span data-stu-id="23b9a-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a><span data-ttu-id="23b9a-119">Véase también</span><span class="sxs-lookup"><span data-stu-id="23b9a-119">See Also</span></span>

[<span data-ttu-id="23b9a-120">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="23b9a-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="23b9a-121">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="23b9a-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="23b9a-122">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="23b9a-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="23b9a-123">Diseñar el proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="23b9a-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)