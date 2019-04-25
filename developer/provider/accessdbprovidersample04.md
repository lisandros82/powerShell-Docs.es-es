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
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081032"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="f702a-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="f702a-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="f702a-103">Este ejemplo muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a la `Copy-Item`, `Get-ChildItem`, `New-Item`, y `Remove-Item` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f702a-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="f702a-104">Estos métodos deberían implementarse cuando el almacén de datos contengan elementos que son contenedores.</span><span class="sxs-lookup"><span data-stu-id="f702a-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="f702a-105">Un contenedor es un grupo de elementos secundarios con un elemento primario común.</span><span class="sxs-lookup"><span data-stu-id="f702a-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="f702a-106">La clase de proveedor en este ejemplo se deriva de la [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="f702a-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f702a-107">Muestra</span><span class="sxs-lookup"><span data-stu-id="f702a-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f702a-108">Probablemente se derivará la clase de proveedor de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="f702a-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="f702a-109">Este ejemplo muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="f702a-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="f702a-110">Declarar el `CmdletProvider` atributo.</span><span class="sxs-lookup"><span data-stu-id="f702a-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="f702a-111">Definir una clase de proveedor que se deriva el [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="f702a-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="f702a-112">Sobrescribiendo el [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método para cambiar el comportamiento de la `Copy-Item` cmdlet que permite al usuario copiar los elementos de una ubicación a otra.</span><span class="sxs-lookup"><span data-stu-id="f702a-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="f702a-113">(Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Copy-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="f702a-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="f702a-114">Sobrescribiendo el [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método para cambiar el comportamiento del cmdlet Get-ChildItems, lo que permite al usuario recuperar los elementos secundarios del elemento primario .</span><span class="sxs-lookup"><span data-stu-id="f702a-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="f702a-115">(Este ejemplo no muestra cómo agregar parámetros dinámicos al cmdlet Get-ChildItems).</span><span class="sxs-lookup"><span data-stu-id="f702a-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="f702a-116">Sobrescribiendo el [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método para cambiar el comportamiento del cmdlet Get-ChildItems cuando el `Name` se especifica el parámetro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f702a-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="f702a-117">Sobrescribiendo el [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método para cambiar el comportamiento de la `New-Item` cmdlet, que permite al usuario agregar elementos al almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="f702a-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="f702a-118">(Este ejemplo no muestra cómo agregar parámetros dinámicos a la `New-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="f702a-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="f702a-119">Sobrescribiendo el [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método para cambiar el comportamiento de la `Remove-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f702a-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="f702a-120">(Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Remove-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="f702a-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="f702a-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f702a-121">Example</span></span>

<span data-ttu-id="f702a-122">Este ejemplo muestra cómo sobrescribir los métodos necesarios para copiar, crear y quitar elementos, así como métodos para obtener al elemento secundario de los elementos de un elemento primario.</span><span class="sxs-lookup"><span data-stu-id="f702a-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="f702a-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="f702a-123">See Also</span></span>

[<span data-ttu-id="f702a-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f702a-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="f702a-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f702a-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="f702a-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f702a-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="f702a-127">Diseñar el proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f702a-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)