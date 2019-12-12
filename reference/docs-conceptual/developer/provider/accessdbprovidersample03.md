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
ms.openlocfilehash: aa67bb605f90c1ea40323b4583766069ff1226fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359994"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="3057f-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="3057f-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="3057f-103">En este ejemplo se muestra cómo sobrescribir los métodos [System. Management. Automation. Provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) y [System. Management. Automation. Provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) para admitir llamadas a los cmdlets `Get-Item` y `Set-Item`.</span><span class="sxs-lookup"><span data-stu-id="3057f-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="3057f-104">La clase de proveedor de este ejemplo se deriva de la clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="3057f-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3057f-105">Demuestra</span><span class="sxs-lookup"><span data-stu-id="3057f-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3057f-106">Lo más probable es que la clase de proveedor derive de una de las siguientes clases y, posiblemente, implemente otras interfaces de proveedor:</span><span class="sxs-lookup"><span data-stu-id="3057f-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="3057f-107">Clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="3057f-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="3057f-108">Clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="3057f-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="3057f-109">Vea [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="3057f-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="3057f-110">Clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="3057f-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="3057f-111">Vea [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="3057f-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="3057f-112">Para obtener más información sobre cómo elegir la clase de proveedor que se va a derivar en función de las características del proveedor, vea [diseñar un proveedor de Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="3057f-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="3057f-113">Este ejemplo muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3057f-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="3057f-114">Declarar el atributo de `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="3057f-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="3057f-115">Definir una clase de proveedor que se deriva de la clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="3057f-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="3057f-116">Sobrescribir el método [System. Management. Automation. Provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) para cambiar el comportamiento del cmdlet `New-PSDrive`, lo que permite al usuario crear nuevas unidades.</span><span class="sxs-lookup"><span data-stu-id="3057f-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="3057f-117">(En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `New-PSDrive`).</span><span class="sxs-lookup"><span data-stu-id="3057f-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="3057f-118">Sobrescribir el método [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) para admitir la eliminación de unidades existentes.</span><span class="sxs-lookup"><span data-stu-id="3057f-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="3057f-119">Sobrescribir el método [System. Management. Automation. Provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) para cambiar el comportamiento del cmdlet `Get-Item`, lo que permite al usuario recuperar elementos del almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="3057f-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="3057f-120">(En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Get-Item`).</span><span class="sxs-lookup"><span data-stu-id="3057f-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="3057f-121">Sobrescribir el método [System. Management. Automation. Provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) para cambiar el comportamiento del cmdlet `Set-Item`, lo que permite al usuario actualizar los elementos del almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="3057f-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="3057f-122">(En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Get-Item`).</span><span class="sxs-lookup"><span data-stu-id="3057f-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="3057f-123">Sobrescribir el método [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) para cambiar el comportamiento del cmdlet `Test-Path`.</span><span class="sxs-lookup"><span data-stu-id="3057f-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="3057f-124">(En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Test-Path`).</span><span class="sxs-lookup"><span data-stu-id="3057f-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="3057f-125">Sobrescribir el método [System. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) para determinar si la ruta de acceso proporcionada es válida.</span><span class="sxs-lookup"><span data-stu-id="3057f-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="3057f-126">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3057f-126">Example</span></span>

<span data-ttu-id="3057f-127">En este ejemplo se muestra cómo sobrescribir los métodos necesarios para obtener y establecer elementos en una base de datos de Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="3057f-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="3057f-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="3057f-128">See Also</span></span>

[<span data-ttu-id="3057f-129">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="3057f-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="3057f-130">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="3057f-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="3057f-131">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="3057f-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="3057f-132">Diseño del proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3057f-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
