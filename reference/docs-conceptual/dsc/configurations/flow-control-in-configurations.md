---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Instrucciones condicionales y bucles en las configuraciones
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736903"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a><span data-ttu-id="3f400-103">Instrucciones condicionales y bucles en una configuración</span><span class="sxs-lookup"><span data-stu-id="3f400-103">Conditional statements and loops in a Configuration</span></span>

<span data-ttu-id="3f400-104">Puede hacer que sus [configuraciones](configurations.md) sean más dinámicas con las palabras clave de control de flujo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f400-104">You can make your [Configuration](configurations.md) more dynamic by using PowerShell flow-control keywords.</span></span> <span data-ttu-id="3f400-105">En este artículo se muestra cómo puede usar instrucciones condicionales y bucles para hacer que sus `Configuration` sean más dinámicas.</span><span class="sxs-lookup"><span data-stu-id="3f400-105">This article shows you how you can use conditional statements and loops to make your `Configuration` more dynamic.</span></span> <span data-ttu-id="3f400-106">La combinación de instrucciones condicionales y bucles con [parámetros](add-parameters-to-a-configuration.md) y [datos de configuración](configData.md) le concede más flexibilidad y control al compilar sus `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="3f400-106">Combining conditional statements and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your `Configuration`.</span></span>

<span data-ttu-id="3f400-107">Al igual que una función o un bloque de script, puede usar cualquier lenguaje de PowerShell dentro de una `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="3f400-107">Just like a function or a script block, you can use any PowerShell language feature within a `Configuration`.</span></span>
<span data-ttu-id="3f400-108">Las declaraciones que use solo se evaluarán cuando llame a su `Configuration` para compilar un archivo `.mof`.</span><span class="sxs-lookup"><span data-stu-id="3f400-108">The statements you use will only be evaluated when you call your `Configuration` to compile a `.mof` file.</span></span> <span data-ttu-id="3f400-109">Los ejemplos siguientes muestran escenarios para demostrar conceptos.</span><span class="sxs-lookup"><span data-stu-id="3f400-109">The examples below show scenarios to demonstrate concepts.</span></span> <span data-ttu-id="3f400-110">Las instrucciones condicionales y bucles se usan más a menudo con parámetros y datos de configuración.</span><span class="sxs-lookup"><span data-stu-id="3f400-110">Conditional statements and loops are more often used with parameters and configuration Data.</span></span>

<span data-ttu-id="3f400-111">En este ejemplo, el bloque de recursos **Service** recupera el estado actual de un servicio en tiempo de compilación para generar un archivo `.mof` que mantiene su estado actual.</span><span class="sxs-lookup"><span data-stu-id="3f400-111">In this  example, the **Service** resource block retrieves the current state of a service at compile time to generate a `.mof` file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="3f400-112">El uso de bloques de recursos dinámicos se anticipará a la eficacia de Intellisense.</span><span class="sxs-lookup"><span data-stu-id="3f400-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="3f400-113">El analizador de PowerShell no puede determinar si los valores especificados son aceptables hasta que se compile la `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="3f400-113">The PowerShell parser cannot determine if the values specified are acceptable until the `Configuration` is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="3f400-114">Además, puede crear un bloque de recurso **Service** para cada servicio de la máquina actual, mediante el uso de un bucle `foreach`.</span><span class="sxs-lookup"><span data-stu-id="3f400-114">Additionally, you could create a **Service** resource block for every service on the current machine using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="3f400-115">También puede crear una `Configuration` solo para las máquinas que están en línea mediante una instrucción `if`.</span><span class="sxs-lookup"><span data-stu-id="3f400-115">You could also create a `Configuration` only for machines that are online by using an `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="3f400-116">Los bloques de recursos dinámicos de los ejemplos anteriores hacen referencia a la máquina actual.</span><span class="sxs-lookup"><span data-stu-id="3f400-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="3f400-117">En este caso, sería la máquina en la que está creando la `Configuration`, no el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="3f400-117">In this instance, that would be the machine you are authoring the `Configuration` on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="3f400-118">Resumen</span><span class="sxs-lookup"><span data-stu-id="3f400-118">Summary</span></span>

<span data-ttu-id="3f400-119">En resumen, puede usar cualquier lenguaje de PowerShell dentro de una `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="3f400-119">In summary, you can use any PowerShell language feature within a `Configuration`.</span></span>

<span data-ttu-id="3f400-120">Esto incluye elementos como:</span><span class="sxs-lookup"><span data-stu-id="3f400-120">This includes things like:</span></span>

- <span data-ttu-id="3f400-121">Objetos personalizados</span><span class="sxs-lookup"><span data-stu-id="3f400-121">Custom Objects</span></span>
- <span data-ttu-id="3f400-122">Tablas hash</span><span class="sxs-lookup"><span data-stu-id="3f400-122">Hashtables</span></span>
- <span data-ttu-id="3f400-123">Manipulación de cadenas</span><span class="sxs-lookup"><span data-stu-id="3f400-123">String manipulation</span></span>
- <span data-ttu-id="3f400-124">Comunicación remota</span><span class="sxs-lookup"><span data-stu-id="3f400-124">Remoting</span></span>
- <span data-ttu-id="3f400-125">WMI y CIM</span><span class="sxs-lookup"><span data-stu-id="3f400-125">WMI and CIM</span></span>
- <span data-ttu-id="3f400-126">Objetos de ActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="3f400-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="3f400-127">y más...</span><span class="sxs-lookup"><span data-stu-id="3f400-127">and more...</span></span>

<span data-ttu-id="3f400-128">Cualquier código de PowerShell definido en una `Configuration` se evalúa en tiempo de compilación, pero también puede colocar código en el script que contiene `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="3f400-128">Any PowerShell code defined in a `Configuration` is evaluated at compile time, but you can also place code in the script containing your `Configuration`.</span></span> <span data-ttu-id="3f400-129">Cualquier código fuera del bloque `Configuration` se ejecuta al importar la `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="3f400-129">Any code outside of the `Configuration` block is executed when you import your `Configuration`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f400-130">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3f400-130">See also</span></span>

- [<span data-ttu-id="3f400-131">Adición de parámetros a una configuración</span><span class="sxs-lookup"><span data-stu-id="3f400-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="3f400-132">Separación de los datos de configuración de las configuraciones</span><span class="sxs-lookup"><span data-stu-id="3f400-132">Separate Configuration data from Configurations</span></span>](configData.md)
