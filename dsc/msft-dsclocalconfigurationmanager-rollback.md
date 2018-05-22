---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método RollBack de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="24fec-103">Método RollBack de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="24fec-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="24fec-104">Revierte la configuración a una versión anterior.</span><span class="sxs-lookup"><span data-stu-id="24fec-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="24fec-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="24fec-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="24fec-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="24fec-106">Parameters</span></span>
----------

<span data-ttu-id="24fec-107">*configurationNumber* \[in\] Especifica la configuración solicitada.</span><span class="sxs-lookup"><span data-stu-id="24fec-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="24fec-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="24fec-108">Return value</span></span>
------------

<span data-ttu-id="24fec-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="24fec-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24fec-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="24fec-110">Remarks</span></span>

<span data-ttu-id="24fec-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="24fec-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="24fec-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24fec-112">Requirements</span></span>
------------
><span data-ttu-id="24fec-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="24fec-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="24fec-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="24fec-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="24fec-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="24fec-115">See also</span></span>


[<span data-ttu-id="24fec-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="24fec-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)