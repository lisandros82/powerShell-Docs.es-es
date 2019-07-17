---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método StopConfiguration
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726994"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="78235-103">Método StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="78235-103">StopConfiguration method</span></span>

<span data-ttu-id="78235-104">Detiene el cambio de configuración que está en curso.</span><span class="sxs-lookup"><span data-stu-id="78235-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="78235-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="78235-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="78235-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="78235-106">Parameters</span></span>

<span data-ttu-id="78235-107">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="78235-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="78235-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="78235-108">Return value</span></span>

<span data-ttu-id="78235-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="78235-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="78235-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="78235-110">Remarks</span></span>

<span data-ttu-id="78235-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="78235-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="78235-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78235-112">Requirements</span></span>

<span data-ttu-id="78235-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="78235-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="78235-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="78235-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="78235-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="78235-115">See also</span></span>

[<span data-ttu-id="78235-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="78235-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
