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
ms.openlocfilehash: d4f57c062fee09e85c290445082be745ab229985
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795041"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="a0c19-102">Escritura de un complemento de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0c19-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="a0c19-103">En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que puede usarse para registrar todos los cmdlets y proveedores de Windows PowerShell en un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="a0c19-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="a0c19-104">Con este tipo de complemento, no seleccione qué cmdlets y proveedores que desea registrar.</span><span class="sxs-lookup"><span data-stu-id="a0c19-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="a0c19-105">Para escribir un complemento que le permite seleccionar lo que está registrado, consulte [escribir un Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="a0c19-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="a0c19-106">Escritura de un complemento de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0c19-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="a0c19-107">Agregue el atributo RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="a0c19-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="a0c19-108">Cree una clase pública que se deriva el [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) clase.</span><span class="sxs-lookup"><span data-stu-id="a0c19-108">Create a public class that derives from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="a0c19-109">En este ejemplo, el nombre de clase es "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="a0c19-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="a0c19-110">Agregue una propiedad pública para el nombre del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="a0c19-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="a0c19-111">Al asignar nombres a complementos, no utilice ninguno de los siguientes caracteres: #.</span><span class="sxs-lookup"><span data-stu-id="a0c19-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="a0c19-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="a0c19-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="a0c19-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="a0c19-113">@ \` \*</span></span>

    <span data-ttu-id="a0c19-114">En este ejemplo, el nombre del complemento de es "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="a0c19-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="a0c19-115">Agregue una propiedad pública para el proveedor del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="a0c19-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="a0c19-116">En este ejemplo, el proveedor es "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="a0c19-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="a0c19-117">Agregue una propiedad pública para el recurso del proveedor del complemento de (opcional).</span><span class="sxs-lookup"><span data-stu-id="a0c19-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="a0c19-118">En este ejemplo, el recurso del proveedor es "GetProcPSSnapIn01, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="a0c19-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="a0c19-119">Agregue una propiedad pública de la descripción del complemento (obligatorio).</span><span class="sxs-lookup"><span data-stu-id="a0c19-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="a0c19-120">En este ejemplo, la descripción es "Esto es un complemento de Windows PowerShell que se registra el cmdlet get-proc".</span><span class="sxs-lookup"><span data-stu-id="a0c19-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="a0c19-121">Agregue una propiedad pública para el recurso de descripción del complemento de (opcional).</span><span class="sxs-lookup"><span data-stu-id="a0c19-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="a0c19-122">En este ejemplo, el recurso del proveedor es "GetProcPSSnapIn01, esto es un complemento de Windows PowerShell que se registra el cmdlet get-proc".</span><span class="sxs-lookup"><span data-stu-id="a0c19-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="a0c19-123">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a0c19-123">Example</span></span>

<span data-ttu-id="a0c19-124">En este ejemplo se muestra cómo escribir un complemento de Windows PowerShell que puede usarse para registrar el cmdlet Get-Proc en el shell de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a0c19-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="a0c19-125">Tenga en cuenta que en este ejemplo, el ensamblado completo contendría únicamente la GetProcPSSnapIn01 complemento de clase y la clase del cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="a0c19-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a0c19-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="a0c19-126">See Also</span></span>

[<span data-ttu-id="a0c19-127">Cómo registrar Cmdlets, proveedores y aplicaciones Host</span><span class="sxs-lookup"><span data-stu-id="a0c19-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="a0c19-128">Shell de SDK de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0c19-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
