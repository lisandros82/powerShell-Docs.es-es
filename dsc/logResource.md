---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Log
ms.openlocfilehash: 72c9c5a9b8e2a4ed4ce43cfd792572ce95b502b3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-log-resource"></a><span data-ttu-id="ecd22-103">Recurso de DSC Log</span><span class="sxs-lookup"><span data-stu-id="ecd22-103">DSC Log Resource</span></span> 

> <span data-ttu-id="ecd22-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ecd22-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ecd22-105">El recurso __Log__ de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para escribir mensajes en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="ecd22-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="ecd22-106">Nota: De forma predeterminada, solo están habilitados los registros operativos para DSC.</span><span class="sxs-lookup"><span data-stu-id="ecd22-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="ecd22-107">Para que el registro analítico esté disponible o visible, es necesario habilitarlo.</span><span class="sxs-lookup"><span data-stu-id="ecd22-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="ecd22-108">Vea el artículo siguiente.</span><span class="sxs-lookup"><span data-stu-id="ecd22-108">See the following article.</span></span>

[<span data-ttu-id="ecd22-109">¿Dónde se encuentran los registros de eventos de DSC?</span><span class="sxs-lookup"><span data-stu-id="ecd22-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="ecd22-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ecd22-110">Properties</span></span>
|  <span data-ttu-id="ecd22-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ecd22-111">Property</span></span>  |  <span data-ttu-id="ecd22-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecd22-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="ecd22-113">Mensaje</span><span class="sxs-lookup"><span data-stu-id="ecd22-113">Message</span></span>| <span data-ttu-id="ecd22-114">Indica el mensaje que quiere escribir en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="ecd22-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>| 
| <span data-ttu-id="ecd22-115">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ecd22-115">DependsOn</span></span> | <span data-ttu-id="ecd22-116">Indica que la configuración de otro recurso debe ejecutarse antes de que se escriba este mensaje de registro.</span><span class="sxs-lookup"><span data-stu-id="ecd22-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="ecd22-117">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ecd22-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="ecd22-118">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ecd22-118">Example</span></span>

<span data-ttu-id="ecd22-119">En el ejemplo siguiente se muestra cómo incluir un mensaje en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="ecd22-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="ecd22-120">**Nota**: Si ejecuta [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) con este recurso configurado, siempre devolverá **$false**.</span><span class="sxs-lookup"><span data-stu-id="ecd22-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell 
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```

