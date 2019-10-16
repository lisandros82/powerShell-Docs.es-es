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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359994"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

En este ejemplo se muestra cómo sobrescribir los métodos [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) y [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) para admitir llamadas a `Get-Item` y @no__ cmdlets t-3. La clase de proveedor de este ejemplo se deriva de la clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

## <a name="demonstrates"></a>Demuestra

> [!IMPORTANT]
> Lo más probable es que la clase de proveedor derive de una de las siguientes clases y, posiblemente, implemente otras interfaces de proveedor:
>
> -   Clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .
> -   Clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Vea [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   Clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Vea [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Para obtener más información sobre cómo elegir la clase de proveedor que se va a derivar en función de las características del proveedor, vea [diseñar un proveedor de Windows PowerShell](./provider-types.md).

Este ejemplo muestra lo siguiente:

- Declarar el atributo `CmdletProvider`.

- Definir una clase de proveedor que se deriva de la clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

- Sobrescribir el método [System. Management. Automation. Provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) para cambiar el comportamiento del cmdlet `New-PSDrive`, lo que permite al usuario crear nuevas unidades. (En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `New-PSDrive`).

- Sobrescribir el método [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) para admitir la eliminación de unidades existentes.

- Sobrescribir el método [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) para cambiar el comportamiento del cmdlet `Get-Item`, lo que permite al usuario recuperar elementos del almacén de datos. (En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Get-Item`).

- Sobrescribir el método [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) para cambiar el comportamiento del cmdlet `Set-Item`, lo que permite al usuario actualizar los elementos del almacén de datos. (En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Get-Item`).

- Sobrescribir el método [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) para cambiar el comportamiento del cmdlet `Test-Path`. (En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Test-Path`).

- Sobrescribir el método [System. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) para determinar si la ruta de acceso proporcionada es válida.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo sobrescribir los métodos necesarios para obtener y establecer elementos en una base de datos de Microsoft Access.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>Véase también

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Diseño del proveedor de Windows PowerShell](./provider-types.md)
