---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079173"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6ee4c-103">Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6ee4c-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6ee4c-104">Usa el agente de configuración para aplicar la configuración que está pendiente.</span><span class="sxs-lookup"><span data-stu-id="6ee4c-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="6ee4c-105">Si no hay ninguna configuración pendiente, este método vuelve a aplicar la configuración actual.</span><span class="sxs-lookup"><span data-stu-id="6ee4c-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ee4c-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6ee4c-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="6ee4c-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6ee4c-107">Parameters</span></span>

<span data-ttu-id="6ee4c-108">*force* \[in\] Si este parámetro es **true**, se vuelve a aplicar la configuración actual, aunque haya una configuración pendiente.</span><span class="sxs-lookup"><span data-stu-id="6ee4c-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="6ee4c-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="6ee4c-109">Return value</span></span>

<span data-ttu-id="6ee4c-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="6ee4c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ee4c-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="6ee4c-111">Remarks</span></span>

<span data-ttu-id="6ee4c-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="6ee4c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6ee4c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ee4c-113">Requirements</span></span>

<span data-ttu-id="6ee4c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6ee4c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6ee4c-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ee4c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="6ee4c-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="6ee4c-116">See also</span></span>

[<span data-ttu-id="6ee4c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6ee4c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)