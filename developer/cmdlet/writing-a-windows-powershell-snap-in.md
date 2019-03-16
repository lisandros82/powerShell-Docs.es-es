---
title: Escribir un complemento de PowerShell de Windows | Microsoft Docs
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
ms.openlocfilehash: 0c99f4bcfe5e2d34d31714dc85a53b5e8abe0925
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057797"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Escritura de un complemento de Windows PowerShell

En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que puede usarse para registrar todos los cmdlets y proveedores de Windows PowerShell en un ensamblado.

Con este tipo de complemento, no seleccione qué cmdlets y proveedores que desea registrar. Para escribir un complemento que le permite seleccionar lo que está registrado, consulte [escribir un Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Escritura de un complemento de Windows PowerShell

1. Agregue el atributo RunInstallerAttribute.

2. Cree una clase pública que se deriva el [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) clase.

    En este ejemplo, el nombre de clase es "GetProcPSSnapIn01".

3. Agregue una propiedad pública para el nombre del complemento (obligatorio). Al asignar nombres a complementos, no utilice ninguno de los siguientes caracteres: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    En este ejemplo, el nombre del complemento de es "GetProcPSSnapIn01".

4. Agregue una propiedad pública para el proveedor del complemento (obligatorio).

    En este ejemplo, el proveedor es "Microsoft".

5. Agregue una propiedad pública para el recurso del proveedor del complemento de (opcional).

    En este ejemplo, el recurso del proveedor es "GetProcPSSnapIn01, Microsoft".

6. Agregue una propiedad pública de la descripción del complemento (obligatorio).

    En este ejemplo, la descripción es "Esto es un complemento de Windows PowerShell que se registra el cmdlet get-proc".

7. Agregue una propiedad pública para el recurso de descripción del complemento de (opcional).

    En este ejemplo, el recurso del proveedor es "GetProcPSSnapIn01, esto es un complemento de Windows PowerShell que se registra el cmdlet get-proc".

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que puede usarse para registrar el cmdlet Get-Proc en el shell de Windows PowerShell. Tenga en cuenta que en este ejemplo, el ensamblado completo contendría únicamente la GetProcPSSnapIn01 complemento de clase y la clase del cmdlet Get-Proc.

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

## <a name="see-also"></a>Véase también

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Shell de SDK de Windows PowerShell](../windows-powershell-reference.md)
