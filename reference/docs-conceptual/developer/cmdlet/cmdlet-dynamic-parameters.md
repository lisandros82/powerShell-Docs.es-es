---
title: Parámetros dinámicos de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369884"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="522cb-102">Parámetros dinámicos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="522cb-102">Cmdlet dynamic parameters</span></span>

<span data-ttu-id="522cb-103">Los cmdlets pueden definir parámetros que están disponibles para el usuario en condiciones especiales, como cuando el argumento de otro parámetro es un valor específico.</span><span class="sxs-lookup"><span data-stu-id="522cb-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="522cb-104">Estos parámetros se agregan en tiempo de ejecución y se denominan parámetros dinámicos, ya que solo se agregan cuando se necesitan.</span><span class="sxs-lookup"><span data-stu-id="522cb-104">These parameters are added at runtime and are referred to as dynamic parameters because they're only added when needed.</span></span> <span data-ttu-id="522cb-105">Por ejemplo, puede diseñar un cmdlet que agregue varios parámetros solo cuando se especifica un parámetro de modificador específico.</span><span class="sxs-lookup"><span data-stu-id="522cb-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="522cb-106">Los proveedores y las funciones de PowerShell también pueden definir parámetros dinámicos.</span><span class="sxs-lookup"><span data-stu-id="522cb-106">Providers and PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-powershell-cmdlets"></a><span data-ttu-id="522cb-107">Parámetros dinámicos en cmdlets de PowerShell</span><span class="sxs-lookup"><span data-stu-id="522cb-107">Dynamic parameters in PowerShell cmdlets</span></span>

<span data-ttu-id="522cb-108">PowerShell usa parámetros dinámicos en varios de sus cmdlets de proveedor.</span><span class="sxs-lookup"><span data-stu-id="522cb-108">PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="522cb-109">Por ejemplo, los cmdlets `Get-Item` y `Get-ChildItem` agregan un parámetro **CodeSigningCert** en tiempo de ejecución cuando el parámetro **path** especifica la ruta de acceso del proveedor de **certificados** .</span><span class="sxs-lookup"><span data-stu-id="522cb-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a **CodeSigningCert** parameter at runtime when the **Path** parameter specifies the **Certificate** provider path.</span></span> <span data-ttu-id="522cb-110">Si el parámetro **path** especifica una ruta de acceso para un proveedor diferente, el parámetro **CodeSigningCert** no está disponible.</span><span class="sxs-lookup"><span data-stu-id="522cb-110">If the **Path** parameter specifies a path for a different provider, the **CodeSigningCert** parameter isn't available.</span></span>

<span data-ttu-id="522cb-111">En los siguientes ejemplos se muestra cómo se agrega el parámetro **CodeSigningCert** en tiempo de ejecución cuando se ejecuta `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="522cb-111">The following examples show how the **CodeSigningCert** parameter is added at runtime when `Get-Item` is run.</span></span>

<span data-ttu-id="522cb-112">En este ejemplo, el tiempo de ejecución de PowerShell agregó el parámetro y el cmdlet se realiza correctamente.</span><span class="sxs-lookup"><span data-stu-id="522cb-112">In this example, the PowerShell runtime has added the parameter and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="522cb-113">En este ejemplo, se especifica una unidad del **sistema de archivos** y se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="522cb-113">In this example, a **FileSystem** drive is specified and an error is returned.</span></span> <span data-ttu-id="522cb-114">El mensaje de error indica que no se encuentra el parámetro **CodeSigningCert** .</span><span class="sxs-lookup"><span data-stu-id="522cb-114">The error message indicates that the **CodeSigningCert** parameter can't be found.</span></span>

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="522cb-115">Compatibilidad con parámetros dinámicos</span><span class="sxs-lookup"><span data-stu-id="522cb-115">Support for dynamic parameters</span></span>

<span data-ttu-id="522cb-116">Para admitir los parámetros dinámicos, se deben incluir los siguientes elementos en el código del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="522cb-116">To support dynamic parameters, the following elements must be included in the cmdlet code.</span></span>

### <a name="interface"></a><span data-ttu-id="522cb-117">Interfaz</span><span class="sxs-lookup"><span data-stu-id="522cb-117">Interface</span></span>

<span data-ttu-id="522cb-118">[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="522cb-118">[System.Management.Automation.IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span></span>
<span data-ttu-id="522cb-119">Esta interfaz proporciona el método que recupera los parámetros dinámicos.</span><span class="sxs-lookup"><span data-stu-id="522cb-119">This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="522cb-120">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="522cb-120">For example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a><span data-ttu-id="522cb-121">Método</span><span class="sxs-lookup"><span data-stu-id="522cb-121">Method</span></span>

<span data-ttu-id="522cb-122">[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="522cb-122">[System.Management.Automation.IDynamicParameters.GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span></span>
<span data-ttu-id="522cb-123">Este método recupera el objeto que contiene las definiciones de parámetros dinámicos.</span><span class="sxs-lookup"><span data-stu-id="522cb-123">This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="522cb-124">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="522cb-124">For example:</span></span>

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

### <a name="class"></a><span data-ttu-id="522cb-125">Clase</span><span class="sxs-lookup"><span data-stu-id="522cb-125">Class</span></span>

<span data-ttu-id="522cb-126">Una clase que define los parámetros dinámicos que se van a agregar.</span><span class="sxs-lookup"><span data-stu-id="522cb-126">A class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="522cb-127">Esta clase debe incluir un atributo de **parámetro** para cada parámetro y cualquier atributo opcional de **alias** y **validación** que necesite el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="522cb-127">This class must include a **Parameter** attribute for each parameter and any optional **Alias** and **Validation** attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="522cb-128">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="522cb-128">For example:</span></span>

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

<span data-ttu-id="522cb-129">Para obtener un ejemplo completo de un cmdlet que admite parámetros dinámicos, vea [cómo declarar parámetros dinámicos](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="522cb-129">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="522cb-130">Consulta también</span><span class="sxs-lookup"><span data-stu-id="522cb-130">See also</span></span>

[<span data-ttu-id="522cb-131">System. Management. Automation. IDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="522cb-131">System.Management.Automation.IDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="522cb-132">System. Management. Automation. IDynamicParameters. GetDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="522cb-132">System.Management.Automation.IDynamicParameters.GetDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="522cb-133">Cómo declarar parámetros dinámicos</span><span class="sxs-lookup"><span data-stu-id="522cb-133">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="522cb-134">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="522cb-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
