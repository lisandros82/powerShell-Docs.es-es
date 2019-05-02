---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método RollBack de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078374"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="33169-103">Método RollBack de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="33169-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="33169-104">Revierte la configuración a una versión anterior.</span><span class="sxs-lookup"><span data-stu-id="33169-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="33169-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="33169-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="33169-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="33169-106">Parameters</span></span>

<span data-ttu-id="33169-107">*configurationNumber* \[in\] Especifica la configuración solicitada.</span><span class="sxs-lookup"><span data-stu-id="33169-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="33169-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="33169-108">Return value</span></span>

<span data-ttu-id="33169-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="33169-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="33169-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="33169-110">Remarks</span></span>

<span data-ttu-id="33169-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="33169-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="33169-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="33169-112">Requirements</span></span>

<span data-ttu-id="33169-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="33169-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="33169-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="33169-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="33169-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="33169-115">See also</span></span>

[<span data-ttu-id="33169-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="33169-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)