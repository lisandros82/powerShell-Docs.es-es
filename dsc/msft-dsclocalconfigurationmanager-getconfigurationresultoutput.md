---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c929e-103">Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c929e-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c929e-104">Obtiene la salida del agente de configuración asociada con un trabajo específico.</span><span class="sxs-lookup"><span data-stu-id="c929e-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="c929e-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c929e-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="c929e-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c929e-106">Parameters</span></span>
----------

<span data-ttu-id="c929e-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c929e-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="c929e-108">Identificador del trabajo del que quiere obtener datos de salida.</span><span class="sxs-lookup"><span data-stu-id="c929e-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="c929e-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c929e-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="c929e-110">Especifica que la salida debe tener una continuación de un marcador anterior.</span><span class="sxs-lookup"><span data-stu-id="c929e-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="c929e-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="c929e-111">*output* \[out\]</span></span>  
<span data-ttu-id="c929e-112">Salida del trabajo especificado.</span><span class="sxs-lookup"><span data-stu-id="c929e-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="c929e-113">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="c929e-113">Return value</span></span>
------------

<span data-ttu-id="c929e-114">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="c929e-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c929e-115">Observaciones</span><span class="sxs-lookup"><span data-stu-id="c929e-115">Remarks</span></span>

<span data-ttu-id="c929e-116">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="c929e-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c929e-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c929e-117">Requirements</span></span>
------------
><span data-ttu-id="c929e-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c929e-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c929e-119">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c929e-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c929e-120">Vea también</span><span class="sxs-lookup"><span data-stu-id="c929e-120">See also</span></span>


[<span data-ttu-id="c929e-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c929e-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



