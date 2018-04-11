---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2844e354e0d054b13b92267ce314536d88a1c33e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bdce4-103">Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bdce4-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bdce4-104">Usa el agente de configuración para aplicar la configuración que está pendiente.</span><span class="sxs-lookup"><span data-stu-id="bdce4-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="bdce4-105">Si no hay ninguna configuración pendiente, este método vuelve a aplicar la configuración actual.</span><span class="sxs-lookup"><span data-stu-id="bdce4-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="bdce4-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="bdce4-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="bdce4-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdce4-107">Parameters</span></span>
----------

<span data-ttu-id="bdce4-108">*force* \[in\] Si este parámetro es **true**, se vuelve a aplicar la configuración actual, aunque haya una configuración pendiente.</span><span class="sxs-lookup"><span data-stu-id="bdce4-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="bdce4-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="bdce4-109">Return value</span></span>
------------

<span data-ttu-id="bdce4-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="bdce4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bdce4-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="bdce4-111">Remarks</span></span>

<span data-ttu-id="bdce4-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="bdce4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bdce4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bdce4-113">Requirements</span></span>
------------
><span data-ttu-id="bdce4-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bdce4-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bdce4-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bdce4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bdce4-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="bdce4-116">See also</span></span>


[<span data-ttu-id="bdce4-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bdce4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)