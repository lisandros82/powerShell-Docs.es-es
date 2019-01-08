---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048016"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d2348-103">Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d2348-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d2348-104">Habilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="d2348-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2348-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d2348-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="d2348-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d2348-106">Parameters</span></span>

<span data-ttu-id="d2348-107">*BreakAll* \[in\] Establece un punto de interrupción en cada línea del script de recursos.</span><span class="sxs-lookup"><span data-stu-id="d2348-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="d2348-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="d2348-108">Return value</span></span>

<span data-ttu-id="d2348-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="d2348-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2348-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d2348-110">Remarks</span></span>

<span data-ttu-id="d2348-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="d2348-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2348-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2348-112">Requirements</span></span>

<span data-ttu-id="d2348-113">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d2348-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d2348-114">Espacio de nombres {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2348-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d2348-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="d2348-115">See also</span></span>

[<span data-ttu-id="d2348-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d2348-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)