---
title: Ejemplos de proveedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366304"
---
# <a name="provider-samples"></a>Ejemplos de proveedor

En esta sección se incluyen ejemplos de proveedores que tienen acceso a una base de datos de Microsoft Access. En estos ejemplos se incluyen las clases de proveedor que derivan de todas las clases base del proveedor.

## <a name="in-this-section"></a>En esta sección

Esta sección incluye los temas siguientes:

[Ejemplo de AccessDBProviderSample01](./accessdbprovidersample01.md) En este ejemplo se muestra cómo declarar la clase de proveedor que se deriva directamente de la clase [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . Se incluye aquí solo por cuestiones de integridad.

[AccessDBProviderSample02](./accessdbprovidersample02.md) En este ejemplo se muestra cómo sobrescribir los métodos [System. Management. Automation. Provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) y [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) para admitir llamadas al `New-PSDrive` y @no__t 4 cmdlets. La clase de proveedor de este ejemplo se deriva de la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .

[AccessDBProviderSample03](./accessdbprovidersample03.md) En este ejemplo se muestra cómo sobrescribir los métodos [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) y [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) para admitir llamadas a los `Get-Item` y @no__ cmdlets t-4. La clase de proveedor de este ejemplo se deriva de la clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

[AccessDBProviderSample04](./accessdbprovidersample04.md) En este ejemplo se muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a los cmdlets `Copy-Item`, `Get-ChildItem`, `New-Item` y `Remove-Item`. Estos métodos deberían implementarse cuando el almacén de datos contengan elementos que son contenedores. Un contenedor es un grupo de elementos secundarios con un elemento primario común. La clase de proveedor de este ejemplo se deriva de la clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

[AccessDBProviderSample05](./accessdbprovidersample05.md) En este ejemplo se muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a los cmdlets `Move-Item` y `Join-Path`. Estos métodos deberían implementarse cuando el usuario necesite mover elementos dentro de un contenedor y si el almacén de datos tiene contenedores anidados. La clase de proveedor de este ejemplo se deriva de la clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

[AccessDBProviderSample06](./accessdbprovidersample06.md) En este ejemplo se muestra cómo sobrescribir métodos de contenido para admitir llamadas a los cmdlets `Clear-Content`, `Get-Content` y `Set-Content`. Estos métodos deberían implementarse cuando el usuario necesite administrar el contenido de los elementos en el almacén de datos. La clase de proveedor de este ejemplo se deriva de la clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) e implementa la interfaz [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

## <a name="see-also"></a>Véase también

[Escribir un proveedor de Windows PowerShell](./writing-a-windows-powershell-provider.md)