---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
contributor: vaibch
title: Error de cmdlets de Network Switch Manager
ms.openlocfilehash: 626809513e7a8f1aa2c47a48c74e69ca4077f598
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
<span data-ttu-id="6f4e0-103">Los cmdlets de Network Switch Manager se pueden usar para administrar modificadores de red a través de WSMAN.</span><span class="sxs-lookup"><span data-stu-id="6f4e0-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="6f4e0-104">Algunos cmdlets de este módulo pueden aceptar valores de canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="6f4e0-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="6f4e0-105">En la versión preliminar de WMF 5.1, los cmdlets que pueden aceptar el valor de la canalización no pueden ejecutarse si los valores no pasan a través de canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="6f4e0-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="6f4e0-106">Si no se usa el parámetro "InputObject", el cmdlet debería continuar ejecutándose sin errores.</span><span class="sxs-lookup"><span data-stu-id="6f4e0-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="6f4e0-107">Esta es la lista de cmdlets afectados; es decir, estos cmdlets pueden aceptar el valor del parámetro "InputObject" de la canalización.</span><span class="sxs-lookup"><span data-stu-id="6f4e0-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="6f4e0-108">Si no se pasa este valor de la canalización, se producirá un error en la ejecución del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6f4e0-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="6f4e0-109">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="6f4e0-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="6f4e0-110">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="6f4e0-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="6f4e0-111">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="6f4e0-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="6f4e0-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="6f4e0-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="6f4e0-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="6f4e0-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="6f4e0-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="6f4e0-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="6f4e0-115">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="6f4e0-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="6f4e0-116">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="6f4e0-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="6f4e0-117">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="6f4e0-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="6f4e0-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="6f4e0-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="6f4e0-119">Solución</span><span class="sxs-lookup"><span data-stu-id="6f4e0-119">Resolution</span></span>
<span data-ttu-id="6f4e0-120">Los cmdlets funcionan bien cuando el valor del parámetro InputObject se pasa a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="6f4e0-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="6f4e0-121">Algunos ejemplos que funcionan con los cmdlets anteriores son:</span><span class="sxs-lookup"><span data-stu-id="6f4e0-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="6f4e0-122">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="6f4e0-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="6f4e0-123">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="6f4e0-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="6f4e0-124">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="6f4e0-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="6f4e0-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="6f4e0-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="6f4e0-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="6f4e0-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="6f4e0-127">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="6f4e0-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="6f4e0-128">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="6f4e0-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="6f4e0-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="6f4e0-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```