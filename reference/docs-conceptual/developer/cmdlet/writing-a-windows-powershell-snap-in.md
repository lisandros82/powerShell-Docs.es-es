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
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="95c28-102">Escritura de un complemento de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95c28-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="95c28-103">En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que se puede usar para registrar todos los cmdlets y proveedores de Windows PowerShell en un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="95c28-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="95c28-104">Con este tipo de complemento, no se seleccionan los cmdlets y proveedores que se van a registrar.</span><span class="sxs-lookup"><span data-stu-id="95c28-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="95c28-105">Para escribir un complemento que le permita seleccionar lo que se registra, consulte [escribir un complemento personalizado de Windows PowerShell](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="95c28-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="95c28-106">Escritura de un complemento de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95c28-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="95c28-107">Agregue el atributo RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="95c28-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="95c28-108">Cree una clase pública que se derive de la clase [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="95c28-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="95c28-109">En este ejemplo, el nombre de la clase es "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="95c28-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="95c28-110">Agregue una propiedad pública para el nombre del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="95c28-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="95c28-111">Al asignar nombres a los complementos, no use ninguno de los siguientes caracteres: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@``` ` \`\`\`\*\`,</span><span class="sxs-lookup"><span data-stu-id="95c28-111">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

    <span data-ttu-id="95c28-112">En este ejemplo, el nombre del complemento es "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="95c28-112">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="95c28-113">Agregue una propiedad pública para el proveedor del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="95c28-113">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="95c28-114">En este ejemplo, el proveedor es "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="95c28-114">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="95c28-115">Agregue una propiedad pública para el recurso de proveedor del complemento (opcional).</span><span class="sxs-lookup"><span data-stu-id="95c28-115">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="95c28-116">En este ejemplo, el recurso Vendor es "GetProcPSSnapIn01, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="95c28-116">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="95c28-117">Agregue una propiedad pública para la descripción del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="95c28-117">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="95c28-118">En este ejemplo, la descripción es "este es un complemento de Windows PowerShell que registra el cmdlet Get-proc".</span><span class="sxs-lookup"><span data-stu-id="95c28-118">In this example, the description is "This is a Windows PowerShell snap-in that registers the  get-proc cmdlet".</span></span>

7. <span data-ttu-id="95c28-119">Agregue una propiedad pública para el recurso de Descripción del complemento (opcional).</span><span class="sxs-lookup"><span data-stu-id="95c28-119">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="95c28-120">En este ejemplo, el recurso Vendor es "GetProcPSSnapIn01, es un complemento de Windows PowerShell que registra el cmdlet Get-proc".</span><span class="sxs-lookup"><span data-stu-id="95c28-120">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in  that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="95c28-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="95c28-121">Example</span></span>

<span data-ttu-id="95c28-122">En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que se puede usar para registrar el cmdlet Get-proc en el shell de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95c28-122">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="95c28-123">Tenga en cuenta que en este ejemplo, el ensamblado completo solo contendría la clase de complemento GetProcPSSnapIn01 y la clase de cmdlet `Get-Proc`.</span><span class="sxs-lookup"><span data-stu-id="95c28-123">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the `Get-Proc` cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="95c28-124">Vea también</span><span class="sxs-lookup"><span data-stu-id="95c28-124">See Also</span></span>

<span data-ttu-id="95c28-125">[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="95c28-125">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="95c28-126">SDK de Windows PowerShell Shell</span><span class="sxs-lookup"><span data-stu-id="95c28-126">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
