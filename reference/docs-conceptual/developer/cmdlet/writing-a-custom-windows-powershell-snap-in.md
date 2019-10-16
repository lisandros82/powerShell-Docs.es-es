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
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="5e528-102">Escritura de un complemento de Windows PowerShell personalizado</span><span class="sxs-lookup"><span data-stu-id="5e528-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="5e528-103">En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que registra cmdlets específicos.</span><span class="sxs-lookup"><span data-stu-id="5e528-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="5e528-104">Con este tipo de complemento, se especifica qué cmdlets, proveedores, tipos o formatos se van a registrar.</span><span class="sxs-lookup"><span data-stu-id="5e528-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="5e528-105">Para obtener más información sobre cómo escribir un complemento que registre todos los cmdlets y proveedores de un ensamblado, consulte [escribir un complemento de Windows PowerShell](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="5e528-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="5e528-106">Para escribir un complemento de Windows PowerShell que registre cmdlets específicos.</span><span class="sxs-lookup"><span data-stu-id="5e528-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="5e528-107">Agregue el atributo RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="5e528-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="5e528-108">Cree una clase pública que se derive de la clase [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="5e528-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="5e528-109">En este ejemplo, el nombre de la clase es "CustomPSSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="5e528-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="5e528-110">Agregue una propiedad pública para el nombre del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="5e528-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="5e528-111">Al asignar nombres a los complementos, no use ninguno de los siguientes caracteres: #.</span><span class="sxs-lookup"><span data-stu-id="5e528-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="5e528-112">, () {} [] &-/\ $; : "' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="5e528-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="5e528-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="5e528-113">@ \` \*</span></span>

   <span data-ttu-id="5e528-114">En este ejemplo, el nombre del complemento es "CustomPSSnapInTest".</span><span class="sxs-lookup"><span data-stu-id="5e528-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="5e528-115">Agregue una propiedad pública para el proveedor del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="5e528-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="5e528-116">En este ejemplo, el proveedor es "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="5e528-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="5e528-117">Agregue una propiedad pública para el recurso de proveedor del complemento (opcional).</span><span class="sxs-lookup"><span data-stu-id="5e528-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="5e528-118">En este ejemplo, el recurso Vendor es "CustomPSSnapInTest, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="5e528-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="5e528-119">Agregue una propiedad pública para la descripción del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="5e528-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="5e528-120">En este ejemplo, la descripción es: "se trata de un complemento personalizado de Windows PowerShell que incluye los cmdlets test-HelloWorld y test-CustomSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="5e528-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="5e528-121">Agregue una propiedad pública para el recurso de Descripción del complemento (opcional).</span><span class="sxs-lookup"><span data-stu-id="5e528-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="5e528-122">En este ejemplo, el recurso Vendor es "CustomPSSnapInTest, es un complemento personalizado de Windows PowerShell que incluye los cmdlets test-HelloWorld y test-CustomSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="5e528-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="5e528-123">Especifique los cmdlets que pertenecen al complemento personalizado (opcional) mediante la clase [System. Management. Automation. espacios de Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) .</span><span class="sxs-lookup"><span data-stu-id="5e528-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="5e528-124">La información que se agrega aquí incluye el nombre del cmdlet, su tipo de .NET y el nombre del archivo de ayuda del cmdlet (el formato del nombre del archivo de ayuda del cmdlet debe ser Name. dll-help. xml).</span><span class="sxs-lookup"><span data-stu-id="5e528-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="5e528-125">En este ejemplo se agregan los cmdlets test-HelloWorld y TestCustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="5e528-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="5e528-126">Especifique los proveedores que pertenecen al complemento personalizado (opcional).</span><span class="sxs-lookup"><span data-stu-id="5e528-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="5e528-127">En este ejemplo no se especifica ningún proveedor.</span><span class="sxs-lookup"><span data-stu-id="5e528-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="5e528-128">Especifique los tipos que pertenecen al complemento personalizado (opcional).</span><span class="sxs-lookup"><span data-stu-id="5e528-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="5e528-129">En este ejemplo no se especifica ningún tipo.</span><span class="sxs-lookup"><span data-stu-id="5e528-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="5e528-130">Especifique los formatos que pertenecen al complemento personalizado (opcional).</span><span class="sxs-lookup"><span data-stu-id="5e528-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="5e528-131">En este ejemplo no se especifica ningún formato.</span><span class="sxs-lookup"><span data-stu-id="5e528-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="5e528-132">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5e528-132">Example</span></span>

<span data-ttu-id="5e528-133">En este ejemplo se muestra cómo escribir un complemento personalizado de Windows PowerShell que se puede usar para registrar los cmdlets test-HelloWorld y test-CustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="5e528-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="5e528-134">Tenga en cuenta que en este ejemplo, el ensamblado completo podría contener otros cmdlets y proveedores que este complemento no registraría.</span><span class="sxs-lookup"><span data-stu-id="5e528-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

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

<span data-ttu-id="5e528-135">Para obtener más información sobre el registro de complementos, vea [Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) en la [Guía del programador de Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="5e528-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5e528-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="5e528-136">See Also</span></span>

[<span data-ttu-id="5e528-137">Cómo registrar cmdlets, proveedores y aplicaciones host</span><span class="sxs-lookup"><span data-stu-id="5e528-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="5e528-138">SDK de Windows PowerShell Shell</span><span class="sxs-lookup"><span data-stu-id="5e528-138">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
