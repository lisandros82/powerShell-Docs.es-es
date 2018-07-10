---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método StopConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893882"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="98a84-103">Método StopConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="98a84-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="98a84-104">Detiene el cambio de configuración que está en curso.</span><span class="sxs-lookup"><span data-stu-id="98a84-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="98a84-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="98a84-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="98a84-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="98a84-106">Parameters</span></span>

<span data-ttu-id="98a84-107">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="98a84-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="98a84-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="98a84-108">Return value</span></span>

<span data-ttu-id="98a84-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="98a84-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="98a84-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="98a84-110">Remarks</span></span>

<span data-ttu-id="98a84-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="98a84-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="98a84-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98a84-112">Requirements</span></span>

<span data-ttu-id="98a84-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="98a84-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="98a84-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="98a84-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="98a84-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="98a84-115">See also</span></span>

[<span data-ttu-id="98a84-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="98a84-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)