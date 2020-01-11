---
title: Escribir un complemento de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: d12a66e354a23041fffb0f8fa286c849849ec2b0
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870479"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Escritura de un complemento de Windows PowerShell

En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que se puede usar para registrar todos los cmdlets y proveedores de Windows PowerShell en un ensamblado.

Con este tipo de complemento, no se seleccionan los cmdlets y proveedores que se van a registrar. Para escribir un complemento que le permita seleccionar lo que se registra, consulte [escribir un complemento personalizado de Windows PowerShell](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Escritura de un complemento de Windows PowerShell

1. Agregue el atributo RunInstallerAttribute.

2. Cree una clase pública que se derive de la clase [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) .

    En este ejemplo, el nombre de la clase es "GetProcPSSnapIn01".

3. Agregue una propiedad pública para el nombre del complemento (obligatorio). Al asignar nombres a los complementos, no use ninguno de los siguientes caracteres: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@``` ` ```*`,

    En este ejemplo, el nombre del complemento es "GetProcPSSnapIn01".

4. Agregue una propiedad pública para el proveedor del complemento (obligatorio).

    En este ejemplo, el proveedor es "Microsoft".

5. Agregue una propiedad pública para el recurso de proveedor del complemento (opcional).

    En este ejemplo, el recurso Vendor es "GetProcPSSnapIn01, Microsoft".

6. Agregue una propiedad pública para la descripción del complemento (obligatorio).

    En este ejemplo, la descripción es "este es un complemento de Windows PowerShell que registra el cmdlet Get-proc".

7. Agregue una propiedad pública para el recurso de Descripción del complemento (opcional).

    En este ejemplo, el recurso Vendor es "GetProcPSSnapIn01, es un complemento de Windows PowerShell que registra el cmdlet Get-proc".

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que se puede usar para registrar el cmdlet Get-proc en el shell de Windows PowerShell. Tenga en cuenta que en este ejemplo, el ensamblado completo solo contendría la clase de complemento GetProcPSSnapIn01 y la clase de cmdlet `Get-Proc`.

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a>Vea también

[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions/ms714644(v=vs.85))

[SDK de Windows PowerShell Shell](../windows-powershell-reference.md)
