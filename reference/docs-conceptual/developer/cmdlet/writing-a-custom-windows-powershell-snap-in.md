---
title: Escribir un complemento de Windows PowerShell personalizado | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364254"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Escritura de un complemento de Windows PowerShell personalizado

En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que registra cmdlets específicos.

Con este tipo de complemento, se especifica qué cmdlets, proveedores, tipos o formatos se van a registrar. Para obtener más información sobre cómo escribir un complemento que registre todos los cmdlets y proveedores de un ensamblado, consulte [escribir un complemento de Windows PowerShell](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Para escribir un complemento de Windows PowerShell que registre cmdlets específicos.

1. Agregue el atributo RunInstallerAttribute.

2. Cree una clase pública que se derive de la clase [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .

   En este ejemplo, el nombre de la clase es "CustomPSSnapinTest".

3. Agregue una propiedad pública para el nombre del complemento (obligatorio). Al asignar nombres a los complementos, no use ninguno de los siguientes caracteres: #. , () {} [] &-/\ $; : "' \< > &#124; ? @ ` *

   En este ejemplo, el nombre del complemento es "CustomPSSnapInTest".

4. Agregue una propiedad pública para el proveedor del complemento (obligatorio).

   En este ejemplo, el proveedor es "Microsoft".

5. Agregue una propiedad pública para el recurso de proveedor del complemento (opcional).

   En este ejemplo, el recurso Vendor es "CustomPSSnapInTest, Microsoft".

6. Agregue una propiedad pública para la descripción del complemento (obligatorio).

   En este ejemplo, la descripción es: "se trata de un complemento personalizado de Windows PowerShell que incluye los cmdlets test-HelloWorld y test-CustomSnapinTest".

7. Agregue una propiedad pública para el recurso de Descripción del complemento (opcional).

   En este ejemplo, el recurso Vendor es "CustomPSSnapInTest, es un complemento personalizado de Windows PowerShell que incluye los cmdlets test-HelloWorld y test-CustomSnapinTest".

8. Especifique los cmdlets que pertenecen al complemento personalizado (opcional) mediante la clase [System. Management. Automation. espacios de Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) . La información que se agrega aquí incluye el nombre del cmdlet, su tipo de .NET y el nombre del archivo de ayuda del cmdlet (el formato del nombre del archivo de ayuda del cmdlet debe ser Name. dll-help. xml).

   En este ejemplo se agregan los cmdlets test-HelloWorld y TestCustomSnapinTest.

9. Especifique los proveedores que pertenecen al complemento personalizado (opcional).

   En este ejemplo no se especifica ningún proveedor.

10. Especifique los tipos que pertenecen al complemento personalizado (opcional).

    En este ejemplo no se especifica ningún tipo.

11. Especifique los formatos que pertenecen al complemento personalizado (opcional).

    En este ejemplo no se especifica ningún formato.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo escribir un complemento personalizado de Windows PowerShell que se puede usar para registrar los cmdlets test-HelloWorld y test-CustomSnapinTest. Tenga en cuenta que en este ejemplo, el ensamblado completo podría contener otros cmdlets y proveedores que este complemento no registraría.

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

Para obtener más información sobre el registro de complementos, vea [Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) en la [Guía del programador de Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Véase también

[Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK de Windows PowerShell Shell](../windows-powershell-reference.md)
