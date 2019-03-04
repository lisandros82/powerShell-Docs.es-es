---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859411"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="36257-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="36257-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="36257-103">Este ejemplo muestra cómo sobrescribir los [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) y [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) métodos para admitir llamadas a la `Get-Item` y `Set-Item` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="36257-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="36257-104">La clase de proveedor en este ejemplo se deriva de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="36257-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="36257-105">Demostraciones</span><span class="sxs-lookup"><span data-stu-id="36257-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36257-106">La clase de proveedor se más probable es que se derive de una de las siguientes clases y posiblemente implementar otras interfaces de proveedor:</span><span class="sxs-lookup"><span data-stu-id="36257-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="36257-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="36257-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="36257-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="36257-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="36257-109">Consulte [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="36257-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="36257-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="36257-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="36257-111">Consulte [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="36257-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="36257-112">Para obtener más información acerca de cómo elegir qué clase de proveedor para derivar según las características del proveedor, consulte [diseñar su proveedor de Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="36257-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="36257-113">Este ejemplo muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="36257-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="36257-114">Declarar el `CmdletProvider` atributo.</span><span class="sxs-lookup"><span data-stu-id="36257-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="36257-115">Definir una clase de proveedor que se deriva el [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="36257-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="36257-116">Sobrescribiendo el [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método para cambiar el comportamiento de la `New-PSDrive` cmdlet, lo que permite al usuario crear nuevas unidades de disco.</span><span class="sxs-lookup"><span data-stu-id="36257-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="36257-117">(Este ejemplo no muestra cómo agregar parámetros dinámicos a la `New-PSDrive` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="36257-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="36257-118">Sobrescribiendo el [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método para admitir la eliminación de unidades de disco existentes.</span><span class="sxs-lookup"><span data-stu-id="36257-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="36257-119">Sobrescribiendo el [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para cambiar el comportamiento de la `Get-Item` cmdlet, que permite al usuario recuperar los elementos del almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="36257-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="36257-120">(Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Get-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="36257-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="36257-121">Sobrescribiendo el [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método para cambiar el comportamiento de la `Set-Item` cmdlet, que permite al usuario actualizar los elementos en el almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="36257-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="36257-122">(Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Get-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="36257-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="36257-123">Sobrescribiendo el [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método para cambiar el comportamiento de la `Test-Path` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36257-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="36257-124">(Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Test-Path` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="36257-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="36257-125">Sobrescribiendo el [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método para determinar si la ruta de acceso proporcionada es válida.</span><span class="sxs-lookup"><span data-stu-id="36257-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="36257-126">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="36257-126">Example</span></span>

<span data-ttu-id="36257-127">Este ejemplo muestra cómo sobrescribir los métodos necesarios para obtener y establecer los elementos de datos Microsoft Access base.</span><span class="sxs-lookup"><span data-stu-id="36257-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="36257-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="36257-128">See Also</span></span>

[<span data-ttu-id="36257-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="36257-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="36257-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="36257-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="36257-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="36257-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="36257-132">Diseñar el proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="36257-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)