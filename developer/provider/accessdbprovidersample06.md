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
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080992"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="7cb8f-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="7cb8f-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="7cb8f-103">En este ejemplo se muestra cómo sobrescribir métodos de contenido para admitir llamadas a la `Clear-Content`, `Get-Content`, y `Set-Content` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="7cb8f-104">Estos métodos deberían implementarse cuando el usuario necesite administrar el contenido de los elementos en el almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="7cb8f-105">La clase de proveedor en este ejemplo se deriva de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase e implementa el [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaz.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7cb8f-106">Muestra</span><span class="sxs-lookup"><span data-stu-id="7cb8f-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7cb8f-107">La clase de proveedor se más probable es que se derive de una de las siguientes clases y posiblemente implementar otras interfaces de proveedor:</span><span class="sxs-lookup"><span data-stu-id="7cb8f-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="7cb8f-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="7cb8f-109">Consulte [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="7cb8f-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="7cb8f-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="7cb8f-111">Consulte [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="7cb8f-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="7cb8f-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="7cb8f-113">Para obtener más información acerca de cómo elegir qué clase de proveedor para derivar según las características del proveedor, consulte [diseñar su proveedor de Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="7cb8f-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="7cb8f-114">Este ejemplo muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7cb8f-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="7cb8f-115">Declarar el `CmdletProvider` atributo.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="7cb8f-116">Definir una clase de proveedor que se deriva el [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase y que declara el [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaz.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="7cb8f-117">Sobrescribiendo el [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método para cambiar el comportamiento de la `Clear-Content` cmdlet, que permite al usuario quitar el contenido de un elemento.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="7cb8f-118">(Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Clear-Content` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="7cb8f-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="7cb8f-119">Sobrescribiendo el [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método para cambiar el comportamiento de la `Get-Content` cmdlet, que permite al usuario recuperar el contenido de un elemento.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="7cb8f-120">(Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Get-Content` cmdlet.).</span><span class="sxs-lookup"><span data-stu-id="7cb8f-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="7cb8f-121">Sobrescribiendo el [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) método para cambiar el comportamiento de la `Set-Content` cmdlet, que permite al usuario actualizar el contenido de un elemento.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="7cb8f-122">(Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Set-Content` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="7cb8f-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="7cb8f-123">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7cb8f-123">Example</span></span>

<span data-ttu-id="7cb8f-124">Este ejemplo muestra cómo sobrescribir los métodos necesarios para borrar, obtener y establecer el contenido de elementos de datos Microsoft Access base.</span><span class="sxs-lookup"><span data-stu-id="7cb8f-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="7cb8f-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="7cb8f-125">See Also</span></span>

[<span data-ttu-id="7cb8f-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7cb8f-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="7cb8f-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7cb8f-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="7cb8f-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7cb8f-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="7cb8f-129">Diseñar el proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7cb8f-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)