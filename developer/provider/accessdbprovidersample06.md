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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055553"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

En este ejemplo se muestra cómo sobrescribir métodos de contenido para admitir llamadas a la `Clear-Content`, `Get-Content`, y `Set-Content` cmdlets. Estos métodos deberían implementarse cuando el usuario necesite administrar el contenido de los elementos en el almacén de datos. La clase de proveedor en este ejemplo se deriva de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase e implementa el [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaz.

## <a name="demonstrates"></a>Demostraciones

> [!IMPORTANT]
> La clase de proveedor se más probable es que se derive de una de las siguientes clases y posiblemente implementar otras interfaces de proveedor:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase. Consulte [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase. Consulte [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase.
>
> Para obtener más información acerca de cómo elegir qué clase de proveedor para derivar según las características del proveedor, consulte [diseñar su proveedor de Windows PowerShell](./provider-types.md).

Este ejemplo muestra lo siguiente:

- Declarar el `CmdletProvider` atributo.

- Definir una clase de proveedor que se deriva el [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase y que declara el [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaz.

- Sobrescribiendo el [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método para cambiar el comportamiento de la `Clear-Content` cmdlet, que permite al usuario quitar el contenido de un elemento. (Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Clear-Content` cmdlet.)

- Sobrescribiendo el [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método para cambiar el comportamiento de la `Get-Content` cmdlet, que permite al usuario recuperar el contenido de un elemento. (Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Get-Content` cmdlet.).

- Sobrescribiendo el [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) método para cambiar el comportamiento de la `Set-Content` cmdlet, que permite al usuario actualizar el contenido de un elemento. (Este ejemplo no muestra cómo agregar parámetros dinámicos a la `Set-Content` cmdlet.)

## <a name="example"></a>Ejemplo

Este ejemplo muestra cómo sobrescribir los métodos necesarios para borrar, obtener y establecer el contenido de elementos de datos Microsoft Access base.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Véase también

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Diseñar el proveedor de Windows PowerShell](./provider-types.md)