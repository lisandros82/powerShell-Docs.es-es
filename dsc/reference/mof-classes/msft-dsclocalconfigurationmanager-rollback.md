---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método RollBack
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727031"
---
# <a name="rollback-method"></a><span data-ttu-id="5cf0a-103">Método RollBack</span><span class="sxs-lookup"><span data-stu-id="5cf0a-103">RollBack method</span></span>

<span data-ttu-id="5cf0a-104">Revierte la configuración a una versión anterior.</span><span class="sxs-lookup"><span data-stu-id="5cf0a-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="5cf0a-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5cf0a-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="5cf0a-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5cf0a-106">Parameters</span></span>

<span data-ttu-id="5cf0a-107">*configurationNumber* \[in\] Especifica la configuración solicitada.</span><span class="sxs-lookup"><span data-stu-id="5cf0a-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="5cf0a-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="5cf0a-108">Return value</span></span>

<span data-ttu-id="5cf0a-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="5cf0a-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5cf0a-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5cf0a-110">Remarks</span></span>

<span data-ttu-id="5cf0a-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="5cf0a-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5cf0a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5cf0a-112">Requirements</span></span>

<span data-ttu-id="5cf0a-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5cf0a-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5cf0a-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5cf0a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5cf0a-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="5cf0a-115">See also</span></span>

[<span data-ttu-id="5cf0a-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5cf0a-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
