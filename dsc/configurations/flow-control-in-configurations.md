---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Instrucciones condicionales y bucles en las configuraciones
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402314"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="a64fd-103">Instrucciones condicionales y bucles en las configuraciones</span><span class="sxs-lookup"><span data-stu-id="a64fd-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="a64fd-104">Puede hacer su [configuraciones](configurations.md) más dinámico con las palabras clave de control de flujo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a64fd-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="a64fd-105">En este artículo le mostrará cómo puede usar instrucciones condicionales y bucles para hacer que las configuraciones más dinámicas.</span><span class="sxs-lookup"><span data-stu-id="a64fd-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="a64fd-106">Combinación condicionales y bucles con [parámetros](add-parameters-to-a-configuration.md) y [datos de configuración](configData.md) permite más flexibilidad y control al compilar las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="a64fd-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="a64fd-107">Al igual que una función o un bloque de Script, puede usar cualquier lenguaje de PowerShell dentro de una configuración.</span><span class="sxs-lookup"><span data-stu-id="a64fd-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="a64fd-108">Solo se evaluarán las instrucciones que se utilizan cuando se llama a la configuración para compilar un archivo ".mof".</span><span class="sxs-lookup"><span data-stu-id="a64fd-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="a64fd-109">Los ejemplos siguientes muestran los escenarios sencillos para demostrar conceptos.</span><span class="sxs-lookup"><span data-stu-id="a64fd-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="a64fd-110">Instrucciones condicionales son los bucles se utilizan con más frecuencia con parámetros y datos de configuración.</span><span class="sxs-lookup"><span data-stu-id="a64fd-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="a64fd-111">En este sencillo ejemplo, la **servicio** bloque de recursos recupera el estado actual de un servicio en tiempo de compilación para generar un archivo de "MOF" que mantiene su estado actual.</span><span class="sxs-lookup"><span data-stu-id="a64fd-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="a64fd-112">Uso de bloques de recursos dinámicos adelantan a la eficacia de Intellisense.</span><span class="sxs-lookup"><span data-stu-id="a64fd-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="a64fd-113">El analizador de PowerShell no puede determinar si los valores especificados son aceptables, hasta que se compile la configuración.</span><span class="sxs-lookup"><span data-stu-id="a64fd-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="a64fd-114">Además, puede crear un **servicio** bloquear recursos para cada servicio en el equipo actual, utilizando un `foreach` bucle.</span><span class="sxs-lookup"><span data-stu-id="a64fd-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
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

<span data-ttu-id="a64fd-115">También sólo se podían crear configuraciones para las máquinas que estén en línea, mediante un sencillo `if` instrucción.</span><span class="sxs-lookup"><span data-stu-id="a64fd-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> <span data-ttu-id="a64fd-116">Bloquea el recurso dinámico en la referencia de los ejemplos anteriores en la máquina actual.</span><span class="sxs-lookup"><span data-stu-id="a64fd-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="a64fd-117">En este caso, lo que sería la máquina que se va a crear la configuración, no el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="a64fd-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="a64fd-118">Resumen</span><span class="sxs-lookup"><span data-stu-id="a64fd-118">Summary</span></span>

<span data-ttu-id="a64fd-119">En resumen, puede usar cualquier lenguaje de PowerShell dentro de una configuración.</span><span class="sxs-lookup"><span data-stu-id="a64fd-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="a64fd-120">Esto incluye cosas como:</span><span class="sxs-lookup"><span data-stu-id="a64fd-120">This includes things like:</span></span>

- <span data-ttu-id="a64fd-121">Objetos personalizados</span><span class="sxs-lookup"><span data-stu-id="a64fd-121">Custom Objects</span></span>
- <span data-ttu-id="a64fd-122">Tablas hash</span><span class="sxs-lookup"><span data-stu-id="a64fd-122">Hashtables</span></span>
- <span data-ttu-id="a64fd-123">Manipulación de cadenas</span><span class="sxs-lookup"><span data-stu-id="a64fd-123">String manipulation</span></span>
- <span data-ttu-id="a64fd-124">Comunicación remota</span><span class="sxs-lookup"><span data-stu-id="a64fd-124">Remoting</span></span>
- <span data-ttu-id="a64fd-125">WMI y CIM</span><span class="sxs-lookup"><span data-stu-id="a64fd-125">WMI and CIM</span></span>
- <span data-ttu-id="a64fd-126">Objetos de Active Directory</span><span class="sxs-lookup"><span data-stu-id="a64fd-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="a64fd-127">y más...</span><span class="sxs-lookup"><span data-stu-id="a64fd-127">and more...</span></span>

<span data-ttu-id="a64fd-128">Cualquier código de PowerShell definido en la configuración se evaluará un tiempo de compilación, pero también puede colocar código en el script que contiene la configuración.</span><span class="sxs-lookup"><span data-stu-id="a64fd-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="a64fd-129">Al importar la configuración, se ejecutará cualquier código fuera del bloque de configuración.</span><span class="sxs-lookup"><span data-stu-id="a64fd-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="a64fd-130">Vea también</span><span class="sxs-lookup"><span data-stu-id="a64fd-130">See also</span></span>

- [<span data-ttu-id="a64fd-131">Adición de parámetros a una configuración</span><span class="sxs-lookup"><span data-stu-id="a64fd-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="a64fd-132">Separación de los datos de configuración de las configuraciones</span><span class="sxs-lookup"><span data-stu-id="a64fd-132">Separate Configuration data from Configurations</span></span>](configData.md)
