---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: 7096f8066568c214a5902f6943a2c093932d3b56
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366344"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="8806d-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="8806d-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="8806d-103">En este ejemplo se muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a los cmdlets `Copy-Item`, `Get-ChildItem`, `New-Item` y `Remove-Item`.</span><span class="sxs-lookup"><span data-stu-id="8806d-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="8806d-104">Estos métodos deberían implementarse cuando el almacén de datos contengan elementos que son contenedores.</span><span class="sxs-lookup"><span data-stu-id="8806d-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="8806d-105">Un contenedor es un grupo de elementos secundarios con un elemento primario común.</span><span class="sxs-lookup"><span data-stu-id="8806d-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="8806d-106">La clase de proveedor de este ejemplo se deriva de la clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="8806d-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8806d-107">Demuestra</span><span class="sxs-lookup"><span data-stu-id="8806d-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8806d-108">Lo más probable es que la clase de proveedor derive de [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="8806d-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="8806d-109">Este ejemplo muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="8806d-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="8806d-110">Declarar el atributo `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="8806d-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="8806d-111">Definir una clase de proveedor que se deriva de la clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="8806d-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="8806d-112">Sobrescribir el método [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) para cambiar el comportamiento del cmdlet `Copy-Item` que permite al usuario copiar elementos de una ubicación a otra.</span><span class="sxs-lookup"><span data-stu-id="8806d-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="8806d-113">(En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Copy-Item`).</span><span class="sxs-lookup"><span data-stu-id="8806d-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="8806d-114">Sobrescribir el método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) para cambiar el comportamiento del cmdlet Get-ChildItems, que permite al usuario recuperar los elementos secundarios del elemento primario.</span><span class="sxs-lookup"><span data-stu-id="8806d-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="8806d-115">(En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet Get-ChildItems).</span><span class="sxs-lookup"><span data-stu-id="8806d-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="8806d-116">Sobrescribir el método [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) para cambiar el comportamiento del cmdlet Get-ChildItems cuando se especifica el parámetro `Name` del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8806d-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="8806d-117">Sobrescribir el método [System. Management. Automation. Provider. Containercmdletprovider. newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) para cambiar el comportamiento del cmdlet `New-Item`, que permite al usuario agregar elementos al almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="8806d-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="8806d-118">(En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `New-Item`).</span><span class="sxs-lookup"><span data-stu-id="8806d-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="8806d-119">Sobrescribir el método [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) para cambiar el comportamiento del cmdlet `Remove-Item`.</span><span class="sxs-lookup"><span data-stu-id="8806d-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="8806d-120">(En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Remove-Item`).</span><span class="sxs-lookup"><span data-stu-id="8806d-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="8806d-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8806d-121">Example</span></span>

<span data-ttu-id="8806d-122">En este ejemplo se muestra cómo sobrescribir los métodos necesarios para copiar, crear y quitar elementos, así como métodos para obtener los elementos secundarios de un elemento primario.</span><span class="sxs-lookup"><span data-stu-id="8806d-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="8806d-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="8806d-123">See Also</span></span>

[<span data-ttu-id="8806d-124">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8806d-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="8806d-125">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8806d-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="8806d-126">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8806d-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="8806d-127">Diseño del proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8806d-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
