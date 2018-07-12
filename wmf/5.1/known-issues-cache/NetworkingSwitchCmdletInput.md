---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
contributor: vaibch
title: Error de cmdlets de Network Switch Manager
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893161"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="791d2-103">Error de cmdlets de Network Switch Manager</span><span class="sxs-lookup"><span data-stu-id="791d2-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="791d2-104">Los cmdlets de Network Switch Manager se pueden usar para administrar modificadores de red a través de WSMAN.</span><span class="sxs-lookup"><span data-stu-id="791d2-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="791d2-105">Algunos cmdlets de este módulo pueden aceptar valores de canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="791d2-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="791d2-106">En la versión preliminar de WMF 5.1, los cmdlets que pueden aceptar el valor de la canalización no pueden ejecutarse si los valores no pasan a través de canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="791d2-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="791d2-107">Si no se usa el parámetro "InputObject", el cmdlet debería continuar ejecutándose sin errores.</span><span class="sxs-lookup"><span data-stu-id="791d2-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="791d2-108">Esta es la lista de cmdlets afectados; es decir, estos cmdlets pueden aceptar el valor del parámetro "InputObject" de la canalización.</span><span class="sxs-lookup"><span data-stu-id="791d2-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="791d2-109">Si no se pasa este valor de la canalización, se producirá un error en la ejecución del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="791d2-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="791d2-110">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="791d2-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="791d2-111">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="791d2-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="791d2-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="791d2-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="791d2-113">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="791d2-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="791d2-114">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="791d2-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="791d2-115">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="791d2-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="791d2-116">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="791d2-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="791d2-117">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="791d2-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="791d2-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="791d2-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="791d2-119">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="791d2-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="791d2-120">Solución</span><span class="sxs-lookup"><span data-stu-id="791d2-120">Resolution</span></span>

<span data-ttu-id="791d2-121">Los cmdlets funcionan bien cuando el valor del parámetro InputObject se pasa a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="791d2-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="791d2-122">Algunos ejemplos que funcionan con los cmdlets anteriores son:</span><span class="sxs-lookup"><span data-stu-id="791d2-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```