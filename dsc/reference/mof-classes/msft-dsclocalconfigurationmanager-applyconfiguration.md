---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método ApplyConfiguration
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727182"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="c7a13-103">Método ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="c7a13-103">ApplyConfiguration method</span></span>

<span data-ttu-id="c7a13-104">Usa el agente de configuración para aplicar la configuración que está pendiente.</span><span class="sxs-lookup"><span data-stu-id="c7a13-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="c7a13-105">Si no hay ninguna configuración pendiente, este método vuelve a aplicar la configuración actual.</span><span class="sxs-lookup"><span data-stu-id="c7a13-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7a13-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c7a13-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c7a13-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c7a13-107">Parameters</span></span>

<span data-ttu-id="c7a13-108">*force* \[in\] Si este parámetro es **true**, se vuelve a aplicar la configuración actual, aunque haya una configuración pendiente.</span><span class="sxs-lookup"><span data-stu-id="c7a13-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="c7a13-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="c7a13-109">Return value</span></span>

<span data-ttu-id="c7a13-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="c7a13-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7a13-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="c7a13-111">Remarks</span></span>

<span data-ttu-id="c7a13-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="c7a13-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7a13-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7a13-113">Requirements</span></span>

<span data-ttu-id="c7a13-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c7a13-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c7a13-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c7a13-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c7a13-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="c7a13-116">See also</span></span>

[<span data-ttu-id="c7a13-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c7a13-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
