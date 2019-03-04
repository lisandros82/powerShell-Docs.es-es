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
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Este ejemplo muestra cómo sobrescribir los [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) y [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) métodos para admitir llamadas a la `Get-Item` y `Set-Item` cmdlets. La clase de proveedor en este ejemplo se deriva de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase.

## <a name="demonstrates"></a>Demostraciones

> [!IMPORTANT]
> La clase de proveedor se más probable es que se derive de una de las siguientes clases y posiblemente implementar otras interfaces de proveedor:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase. Consulte [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase. Consulte [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Para obtener más información acerca de cómo elegir qué clase de proveedor para derivar según las características del proveedor, consulte [diseñar su proveedor de Windows PowerShell](./provider-types.md).

Este ejemplo muestra lo siguiente:

- Declarar el `CmdletProvider` atributo.

- Definir una clase de proveedor que se deriva el [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase.

- Sobrescribiendo el [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método para cambiar el comportamiento de la `New-PSDrive` cmdlet, lo que permite al usuario crear nuevas unidades de disco. (Este ejemplo no muestra cómo agregar parámetros dinámicos a la `New-PSDrive` cmdlet.)

- Sobrescribiendo el [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método para admitir la eliminación de unidades de disco existentes.

- Sobrescribiendo el [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para cambiar el comportamiento de la `Get-Item` cmdlet, que permite al usuario recuperar los elementos del almacén de datos. (Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Get-Item` cmdlet.)

- Sobrescribiendo el [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método para cambiar el comportamiento de la `Set-Item` cmdlet, que permite al usuario actualizar los elementos en el almacén de datos. (Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Get-Item` cmdlet.)

- Sobrescribiendo el [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método para cambiar el comportamiento de la `Test-Path` cmdlet. (Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Test-Path` cmdlet.)

- Sobrescribiendo el [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método para determinar si la ruta de acceso proporcionada es válida.

## <a name="example"></a>Ejemplo

Este ejemplo muestra cómo sobrescribir los métodos necesarios para obtener y establecer los elementos de datos Microsoft Access base.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>Véase también

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Diseñar el proveedor de Windows PowerShell](./provider-types.md)