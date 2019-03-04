---
title: Los parámetros de cmdlet dinámica | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853811"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="eed37-102">Parámetros dinámicos del cmdlet</span><span class="sxs-lookup"><span data-stu-id="eed37-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="eed37-103">Cmdlets puede definir los parámetros que están disponibles para el usuario bajo condiciones especiales, como cuando el argumento de otro parámetro es un valor específico.</span><span class="sxs-lookup"><span data-stu-id="eed37-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="eed37-104">Estos parámetros se agregan en tiempo de ejecución y se conocen como *parámetros dinámicos* porque se agregan solo cuando sean necesarios.</span><span class="sxs-lookup"><span data-stu-id="eed37-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="eed37-105">Por ejemplo, puede diseñar un cmdlet que agrega varios parámetros solo cuando se especifica un parámetro de modificador específico.</span><span class="sxs-lookup"><span data-stu-id="eed37-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="eed37-106">Los proveedores y las funciones de Windows PowerShell también pueden definir los parámetros dinámicos.</span><span class="sxs-lookup"><span data-stu-id="eed37-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="eed37-107">Parámetros dinámicos en los Cmdlets de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eed37-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="eed37-108">Windows PowerShell usa los parámetros dinámicos en varias de sus cmdlets de proveedor.</span><span class="sxs-lookup"><span data-stu-id="eed37-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="eed37-109">Por ejemplo, el `Get-Item` y `Get-ChildItem` agregar cmdlets un `CodeSigningCert` parámetro en tiempo de ejecución cuando el `Path` parámetro del cmdlet especifica la ruta de acceso del proveedor de certificados.</span><span class="sxs-lookup"><span data-stu-id="eed37-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="eed37-110">Si el `Path` parámetro del cmdlet especifica una ruta de acceso para un proveedor diferente, el `CodeSigningCert` parámetro no está disponible.</span><span class="sxs-lookup"><span data-stu-id="eed37-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="eed37-111">Los ejemplos siguientes muestran cómo el `CodeSigningCert` se agrega el parámetro en tiempo de ejecución cuando el `Get-Item` cmdlet se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="eed37-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="eed37-112">En el primer ejemplo, el tiempo de ejecución de Windows PowerShell agregó el parámetro y el cmdlet es correcto.</span><span class="sxs-lookup"><span data-stu-id="eed37-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="eed37-113">En el segundo ejemplo, se especifica una unidad de sistema de archivos y se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="eed37-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="eed37-114">El mensaje de error indica que el `CodeSigningCert` no se encuentra el parámetro.</span><span class="sxs-lookup"><span data-stu-id="eed37-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="eed37-115">Compatibilidad con los parámetros dinámicos</span><span class="sxs-lookup"><span data-stu-id="eed37-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="eed37-116">Para admitir los parámetros dinámicos, el código del cmdlet debe incluir los siguientes elementos.</span><span class="sxs-lookup"><span data-stu-id="eed37-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="eed37-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) esta interfaz proporciona el método que recupera los parámetros dinámicos.</span><span class="sxs-lookup"><span data-stu-id="eed37-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="eed37-118">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="eed37-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="eed37-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) este método recupera el objeto que contiene las definiciones de parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="eed37-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="eed37-120">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="eed37-120">Example:</span></span>

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

<span data-ttu-id="eed37-121">Clase de parámetro dinámico esta clase define los parámetros que se va a agregar.</span><span class="sxs-lookup"><span data-stu-id="eed37-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="eed37-122">Esta clase debe incluir un atributo de parámetro para cada parámetro y los atributos opcionales de Alias y la validación que son necesarios para el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eed37-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="eed37-123">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="eed37-123">Example:</span></span>

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

<span data-ttu-id="eed37-124">Para obtener un ejemplo completo de un cmdlet que admite parámetros dinámicos, consulte [cómo declarar los parámetros dinámicos](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="eed37-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eed37-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="eed37-125">See Also</span></span>

[<span data-ttu-id="eed37-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="eed37-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="eed37-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="eed37-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="eed37-128">Cómo declarar los parámetros dinámicos</span><span class="sxs-lookup"><span data-stu-id="eed37-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="eed37-129">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eed37-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
