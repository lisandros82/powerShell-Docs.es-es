---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método StopConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: aaed29cb81e2079c4673b621b81c52e109aa7b48
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218882"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="135f3-103">Método StopConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="135f3-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="135f3-104">Detiene el cambio de configuración que está en curso.</span><span class="sxs-lookup"><span data-stu-id="135f3-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="135f3-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="135f3-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="135f3-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="135f3-106">Parameters</span></span>
----------

<span data-ttu-id="135f3-107">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="135f3-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="135f3-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="135f3-108">Return value</span></span>
------------

<span data-ttu-id="135f3-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="135f3-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="135f3-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="135f3-110">Remarks</span></span>

<span data-ttu-id="135f3-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="135f3-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="135f3-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="135f3-112">Requirements</span></span>
------------
><span data-ttu-id="135f3-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="135f3-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="135f3-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="135f3-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="135f3-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="135f3-115">See also</span></span>


[<span data-ttu-id="135f3-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="135f3-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)