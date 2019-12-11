---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método RollBack
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954942"
---
# <a name="rollback-method"></a><span data-ttu-id="8f8bf-103">Método RollBack</span><span class="sxs-lookup"><span data-stu-id="8f8bf-103">RollBack method</span></span>

<span data-ttu-id="8f8bf-104">Revierte la configuración a una versión anterior.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="8f8bf-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8f8bf-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="8f8bf-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="8f8bf-106">Parameters</span></span>

<span data-ttu-id="8f8bf-107">*configurationNumber* \[in\] Especifica la configuración solicitada.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="8f8bf-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="8f8bf-108">Return value</span></span>

<span data-ttu-id="8f8bf-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f8bf-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8f8bf-110">Remarks</span></span>

<span data-ttu-id="8f8bf-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8f8bf-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f8bf-112">Requirements</span></span>

<span data-ttu-id="8f8bf-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8f8bf-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8f8bf-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8f8bf-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8f8bf-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="8f8bf-115">See also</span></span>

[<span data-ttu-id="8f8bf-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8f8bf-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
