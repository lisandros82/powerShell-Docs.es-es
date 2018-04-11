---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9fe41fa806a6abff1d36dadd0c041a5cf0e78caf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3b090-103">Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3b090-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3b090-104">Habilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="3b090-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="3b090-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3b090-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="3b090-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3b090-106">Parameters</span></span>
----------

<span data-ttu-id="3b090-107">*BreakAll* \[in\] Establece un punto de interrupción en cada línea del script de recursos.</span><span class="sxs-lookup"><span data-stu-id="3b090-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="3b090-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="3b090-108">Return value</span></span>
------------

<span data-ttu-id="3b090-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="3b090-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3b090-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3b090-110">Remarks</span></span>

<span data-ttu-id="3b090-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="3b090-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3b090-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b090-112">Requirements</span></span>
------------
><span data-ttu-id="3b090-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3b090-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3b090-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3b090-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3b090-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="3b090-115">See also</span></span>


[<span data-ttu-id="3b090-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3b090-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)