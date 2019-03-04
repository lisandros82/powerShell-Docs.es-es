---
title: Muestras de proveedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853131"
---
# <a name="provider-samples"></a>Ejemplos de proveedor

Esta sección incluyen ejemplos de proveedores que tienen acceso a una base de datos de Microsoft Access. Estos ejemplos incluyen las clases de proveedor que se derivan todas las clases de proveedor base.

## <a name="in-this-section"></a>En esta sección

Esta sección incluye los temas siguientes:

[Ejemplo de AccessDBProviderSample01](./accessdbprovidersample01.md) en este ejemplo se muestra cómo declarar la clase de proveedor que derive directamente de la [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) clase. Se incluye aquí solo por cuestiones de integridad.

[AccessDBProviderSample02](./accessdbprovidersample02.md) este ejemplo muestra cómo sobrescribir los [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) y [ System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) métodos para admitir llamadas a la `New-PSDrive` y `Remove-PSDrive` cmdlets. La clase de proveedor en este ejemplo se deriva de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase.

[AccessDBProviderSample03](./accessdbprovidersample03.md) este ejemplo muestra cómo sobrescribir los [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) y [ System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) métodos para admitir llamadas a la `Get-Item` y `Set-Item` cmdlets. La clase de proveedor en este ejemplo se deriva de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase.

[AccessDBProviderSample04](./accessdbprovidersample04.md) este ejemplo muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a la `Copy-Item`, `Get-ChildItem`, `New-Item`, y `Remove-Item` cmdlets. Estos métodos deberían implementarse cuando el almacén de datos contengan elementos que son contenedores. Un contenedor es un grupo de elementos secundarios con un elemento primario común. La clase de proveedor en este ejemplo se deriva de la [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase.

[AccessDBProviderSample05](./accessdbprovidersample05.md) este ejemplo muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a la `Move-Item` y `Join-Path` cmdlets. Estos métodos deberían implementarse cuando el usuario necesite mover elementos dentro de un contenedor y si el almacén de datos tiene contenedores anidados. La clase de proveedor en este ejemplo se deriva de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase.

[AccessDBProviderSample06](./accessdbprovidersample06.md) en este ejemplo se muestra cómo sobrescribir métodos de contenido para admitir llamadas a la `Clear-Content`, `Get-Content`, y `Set-Content` cmdlets. Estos métodos deberían implementarse cuando el usuario necesite administrar el contenido de los elementos en el almacén de datos. La clase de proveedor en este ejemplo se deriva de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase e implementa el [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaz.

## <a name="see-also"></a>Véase también

[Escribir un proveedor de Windows PowerShell](./writing-a-windows-powershell-provider.md)