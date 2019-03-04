---
title: Escribir un complemento personalizado de Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: 20b7fdce1d31e3dee4598a7595962fca1c99d80a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863351"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Escritura de un complemento de Windows PowerShell personalizado

En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que registra los cmdlets específicos.

Con este tipo de complemento, especifique qué cmdlets, proveedores, los tipos o formatos para registrar. Para obtener más información sobre cómo escribir un complemento que se registra todos los cmdlets y proveedores en un ensamblado, vea [escribiendo un Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Para escribir un Windows PowerShell Snap-in que registra los cmdlets específicos.

1. Agregue el atributo RunInstallerAttribute.

2. Cree una clase pública que se deriva el [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) clase.

   En este ejemplo, el nombre de clase es "CustomPSSnapinTest".

3. Agregue una propiedad pública para el nombre del complemento (obligatorio). Al asignar nombres a complementos, no utilice ninguno de los siguientes caracteres: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ? @ ` *

   En este ejemplo, el nombre del complemento de es "CustomPSSnapInTest".

4. Agregue una propiedad pública para el proveedor del complemento (obligatorio).

   En este ejemplo, el proveedor es "Microsoft".

5. Agregue una propiedad pública para el recurso del proveedor del complemento de (opcional).

   En este ejemplo, el recurso del proveedor es "CustomPSSnapInTest, Microsoft".

6. Agregue una propiedad pública de la descripción del complemento (obligatorio).

   En este ejemplo, la descripción es: "Esto es un complemento personalizado de Windows PowerShell que incluye los cmdlets de prueba CustomSnapinTest y Test-HelloWorld".

7. Agregue una propiedad pública para el recurso de descripción del complemento de (opcional).

   En este ejemplo, el recurso del proveedor es "CustomPSSnapInTest, esto es un complemento personalizado de Windows PowerShell que incluye los cmdlets de prueba-HelloWorld y CustomSnapinTest de prueba".

8. Especifique los cmdlets que pertenecen a la personalizada complemento (opcional) con el [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) clase. La información agregada aquí incluye el nombre del cmdlet, su tipo de .NET y el nombre de archivo de Ayuda de cmdlet (el formato del nombre de archivo de Ayuda del cmdlet debe ser name.dll help.xml).

   Este ejemplo agrega los cmdlets Test-HelloWorld y TestCustomSnapinTest.

9. Especifique los proveedores que pertenecen al complemento personalizado (opcional).

   En este ejemplo no especifica todos los proveedores.

10. Especificar los tipos que pertenecen al complemento personalizado (opcional).

    En este ejemplo no especifica ningún tipo.

11. Especificar los formatos que pertenecen al complemento personalizado (opcional).

    En este ejemplo no especifica ningún formato.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo escribir un complemento personalizado Windows PowerShell que puede usarse para registrar los cmdlets de prueba CustomSnapinTest y Test-HelloWorld. Tenga en cuenta que en este ejemplo, el ensamblado completando podría contener otros cmdlets y proveedores que no se registrarían mediante este complemento.

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

Para obtener más información sobre el registro de complementos, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) en el [Guía del programador de Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Véase también

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Shell de SDK de Windows PowerShell](../windows-powershell-reference.md)
