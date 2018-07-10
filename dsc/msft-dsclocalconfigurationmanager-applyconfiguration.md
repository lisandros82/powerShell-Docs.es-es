---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892629"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5f12c-103">Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5f12c-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5f12c-104">Usa el agente de configuración para aplicar la configuración que está pendiente.</span><span class="sxs-lookup"><span data-stu-id="5f12c-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="5f12c-105">Si no hay ninguna configuración pendiente, este método vuelve a aplicar la configuración actual.</span><span class="sxs-lookup"><span data-stu-id="5f12c-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f12c-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5f12c-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5f12c-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5f12c-107">Parameters</span></span>

<span data-ttu-id="5f12c-108">*force* \[in\] Si este parámetro es **true**, se vuelve a aplicar la configuración actual, aunque haya una configuración pendiente.</span><span class="sxs-lookup"><span data-stu-id="5f12c-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="5f12c-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="5f12c-109">Return value</span></span>

<span data-ttu-id="5f12c-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="5f12c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5f12c-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5f12c-111">Remarks</span></span>

<span data-ttu-id="5f12c-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="5f12c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5f12c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f12c-113">Requirements</span></span>

<span data-ttu-id="5f12c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5f12c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5f12c-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f12c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5f12c-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="5f12c-116">See also</span></span>

[<span data-ttu-id="5f12c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5f12c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)