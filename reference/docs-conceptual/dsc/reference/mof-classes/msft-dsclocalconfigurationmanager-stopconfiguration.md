---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método StopConfiguration
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953362"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="8a752-103">Método StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a752-103">StopConfiguration method</span></span>

<span data-ttu-id="8a752-104">Detiene el cambio de configuración que está en curso.</span><span class="sxs-lookup"><span data-stu-id="8a752-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a752-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8a752-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="8a752-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="8a752-106">Parameters</span></span>

<span data-ttu-id="8a752-107">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="8a752-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="8a752-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="8a752-108">Return value</span></span>

<span data-ttu-id="8a752-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="8a752-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a752-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8a752-110">Remarks</span></span>

<span data-ttu-id="8a752-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="8a752-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8a752-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a752-112">Requirements</span></span>

<span data-ttu-id="8a752-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8a752-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8a752-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a752-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8a752-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="8a752-115">See also</span></span>

[<span data-ttu-id="8a752-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8a752-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
