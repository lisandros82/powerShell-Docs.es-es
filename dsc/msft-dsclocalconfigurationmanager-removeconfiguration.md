---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método RemoveConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e08c4-103">Método RemoveConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e08c4-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e08c4-104">Quita los archivos de configuración.</span><span class="sxs-lookup"><span data-stu-id="e08c4-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="e08c4-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e08c4-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="e08c4-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e08c4-106">Parameters</span></span>
----------

<span data-ttu-id="e08c4-107">*Stage* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e08c4-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="e08c4-108">Especifica qué documento de configuración quiere quitar.</span><span class="sxs-lookup"><span data-stu-id="e08c4-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="e08c4-109">Los valores siguientes son válidos:</span><span class="sxs-lookup"><span data-stu-id="e08c4-109">The following values are valid:</span></span>

|<span data-ttu-id="e08c4-110">Value</span><span class="sxs-lookup"><span data-stu-id="e08c4-110">Value</span></span> |<span data-ttu-id="e08c4-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="e08c4-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="e08c4-112">**1**</span><span class="sxs-lookup"><span data-stu-id="e08c4-112">**1**</span></span> | <span data-ttu-id="e08c4-113">Documento de configuración **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="e08c4-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="e08c4-114">**2**</span><span class="sxs-lookup"><span data-stu-id="e08c4-114">**2**</span></span> | <span data-ttu-id="e08c4-115">Documento de configuración **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="e08c4-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="e08c4-116">**4**</span><span class="sxs-lookup"><span data-stu-id="e08c4-116">**4**</span></span> | <span data-ttu-id="e08c4-117">Documento de configuración **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="e08c4-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="e08c4-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e08c4-118">*Force* \[in\]</span></span>  
<span data-ttu-id="e08c4-119">**true** para forzar la eliminación de la configuración.</span><span class="sxs-lookup"><span data-stu-id="e08c4-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="e08c4-120">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="e08c4-120">Return value</span></span>
------------

<span data-ttu-id="e08c4-121">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="e08c4-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e08c4-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e08c4-122">Remarks</span></span>

<span data-ttu-id="e08c4-123">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="e08c4-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e08c4-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e08c4-124">Requirements</span></span>
------------
><span data-ttu-id="e08c4-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e08c4-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e08c4-126">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e08c4-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e08c4-127">Vea también</span><span class="sxs-lookup"><span data-stu-id="e08c4-127">See also</span></span>


[<span data-ttu-id="e08c4-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e08c4-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



