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
ms.openlocfilehash: 465ab9e8fa29716ce0f46ad0dcf01d0ddd615bcd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364234"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="34cf3-102">Escritura de un complemento de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="34cf3-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="34cf3-103">En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que se puede usar para registrar todos los cmdlets y proveedores de Windows PowerShell en un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="34cf3-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="34cf3-104">Con este tipo de complemento, no se seleccionan los cmdlets y proveedores que se van a registrar.</span><span class="sxs-lookup"><span data-stu-id="34cf3-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="34cf3-105">Para escribir un complemento que le permita seleccionar lo que se registra, consulte [escribir un complemento personalizado de Windows PowerShell](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="34cf3-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="34cf3-106">Escritura de un complemento de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="34cf3-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="34cf3-107">Agregue el atributo RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="34cf3-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="34cf3-108">Cree una clase pública que se derive de la clase [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="34cf3-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="34cf3-109">En este ejemplo, el nombre de la clase es "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="34cf3-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="34cf3-110">Agregue una propiedad pública para el nombre del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="34cf3-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="34cf3-111">Al asignar nombres a los complementos, no use ninguno de los siguientes caracteres: #.</span><span class="sxs-lookup"><span data-stu-id="34cf3-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="34cf3-112">, () {} [] &-/\ $; : "' \< >;?</span><span class="sxs-lookup"><span data-stu-id="34cf3-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="34cf3-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="34cf3-113">@ \` \*</span></span>

    <span data-ttu-id="34cf3-114">En este ejemplo, el nombre del complemento es "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="34cf3-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="34cf3-115">Agregue una propiedad pública para el proveedor del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="34cf3-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="34cf3-116">En este ejemplo, el proveedor es "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="34cf3-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="34cf3-117">Agregue una propiedad pública para el recurso de proveedor del complemento (opcional).</span><span class="sxs-lookup"><span data-stu-id="34cf3-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="34cf3-118">En este ejemplo, el recurso Vendor es "GetProcPSSnapIn01, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="34cf3-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="34cf3-119">Agregue una propiedad pública para la descripción del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="34cf3-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="34cf3-120">En este ejemplo, la descripción es "este es un complemento de Windows PowerShell que registra el cmdlet Get-proc".</span><span class="sxs-lookup"><span data-stu-id="34cf3-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="34cf3-121">Agregue una propiedad pública para el recurso de Descripción del complemento (opcional).</span><span class="sxs-lookup"><span data-stu-id="34cf3-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="34cf3-122">En este ejemplo, el recurso Vendor es "GetProcPSSnapIn01, es un complemento de Windows PowerShell que registra el cmdlet Get-proc".</span><span class="sxs-lookup"><span data-stu-id="34cf3-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="34cf3-123">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="34cf3-123">Example</span></span>

<span data-ttu-id="34cf3-124">En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que se puede usar para registrar el cmdlet Get-proc en el shell de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34cf3-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="34cf3-125">Tenga en cuenta que en este ejemplo, el ensamblado completo solo contendría la clase de complemento GetProcPSSnapIn01 y la clase de cmdlet Get-proc.</span><span class="sxs-lookup"><span data-stu-id="34cf3-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="34cf3-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="34cf3-126">See Also</span></span>

[<span data-ttu-id="34cf3-127">Cómo registrar cmdlets, proveedores y aplicaciones host</span><span class="sxs-lookup"><span data-stu-id="34cf3-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="34cf3-128">SDK de Windows PowerShell Shell</span><span class="sxs-lookup"><span data-stu-id="34cf3-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
