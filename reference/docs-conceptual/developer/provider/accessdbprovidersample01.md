---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360004"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

En este ejemplo se muestra cómo declarar una clase de proveedor que se deriva directamente de la clase [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . Se incluye aquí solo por cuestiones de integridad.

## <a name="demonstrates"></a>Demuestra

> [!IMPORTANT]
> Lo más probable es que la clase de proveedor derive de una de las siguientes clases y, posiblemente, implemente otras interfaces de proveedor:
>
> -   Clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Vea [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   Clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Vea [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   Clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Vea [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Para obtener más información sobre cómo elegir la clase de proveedor que se va a derivar en función de las características del proveedor, vea [diseñar un proveedor de Windows PowerShell](./provider-types.md).

Este ejemplo muestra lo siguiente:

- Declarar el atributo `CmdletProvider`.

- Definir una clase de proveedor que se deriva directamente de la clase [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo definir una clase de proveedor y cómo declarar el atributo `CmdletProvider`.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a>Véase también

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Diseño del proveedor de Windows PowerShell](./provider-types.md)