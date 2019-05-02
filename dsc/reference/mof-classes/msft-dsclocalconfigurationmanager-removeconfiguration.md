---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método RemoveConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078697"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="aeb88-103">Método RemoveConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="aeb88-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="aeb88-104">Quita los archivos de configuración.</span><span class="sxs-lookup"><span data-stu-id="aeb88-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="aeb88-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="aeb88-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="aeb88-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="aeb88-106">Parameters</span></span>

<span data-ttu-id="aeb88-107">*Stage* \[in\] Especifica qué documento de configuración quiere quitar.</span><span class="sxs-lookup"><span data-stu-id="aeb88-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="aeb88-108">Los valores siguientes son válidos:</span><span class="sxs-lookup"><span data-stu-id="aeb88-108">The following values are valid:</span></span>

|<span data-ttu-id="aeb88-109">Value</span><span class="sxs-lookup"><span data-stu-id="aeb88-109">Value</span></span> |<span data-ttu-id="aeb88-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="aeb88-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="aeb88-111">**1**</span><span class="sxs-lookup"><span data-stu-id="aeb88-111">**1**</span></span> | <span data-ttu-id="aeb88-112">Documento de configuración **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="aeb88-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="aeb88-113">**2**</span><span class="sxs-lookup"><span data-stu-id="aeb88-113">**2**</span></span> | <span data-ttu-id="aeb88-114">Documento de configuración **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="aeb88-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="aeb88-115">**4**</span><span class="sxs-lookup"><span data-stu-id="aeb88-115">**4**</span></span> | <span data-ttu-id="aeb88-116">Documento de configuración **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="aeb88-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="aeb88-117">*Force* \[in\] **true** para forzar la eliminación de la configuración.</span><span class="sxs-lookup"><span data-stu-id="aeb88-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="aeb88-118">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="aeb88-118">Return value</span></span>

<span data-ttu-id="aeb88-119">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="aeb88-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="aeb88-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="aeb88-120">Remarks</span></span>

<span data-ttu-id="aeb88-121">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="aeb88-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="aeb88-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aeb88-122">Requirements</span></span>

<span data-ttu-id="aeb88-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="aeb88-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="aeb88-124">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="aeb88-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="aeb88-125">Vea también</span><span class="sxs-lookup"><span data-stu-id="aeb88-125">See also</span></span>

[<span data-ttu-id="aeb88-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="aeb88-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)