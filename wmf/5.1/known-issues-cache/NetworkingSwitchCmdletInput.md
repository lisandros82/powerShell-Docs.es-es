---
title: Error de cmdlets de Network Switch Manager
contributor: vaibch
ms.openlocfilehash: e32e31762b665a7e2c6f6938fe494cb6127d4264
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
<span data-ttu-id="6cb3e-102">Los cmdlets de Network Switch Manager se pueden usar para administrar modificadores de red a través de WSMAN.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-102">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span> <span data-ttu-id="6cb3e-103">Algunos cmdlets de este módulo pueden aceptar valores de canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-103">A few cmdlets of this module are capable of accepting values from pipelines.</span></span> <span data-ttu-id="6cb3e-104">En la versión preliminar de WMF 5.1, los cmdlets que pueden aceptar el valor de la canalización no pueden ejecutarse si los valores no pasan a través de canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-104">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="6cb3e-105">Si no se usa el parámetro "InputObject", el cmdlet debería continuar ejecutándose sin errores.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-105">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="6cb3e-106">Esta es la lista de cmdlets afectados; es decir, estos cmdlets pueden aceptar el valor del parámetro "InputObject" de la canalización.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-106">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span> <span data-ttu-id="6cb3e-107">Si no se pasa este valor de la canalización, se producirá un error en la ejecución del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-107">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="6cb3e-108">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="6cb3e-108">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="6cb3e-109">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="6cb3e-109">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="6cb3e-110">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="6cb3e-110">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="6cb3e-111">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="6cb3e-111">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="6cb3e-112">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="6cb3e-112">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="6cb3e-113">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="6cb3e-113">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="6cb3e-114">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="6cb3e-114">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="6cb3e-115">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="6cb3e-115">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="6cb3e-116">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="6cb3e-116">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="6cb3e-117">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="6cb3e-117">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="6cb3e-118">Solución</span><span class="sxs-lookup"><span data-stu-id="6cb3e-118">Resolution</span></span>
<span data-ttu-id="6cb3e-119">Los cmdlets funcionan bien cuando el valor del parámetro InputObject se pasa a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-119">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="6cb3e-120">Algunos ejemplos que funcionan con los cmdlets anteriores son:</span><span class="sxs-lookup"><span data-stu-id="6cb3e-120">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="6cb3e-121">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="6cb3e-121">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```
- <span data-ttu-id="6cb3e-122">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="6cb3e-122">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="6cb3e-123">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="6cb3e-123">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="6cb3e-124">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="6cb3e-124">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="6cb3e-125">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="6cb3e-125">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="6cb3e-126">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="6cb3e-126">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="6cb3e-127">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="6cb3e-127">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="6cb3e-128">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="6cb3e-128">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
