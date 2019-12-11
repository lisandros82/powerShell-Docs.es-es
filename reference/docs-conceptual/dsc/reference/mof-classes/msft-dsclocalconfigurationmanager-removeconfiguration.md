---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método RemoveConfiguration
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953402"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="0d926-103">Método RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="0d926-103">RemoveConfiguration method</span></span>

<span data-ttu-id="0d926-104">Quita los archivos de configuración.</span><span class="sxs-lookup"><span data-stu-id="0d926-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d926-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0d926-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="0d926-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d926-106">Parameters</span></span>

<span data-ttu-id="0d926-107">*Stage* \[in\] Especifica qué documento de configuración quiere quitar.</span><span class="sxs-lookup"><span data-stu-id="0d926-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="0d926-108">Los valores siguientes son válidos:</span><span class="sxs-lookup"><span data-stu-id="0d926-108">The following values are valid:</span></span>

|<span data-ttu-id="0d926-109">Value</span><span class="sxs-lookup"><span data-stu-id="0d926-109">Value</span></span> |<span data-ttu-id="0d926-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d926-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="0d926-111">**1**</span><span class="sxs-lookup"><span data-stu-id="0d926-111">**1**</span></span> | <span data-ttu-id="0d926-112">Documento de configuración **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="0d926-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="0d926-113">**2**</span><span class="sxs-lookup"><span data-stu-id="0d926-113">**2**</span></span> | <span data-ttu-id="0d926-114">Documento de configuración **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="0d926-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="0d926-115">**4**</span><span class="sxs-lookup"><span data-stu-id="0d926-115">**4**</span></span> | <span data-ttu-id="0d926-116">Documento de configuración **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="0d926-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="0d926-117">*Force* \[in\] **true** para forzar la eliminación de la configuración.</span><span class="sxs-lookup"><span data-stu-id="0d926-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d926-118">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0d926-118">Return value</span></span>

<span data-ttu-id="0d926-119">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="0d926-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d926-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0d926-120">Remarks</span></span>

<span data-ttu-id="0d926-121">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="0d926-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d926-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d926-122">Requirements</span></span>

<span data-ttu-id="0d926-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0d926-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0d926-124">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0d926-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0d926-125">Vea también</span><span class="sxs-lookup"><span data-stu-id="0d926-125">See also</span></span>

[<span data-ttu-id="0d926-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0d926-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
