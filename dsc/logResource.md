---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Log
ms.openlocfilehash: fade94efd8133ae0172737e4bb1aed89fc0f97d9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093483"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="eb8df-103">Recurso de DSC Log</span><span class="sxs-lookup"><span data-stu-id="eb8df-103">DSC Log Resource</span></span>

> <span data-ttu-id="eb8df-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="eb8df-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="eb8df-105">El recurso __Log__ de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para escribir mensajes en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="eb8df-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="eb8df-106">De forma predeterminada, solo están habilitados los registros operativos para DSC.</span><span class="sxs-lookup"><span data-stu-id="eb8df-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="eb8df-107">Para que el registro analítico esté disponible o visible, es necesario habilitarlo.</span><span class="sxs-lookup"><span data-stu-id="eb8df-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="eb8df-108">Para más información, consulte [¿Dónde se encuentran los registros de eventos de DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)</span><span class="sxs-lookup"><span data-stu-id="eb8df-108">For more information, see [Where are DSC Event Logs?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="eb8df-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="eb8df-109">Properties</span></span>

|  <span data-ttu-id="eb8df-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="eb8df-110">Property</span></span>  |  <span data-ttu-id="eb8df-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="eb8df-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="eb8df-112">Mensaje</span><span class="sxs-lookup"><span data-stu-id="eb8df-112">Message</span></span>| <span data-ttu-id="eb8df-113">Indica el mensaje que quiere escribir en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="eb8df-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="eb8df-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="eb8df-114">DependsOn</span></span> | <span data-ttu-id="eb8df-115">Indica que la configuración de otro recurso debe ejecutarse antes de que se escriba este mensaje de registro.</span><span class="sxs-lookup"><span data-stu-id="eb8df-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="eb8df-116">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="eb8df-116">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="eb8df-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="eb8df-117">Example</span></span>

<span data-ttu-id="eb8df-118">En el ejemplo siguiente se muestra cómo incluir un mensaje en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="eb8df-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="eb8df-119">Si ejecuta [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) con este recurso configurado, siempre devolverá **$false**.</span><span class="sxs-lookup"><span data-stu-id="eb8df-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```