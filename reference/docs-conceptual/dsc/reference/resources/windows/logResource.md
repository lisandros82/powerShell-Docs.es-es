---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Log
ms.openlocfilehash: a1b7bf44fbaf36a3adaf0666e9f0a754fa3f6ee1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954672"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="04615-103">Recurso de DSC Log</span><span class="sxs-lookup"><span data-stu-id="04615-103">DSC Log Resource</span></span>

> <span data-ttu-id="04615-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="04615-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="04615-105">El recurso **Log** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para escribir mensajes en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="04615-105">The **Log** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

## <a name="syntax"></a><span data-ttu-id="04615-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="04615-106">Syntax</span></span>

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="04615-107">De forma predeterminada, solo están habilitados los registros operativos para DSC.</span><span class="sxs-lookup"><span data-stu-id="04615-107">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="04615-108">Para que el registro analítico esté disponible o visible, es necesario habilitarlo.</span><span class="sxs-lookup"><span data-stu-id="04615-108">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="04615-109">Para más información, consulte [¿Dónde se encuentran los registros de eventos de DSC?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs)</span><span class="sxs-lookup"><span data-stu-id="04615-109">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="04615-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="04615-110">Properties</span></span>

|<span data-ttu-id="04615-111">Propiedad</span><span class="sxs-lookup"><span data-stu-id="04615-111">Property</span></span> |<span data-ttu-id="04615-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="04615-112">Description</span></span> |
|---|---|
|<span data-ttu-id="04615-113">Mensaje</span><span class="sxs-lookup"><span data-stu-id="04615-113">Message</span></span> |<span data-ttu-id="04615-114">Indica el mensaje que quiere escribir en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="04615-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="04615-115">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="04615-115">Common properties</span></span>

|<span data-ttu-id="04615-116">Propiedad</span><span class="sxs-lookup"><span data-stu-id="04615-116">Property</span></span> |<span data-ttu-id="04615-117">Descripción</span><span class="sxs-lookup"><span data-stu-id="04615-117">Description</span></span> |
|---|---|
|<span data-ttu-id="04615-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="04615-118">DependsOn</span></span> |<span data-ttu-id="04615-119">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="04615-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="04615-120">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="04615-120">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="04615-121">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="04615-121">PsDscRunAsCredential</span></span> |<span data-ttu-id="04615-122">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="04615-122">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="04615-123">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="04615-123">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="04615-124">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="04615-124">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="04615-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="04615-125">Example</span></span>

<span data-ttu-id="04615-126">En el ejemplo siguiente se muestra cómo incluir un mensaje en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="04615-126">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="04615-127">Si ejecuta [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) con este recurso configurado, siempre devolverá **$false**.</span><span class="sxs-lookup"><span data-stu-id="04615-127">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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