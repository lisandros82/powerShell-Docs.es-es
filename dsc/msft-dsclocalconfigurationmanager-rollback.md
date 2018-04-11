---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Método RollBack de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c0a801c4037921e700e447d1434e246df0a63a4f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9e401-103">Método RollBack de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9e401-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9e401-104">Revierte la configuración a una versión anterior.</span><span class="sxs-lookup"><span data-stu-id="9e401-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="9e401-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9e401-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="9e401-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9e401-106">Parameters</span></span>
----------

<span data-ttu-id="9e401-107">*configurationNumber* \[in\] Especifica la configuración solicitada.</span><span class="sxs-lookup"><span data-stu-id="9e401-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="9e401-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="9e401-108">Return value</span></span>
------------

<span data-ttu-id="9e401-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="9e401-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e401-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9e401-110">Remarks</span></span>

<span data-ttu-id="9e401-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="9e401-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e401-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e401-112">Requirements</span></span>
------------
><span data-ttu-id="9e401-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9e401-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9e401-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9e401-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9e401-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="9e401-115">See also</span></span>


[<span data-ttu-id="9e401-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9e401-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)