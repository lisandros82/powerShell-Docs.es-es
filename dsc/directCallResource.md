---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Llamada directa a los métodos de recursos de DSC
ms.openlocfilehash: 3ec3a3a8da615f45f3fdd28b1c1e46e312507ed5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189625"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="a1aff-103">Llamada directa a los métodos de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="a1aff-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="a1aff-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a1aff-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a1aff-105">Puede usar el cmdlet [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) para llamar directamente a las funciones o métodos de un recurso de DSC (las funciones **Get-TargetResource**, **Set-TargetResource** y **Test-TargetResource** de un recurso basado en MOF o los métodos **Get**, **Set** y **Test** de un recurso basado en clases).</span><span class="sxs-lookup"><span data-stu-id="a1aff-105">You can use the [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="a1aff-106">Esto puede servir para terceros que quieran usar recursos de DSC, o como herramienta útil durante el desarrollo de recursos.</span><span class="sxs-lookup"><span data-stu-id="a1aff-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="a1aff-107">Este cmdlet suele usarse en combinación con una propiedad de metaconfiguración `refreshMode = 'Disabled'`, pero se puede usar independientemente de la opción establecida en **refreshMode**.</span><span class="sxs-lookup"><span data-stu-id="a1aff-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="a1aff-108">Al llamar al cmdlet **Invoke-DscResource**, debe especificar qué método o función llamar mediante el parámetro **Method**.</span><span class="sxs-lookup"><span data-stu-id="a1aff-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="a1aff-109">Especifique las propiedades del recurso pasando una tabla hash como el valor del parámetro **Property**.</span><span class="sxs-lookup"><span data-stu-id="a1aff-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="a1aff-110">A continuación, se muestran ejemplos de llamada directa a los métodos de recursos:</span><span class="sxs-lookup"><span data-stu-id="a1aff-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="a1aff-111">Asegurarse de que un archivo está presente</span><span class="sxs-lookup"><span data-stu-id="a1aff-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="a1aff-112">Comprobar que un archivo está presente</span><span class="sxs-lookup"><span data-stu-id="a1aff-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="a1aff-113">Obtener el contenido del archivo</span><span class="sxs-lookup"><span data-stu-id="a1aff-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="a1aff-114">**Nota:** No se admite llamar directamente a métodos de recursos compuestos.</span><span class="sxs-lookup"><span data-stu-id="a1aff-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="a1aff-115">En su lugar, llame a los métodos de los recursos subyacentes que forman el recurso compuesto.</span><span class="sxs-lookup"><span data-stu-id="a1aff-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1aff-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="a1aff-116">See Also</span></span>
- [<span data-ttu-id="a1aff-117">Escribir un recurso de DSC personalizado con MOF</span><span class="sxs-lookup"><span data-stu-id="a1aff-117">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="a1aff-118">Escribir un recurso de DSC personalizado con clases de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1aff-118">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="a1aff-119">Depuración de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="a1aff-119">Debugging DSC resources</span></span>](debugResource.md)