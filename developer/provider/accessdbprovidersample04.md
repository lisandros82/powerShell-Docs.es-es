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
ms.openlocfilehash: fd013384a4b588bcdb397d7771425fe5c031c48f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856701"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Este ejemplo muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a la `Copy-Item`, `Get-ChildItem`, `New-Item`, y `Remove-Item` cmdlets. Estos métodos deberían implementarse cuando el almacén de datos contengan elementos que son contenedores. Un contenedor es un grupo de elementos secundarios con un elemento primario común. La clase de proveedor en este ejemplo se deriva de la [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase.

## <a name="demonstrates"></a>Demostraciones

> [!IMPORTANT]
> Probablemente se derivará la clase de proveedor de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Este ejemplo muestra lo siguiente:

- Declarar el `CmdletProvider` atributo.

- Definir una clase de proveedor que se deriva el [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase.

- Sobrescribiendo el [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método para cambiar el comportamiento de la `Copy-Item` cmdlet que permite al usuario copiar los elementos de una ubicación a otra. (Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Copy-Item` cmdlet.)

- Sobrescribiendo el [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método para cambiar el comportamiento del cmdlet Get-ChildItems, lo que permite al usuario recuperar los elementos secundarios del elemento primario . (Este ejemplo no muestra cómo agregar parámetros dinámicos al cmdlet Get-ChildItems).

- Sobrescribiendo el [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método para cambiar el comportamiento del cmdlet Get-ChildItems cuando el `Name` se especifica el parámetro del cmdlet.

- Sobrescribiendo el [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método para cambiar el comportamiento de la `New-Item` cmdlet, que permite al usuario agregar elementos al almacén de datos. (Este ejemplo no muestra cómo agregar parámetros dinámicos a la `New-Item` cmdlet.)

- Sobrescribiendo el [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método para cambiar el comportamiento de la `Remove-Item` cmdlet. (Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Remove-Item` cmdlet.)

## <a name="example"></a>Ejemplo

Este ejemplo muestra cómo sobrescribir los métodos necesarios para copiar, crear y quitar elementos, así como métodos para obtener al elemento secundario de los elementos de un elemento primario.

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Véase también

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Diseñar el proveedor de Windows PowerShell](./provider-types.md)