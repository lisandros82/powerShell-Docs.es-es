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
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

En este ejemplo se muestra cómo sobrescribir métodos de contenido para admitir llamadas a los cmdlets `Clear-Content`, `Get-Content` y `Set-Content`. Estos métodos deberían implementarse cuando el usuario necesite administrar el contenido de los elementos en el almacén de datos. La clase de proveedor de este ejemplo se deriva de la clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) e implementa la interfaz [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

## <a name="demonstrates"></a>Demuestra

> [!IMPORTANT]
> Lo más probable es que la clase de proveedor derive de una de las siguientes clases y, posiblemente, implemente otras interfaces de proveedor:
>
> -   Clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Vea [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   Clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Vea [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   Clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .
>
> Para obtener más información sobre cómo elegir la clase de proveedor que se va a derivar en función de las características del proveedor, vea [diseñar un proveedor de Windows PowerShell](./provider-types.md).

Este ejemplo muestra lo siguiente:

- Declarar el atributo `CmdletProvider`.

- Definir una clase de proveedor que se deriva de la clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) y que declara la interfaz [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

- Sobrescribir el método [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) para cambiar el comportamiento del cmdlet `Clear-Content`, lo que permite al usuario quitar el contenido de un elemento. (En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Clear-Content`).

- Sobrescribir el método [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) para cambiar el comportamiento del cmdlet `Get-Content`, lo que permite al usuario recuperar el contenido de un elemento. (En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Get-Content`).

- Sobrescribir el método [Microsoft. PowerShell. Commands. Filesystemprovider. Getcontentwriter *](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) para cambiar el comportamiento del cmdlet `Set-Content`, lo que permite al usuario actualizar el contenido de un elemento. (En este ejemplo no se muestra cómo agregar parámetros dinámicos al cmdlet `Set-Content`).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo sobrescribir los métodos necesarios para borrar, obtener y establecer el contenido de los elementos en una base de datos de Microsoft Access.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Véase también

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Diseño del proveedor de Windows PowerShell](./provider-types.md)
