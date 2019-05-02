---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método StopConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078256"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2dcb3-103">Método StopConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2dcb3-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2dcb3-104">Detiene el cambio de configuración que está en curso.</span><span class="sxs-lookup"><span data-stu-id="2dcb3-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="2dcb3-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2dcb3-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="2dcb3-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="2dcb3-106">Parameters</span></span>

<span data-ttu-id="2dcb3-107">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="2dcb3-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="2dcb3-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="2dcb3-108">Return value</span></span>

<span data-ttu-id="2dcb3-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="2dcb3-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2dcb3-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2dcb3-110">Remarks</span></span>

<span data-ttu-id="2dcb3-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="2dcb3-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2dcb3-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2dcb3-112">Requirements</span></span>

<span data-ttu-id="2dcb3-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2dcb3-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2dcb3-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2dcb3-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2dcb3-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="2dcb3-115">See also</span></span>

[<span data-ttu-id="2dcb3-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2dcb3-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)