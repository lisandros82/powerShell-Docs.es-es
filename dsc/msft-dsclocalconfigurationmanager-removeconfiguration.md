---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método RemoveConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c68d17d38336dec08e078366ea5f2071fcf7c5a8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bb607-103">Método RemoveConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bb607-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bb607-104">Quita los archivos de configuración.</span><span class="sxs-lookup"><span data-stu-id="bb607-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="bb607-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="bb607-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="bb607-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bb607-106">Parameters</span></span>
----------

<span data-ttu-id="bb607-107">*Stage* \[in\] Especifica qué documento de configuración quiere quitar.</span><span class="sxs-lookup"><span data-stu-id="bb607-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="bb607-108">Los valores siguientes son válidos:</span><span class="sxs-lookup"><span data-stu-id="bb607-108">The following values are valid:</span></span>

|<span data-ttu-id="bb607-109">Value</span><span class="sxs-lookup"><span data-stu-id="bb607-109">Value</span></span> |<span data-ttu-id="bb607-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="bb607-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="bb607-111">**1**</span><span class="sxs-lookup"><span data-stu-id="bb607-111">**1**</span></span> | <span data-ttu-id="bb607-112">Documento de configuración **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="bb607-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="bb607-113">**2**</span><span class="sxs-lookup"><span data-stu-id="bb607-113">**2**</span></span> | <span data-ttu-id="bb607-114">Documento de configuración **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="bb607-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="bb607-115">**4**</span><span class="sxs-lookup"><span data-stu-id="bb607-115">**4**</span></span> | <span data-ttu-id="bb607-116">Documento de configuración **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="bb607-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="bb607-117">*Force* \[in\] **true** para forzar la eliminación de la configuración.</span><span class="sxs-lookup"><span data-stu-id="bb607-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="bb607-118">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="bb607-118">Return value</span></span>
------------

<span data-ttu-id="bb607-119">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="bb607-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb607-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="bb607-120">Remarks</span></span>

<span data-ttu-id="bb607-121">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="bb607-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb607-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb607-122">Requirements</span></span>
------------
><span data-ttu-id="bb607-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bb607-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bb607-124">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb607-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bb607-125">Vea también</span><span class="sxs-lookup"><span data-stu-id="bb607-125">See also</span></span>


[<span data-ttu-id="bb607-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bb607-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)