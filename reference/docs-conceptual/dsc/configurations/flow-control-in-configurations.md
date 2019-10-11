---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Instrucciones condicionales y bucles en las configuraciones
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954082"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="58437-103">Instrucciones condicionales y bucles en las configuraciones</span><span class="sxs-lookup"><span data-stu-id="58437-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="58437-104">Puede hacer que sus [configuraciones](configurations.md) sean más dinámicas con las palabras clave de control de flujo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58437-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="58437-105">Este artículo le mostrará cómo puede usar instrucciones condicionales y bucles para hacer que sus configuraciones sean más dinámicas.</span><span class="sxs-lookup"><span data-stu-id="58437-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="58437-106">La combinación de condicionales y bucles con [parámetros](add-parameters-to-a-configuration.md) y [datos de configuración](configData.md) le concede más flexibilidad y control al compilar sus configuraciones.</span><span class="sxs-lookup"><span data-stu-id="58437-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="58437-107">Al igual que una función o un bloque de script, puede usar cualquier lenguaje de PowerShell dentro de una configuración.</span><span class="sxs-lookup"><span data-stu-id="58437-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="58437-108">Las declaraciones que use solo se evaluarán cuando llame a su configuración para compilar un archivo ".mof".</span><span class="sxs-lookup"><span data-stu-id="58437-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="58437-109">Los ejemplos siguientes muestran escenarios sencillos para demostrar conceptos.</span><span class="sxs-lookup"><span data-stu-id="58437-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="58437-110">Los condicionales son bucles que se usan más a menudo con parámetros y datos de configuración.</span><span class="sxs-lookup"><span data-stu-id="58437-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="58437-111">En este sencillo ejemplo, el bloque de recursos **Service** recupera el estado actual de un servicio en tiempo de compilación para generar un archivo ".mof" que mantiene su estado actual.</span><span class="sxs-lookup"><span data-stu-id="58437-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="58437-112">El uso de bloques de recursos dinámicos se anticipará a la eficacia de Intellisense.</span><span class="sxs-lookup"><span data-stu-id="58437-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="58437-113">El analizador de PowerShell no puede determinar si los valores especificados son aceptables hasta que se compile la configuración.</span><span class="sxs-lookup"><span data-stu-id="58437-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="58437-114">Además, puede crear un recurso de bloque **Service** para cada servicio de la máquina actual, mediante el uso de un bucle `foreach`.</span><span class="sxs-lookup"><span data-stu-id="58437-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

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

<span data-ttu-id="58437-115">También puede crear configuraciones solo para máquinas que estén en línea, utilizando una simple instrucción `if`.</span><span class="sxs-lookup"><span data-stu-id="58437-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

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
> <span data-ttu-id="58437-116">Los bloques de recursos dinámicos de los ejemplos anteriores hacen referencia a la máquina actual.</span><span class="sxs-lookup"><span data-stu-id="58437-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="58437-117">En este caso, sería la máquina en la que está creando la configuración, no el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="58437-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="58437-118">Resumen</span><span class="sxs-lookup"><span data-stu-id="58437-118">Summary</span></span>

<span data-ttu-id="58437-119">En resumen, puede usar cualquier lenguaje de PowerShell dentro de una configuración.</span><span class="sxs-lookup"><span data-stu-id="58437-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="58437-120">Esto incluye elementos como:</span><span class="sxs-lookup"><span data-stu-id="58437-120">This includes things like:</span></span>

- <span data-ttu-id="58437-121">Objetos personalizados</span><span class="sxs-lookup"><span data-stu-id="58437-121">Custom Objects</span></span>
- <span data-ttu-id="58437-122">Tablas hash</span><span class="sxs-lookup"><span data-stu-id="58437-122">Hashtables</span></span>
- <span data-ttu-id="58437-123">Manipulación de cadenas</span><span class="sxs-lookup"><span data-stu-id="58437-123">String manipulation</span></span>
- <span data-ttu-id="58437-124">Comunicación remota</span><span class="sxs-lookup"><span data-stu-id="58437-124">Remoting</span></span>
- <span data-ttu-id="58437-125">WMI y CIM</span><span class="sxs-lookup"><span data-stu-id="58437-125">WMI and CIM</span></span>
- <span data-ttu-id="58437-126">Objetos de ActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="58437-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="58437-127">y más...</span><span class="sxs-lookup"><span data-stu-id="58437-127">and more...</span></span>

<span data-ttu-id="58437-128">Cualquier código de PowerShell definido en una configuración se evaluará en un tiempo de compilación, pero también puede colocar el código en el script que contiene su configuración.</span><span class="sxs-lookup"><span data-stu-id="58437-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="58437-129">Al importar la configuración, se ejecutará cualquier código fuera del bloque de configuración.</span><span class="sxs-lookup"><span data-stu-id="58437-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="58437-130">Vea también</span><span class="sxs-lookup"><span data-stu-id="58437-130">See also</span></span>

- [<span data-ttu-id="58437-131">Adición de parámetros a una configuración</span><span class="sxs-lookup"><span data-stu-id="58437-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="58437-132">Separación de los datos de configuración de las configuraciones</span><span class="sxs-lookup"><span data-stu-id="58437-132">Separate Configuration data from Configurations</span></span>](configData.md)
