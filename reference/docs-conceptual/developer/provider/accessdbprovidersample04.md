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
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

En este ejemplo se muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a los cmdlets `Copy-Item`, `Get-ChildItem`, `New-Item` y `Remove-Item`. Estos métodos deberían implementarse cuando el almacén de datos contengan elementos que son contenedores. Un contenedor es un grupo de elementos secundarios con un elemento primario común. La clase de proveedor de este ejemplo se deriva de la clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

## <a name="demonstrates"></a>Demuestra

> [!IMPORTANT]
> Lo más probable es que la clase de proveedor derive de [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Este ejemplo muestra lo siguiente:

- Declarar el atributo `CmdletProvider`.

- Definir una clase de proveedor que se deriva de la clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

- Sobrescribir el método [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) para cambiar el comportamiento del cmdlet `Copy-Item` que permite al usuario copiar elementos de una ubicación a otra. (En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Copy-Item`).

- Sobrescribir el método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) para cambiar el comportamiento del cmdlet Get-ChildItems, que permite al usuario recuperar los elementos secundarios del elemento primario. (En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet Get-ChildItems).

- Sobrescribir el método [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) para cambiar el comportamiento del cmdlet Get-ChildItems cuando se especifica el parámetro `Name` del cmdlet.

- Sobrescribir el método [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) para cambiar el comportamiento del cmdlet `New-Item`, que permite al usuario agregar elementos al almacén de datos. (En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `New-Item`).

- Sobrescribir el método [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) para cambiar el comportamiento del cmdlet `Remove-Item`. (En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Remove-Item`).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo sobrescribir los métodos necesarios para copiar, crear y quitar elementos, así como métodos para obtener los elementos secundarios de un elemento primario.

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Véase también

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Diseño del proveedor de Windows PowerShell](./provider-types.md)
