---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método StopConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682216"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2f920-103">Método StopConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2f920-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2f920-104">Detiene el cambio de configuración que está en curso.</span><span class="sxs-lookup"><span data-stu-id="2f920-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="2f920-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2f920-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="2f920-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="2f920-106">Parameters</span></span>

<span data-ttu-id="2f920-107">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="2f920-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="2f920-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="2f920-108">Return value</span></span>

<span data-ttu-id="2f920-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="2f920-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f920-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2f920-110">Remarks</span></span>

<span data-ttu-id="2f920-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="2f920-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f920-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f920-112">Requirements</span></span>

<span data-ttu-id="2f920-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2f920-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2f920-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2f920-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2f920-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="2f920-115">See also</span></span>

[<span data-ttu-id="2f920-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2f920-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)