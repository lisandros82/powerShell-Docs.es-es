---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: 9c00ec6de987729fec42dc57245a949d11e31f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366334"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="44a4d-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="44a4d-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="44a4d-103">En este ejemplo se muestra cómo sobrescribir métodos de contenido para admitir llamadas a los cmdlets `Clear-Content`, `Get-Content` y `Set-Content`.</span><span class="sxs-lookup"><span data-stu-id="44a4d-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="44a4d-104">Estos métodos deberían implementarse cuando el usuario necesite administrar el contenido de los elementos en el almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="44a4d-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="44a4d-105">La clase de proveedor de este ejemplo se deriva de la clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) e implementa la interfaz [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="44a4d-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="44a4d-106">Demuestra</span><span class="sxs-lookup"><span data-stu-id="44a4d-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44a4d-107">Lo más probable es que la clase de proveedor derive de una de las siguientes clases y, posiblemente, implemente otras interfaces de proveedor:</span><span class="sxs-lookup"><span data-stu-id="44a4d-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="44a4d-108">Clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="44a4d-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="44a4d-109">Vea [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="44a4d-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="44a4d-110">Clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="44a4d-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="44a4d-111">Vea [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="44a4d-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="44a4d-112">Clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="44a4d-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="44a4d-113">Para obtener más información sobre cómo elegir la clase de proveedor que se va a derivar en función de las características del proveedor, vea [diseñar un proveedor de Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="44a4d-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="44a4d-114">Este ejemplo muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="44a4d-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="44a4d-115">Declarar el atributo `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="44a4d-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="44a4d-116">Definir una clase de proveedor que se deriva de la clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) y que declara la interfaz [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="44a4d-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="44a4d-117">Sobrescribir el método [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) para cambiar el comportamiento del cmdlet `Clear-Content`, lo que permite al usuario quitar el contenido de un elemento.</span><span class="sxs-lookup"><span data-stu-id="44a4d-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="44a4d-118">(En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Clear-Content`).</span><span class="sxs-lookup"><span data-stu-id="44a4d-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="44a4d-119">Sobrescribir el método [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) para cambiar el comportamiento del cmdlet `Get-Content`, lo que permite al usuario recuperar el contenido de un elemento.</span><span class="sxs-lookup"><span data-stu-id="44a4d-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="44a4d-120">(En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Get-Content`).</span><span class="sxs-lookup"><span data-stu-id="44a4d-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="44a4d-121">Sobrescribir el método [Microsoft. PowerShell. Commands. Filesystemprovider. Getcontentwriter \*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) para cambiar el comportamiento del cmdlet `Set-Content`, lo que permite al usuario actualizar el contenido de un elemento.</span><span class="sxs-lookup"><span data-stu-id="44a4d-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="44a4d-122">(En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Set-Content`).</span><span class="sxs-lookup"><span data-stu-id="44a4d-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="44a4d-123">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="44a4d-123">Example</span></span>

<span data-ttu-id="44a4d-124">En este ejemplo se muestra cómo sobrescribir los métodos necesarios para borrar, obtener y establecer el contenido de los elementos en una base de datos de Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="44a4d-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="44a4d-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="44a4d-125">See Also</span></span>

[<span data-ttu-id="44a4d-126">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="44a4d-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="44a4d-127">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="44a4d-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="44a4d-128">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="44a4d-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="44a4d-129">Diseño del proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="44a4d-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
