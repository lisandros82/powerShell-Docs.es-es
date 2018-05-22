---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
contributor: vaibch
title: Error de cmdlets de Network Switch Manager
ms.openlocfilehash: 197a25411a82e5d256a9420706535d5411991f1b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
<span data-ttu-id="9cead-103">Los cmdlets de Network Switch Manager se pueden usar para administrar modificadores de red a través de WSMAN.</span><span class="sxs-lookup"><span data-stu-id="9cead-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="9cead-104">Algunos cmdlets de este módulo pueden aceptar valores de canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="9cead-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="9cead-105">En la versión preliminar de WMF 5.1, los cmdlets que pueden aceptar el valor de la canalización no pueden ejecutarse si los valores no pasan a través de canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="9cead-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="9cead-106">Si no se usa el parámetro "InputObject", el cmdlet debería continuar ejecutándose sin errores.</span><span class="sxs-lookup"><span data-stu-id="9cead-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="9cead-107">Esta es la lista de cmdlets afectados; es decir, estos cmdlets pueden aceptar el valor del parámetro "InputObject" de la canalización.</span><span class="sxs-lookup"><span data-stu-id="9cead-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="9cead-108">Si no se pasa este valor de la canalización, se producirá un error en la ejecución del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cead-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="9cead-109">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="9cead-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="9cead-110">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="9cead-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="9cead-111">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="9cead-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="9cead-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="9cead-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="9cead-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="9cead-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="9cead-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="9cead-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="9cead-115">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="9cead-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="9cead-116">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="9cead-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="9cead-117">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="9cead-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="9cead-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="9cead-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="9cead-119">Solución</span><span class="sxs-lookup"><span data-stu-id="9cead-119">Resolution</span></span>
<span data-ttu-id="9cead-120">Los cmdlets funcionan bien cuando el valor del parámetro InputObject se pasa a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="9cead-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="9cead-121">Algunos ejemplos que funcionan con los cmdlets anteriores son:</span><span class="sxs-lookup"><span data-stu-id="9cead-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="9cead-122">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="9cead-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="9cead-123">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="9cead-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="9cead-124">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="9cead-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="9cead-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="9cead-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="9cead-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="9cead-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="9cead-127">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="9cead-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="9cead-128">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="9cead-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="9cead-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="9cead-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
