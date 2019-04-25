---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 1153738fdf6f926d5d819bbf91450408dcb17f71
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057815"
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a><span data-ttu-id="8d4f7-102">Generar cmdlets de PowerShell basados en el punto de conexión de OData</span><span class="sxs-lookup"><span data-stu-id="8d4f7-102">Generate PowerShell Cmdlets based on OData Endpoint</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a><span data-ttu-id="8d4f7-103">Generar cmdlets de Windows PowerShell basados en el punto de conexión de OData</span><span class="sxs-lookup"><span data-stu-id="8d4f7-103">Generate Windows PowerShell cmdlets based on an OData endpoint</span></span>

<span data-ttu-id="8d4f7-104">**Export-ODataEndpointProxy** es un cmdlet que genera un conjunto de cmdlets de Windows PowerShell basados en la funcionalidad expuesta por un punto de conexión de OData determinado.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-104">**Export-ODataEndpointProxy** is a cmdlet that generates a set of Windows PowerShell cmdlets based on the functionality exposed by a given OData endpoint.</span></span>

<span data-ttu-id="8d4f7-105">El siguiente ejemplo muestra cómo usar este nuevo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="8d4f7-105">The following example shows how to use this new cmdlet:</span></span>

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

<span data-ttu-id="8d4f7-106">Todavía hay partes de casos de uso clave en el desarrollo de esta funcionalidad. Son, sin limitación:</span><span class="sxs-lookup"><span data-stu-id="8d4f7-106">There are still parts of key use cases in development for this functionality, including, but not limited to:</span></span>
-   <span data-ttu-id="8d4f7-107">Asociaciones</span><span class="sxs-lookup"><span data-stu-id="8d4f7-107">Associations</span></span>
-   <span data-ttu-id="8d4f7-108">Flujos de paso</span><span class="sxs-lookup"><span data-stu-id="8d4f7-108">Passing streams</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="8d4f7-109">Generar cmdlets de Windows PowerShell basados en un punto de conexión de OData con ODataUtils</span><span class="sxs-lookup"><span data-stu-id="8d4f7-109">Generate Windows PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="8d4f7-110">El módulo ODataUtils permite la generación de cmdlets de Windows PowerShell desde los puntos de conexión de REST que admiten OData.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-110">The ODataUtils module allows generation of Windows PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="8d4f7-111">Las siguientes mejoras incrementales se incluyen en el módulo Microsoft.PowerShell.ODataUtils de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-111">The following incremental enhancements are in the Microsoft.PowerShell.ODataUtils Windows PowerShell module.</span></span>
-   <span data-ttu-id="8d4f7-112">Canalización de información adicional del punto de conexión del lado servidor al lado cliente.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-112">Channel additional information from server-side endpoint to client side.</span></span>
-   <span data-ttu-id="8d4f7-113">Compatibilidad con la paginación del lado cliente.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-113">Client-side paging support</span></span>
-   <span data-ttu-id="8d4f7-114">Filtrado del lado servidor mediante el parámetro -Select.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-114">Server-side filtering by using the -Select parameter</span></span>
-   <span data-ttu-id="8d4f7-115">Compatibilidad con los encabezados de solicitud web.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-115">Support for web request headers</span></span>

<span data-ttu-id="8d4f7-116">Los cmdlets de proxy que genera el cmdlet Export-ODataEndPointProxy proporcionan información adicional (no mencionada en los $metadatos usados durante la generación de proxy del lado cliente) del punto de conexión de OData lado servidor en el flujo de información (una nueva característica de Windows PowerShell 5.0).</span><span class="sxs-lookup"><span data-stu-id="8d4f7-116">The proxy cmdlets generated by the Export-ODataEndPointProxy cmdlet provide additional information (not mentioned in the $metadata used during the client-side proxy generation) from the server side OData endpoint on the Information stream (a new Windows PowerShell 5.0 feature).</span></span> <span data-ttu-id="8d4f7-117">A continuación se ofrece un ejemplo de cómo obtener esa información.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-117">Here is an example of how to get that information.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

<span data-ttu-id="8d4f7-118">Puede obtener los registros del lado servidor en lotes mediante la compatibilidad con la paginación del lado cliente.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-118">You can get the records from the server side in batches by using client-side paging support.</span></span> <span data-ttu-id="8d4f7-119">Resulta útil cuando se necesita obtener una gran cantidad de datos del servidor a través de la red.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-119">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

<span data-ttu-id="8d4f7-120">Los cmdlets de proxy generados admiten el parámetro –Select, que puede usar como un filtro para recibir solamente las propiedades de registro que el cliente necesita.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-120">The generated proxy cmdlets support the –Select parameter which you can use as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="8d4f7-121">Esto reduce la cantidad de datos que se transfieren a través de la red, ya que el filtrado se produce en el lado servidor.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-121">This reduces the amount of data that is transferred over the network, because the filtering occurs on the server side.</span></span>

```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="8d4f7-122">El cmdlet Export-ODataEndpointProxy y los cmdlets de proxy que este genera admite ahora el parámetro Headers (proporcione valores como una tabla hash), que puede usar para canalizar cualquier información adicional que espere el punto de conexión de OData del lado servidor.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-122">The Export-ODataEndpointProxy cmdlet, and the proxy cmdlets generated by it, now support the Headers parameter (supply values as a hash table), which you can use to channel any additional information that is expected by the server-side OData endpoint.</span></span> <span data-ttu-id="8d4f7-123">En el ejemplo siguiente, puede canalizar una clave de suscripción a través de los encabezados de los servicios que esperan una clave de suscripción para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8d4f7-123">In the following example, you can channel a Subscription key through Headers for services that are expecting a Subscription key for authentication.</span></span>

```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
