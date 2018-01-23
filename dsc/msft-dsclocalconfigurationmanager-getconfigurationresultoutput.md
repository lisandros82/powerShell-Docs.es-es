---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: f6106bb28dc20004b5bbb6df2d8e719cf0c453f0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4bfae-103">Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4bfae-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4bfae-104">Obtiene la salida del agente de configuración asociada con un trabajo específico.</span><span class="sxs-lookup"><span data-stu-id="4bfae-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="4bfae-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4bfae-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="4bfae-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4bfae-106">Parameters</span></span>
----------

<span data-ttu-id="4bfae-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4bfae-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="4bfae-108">Identificador del trabajo del que quiere obtener datos de salida.</span><span class="sxs-lookup"><span data-stu-id="4bfae-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="4bfae-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4bfae-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="4bfae-110">Especifica que la salida debe tener una continuación de un marcador anterior.</span><span class="sxs-lookup"><span data-stu-id="4bfae-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="4bfae-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="4bfae-111">*output* \[out\]</span></span>  
<span data-ttu-id="4bfae-112">Salida del trabajo especificado.</span><span class="sxs-lookup"><span data-stu-id="4bfae-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="4bfae-113">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4bfae-113">Return value</span></span>
------------

<span data-ttu-id="4bfae-114">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="4bfae-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bfae-115">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4bfae-115">Remarks</span></span>

<span data-ttu-id="4bfae-116">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="4bfae-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4bfae-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4bfae-117">Requirements</span></span>
------------
><span data-ttu-id="4bfae-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4bfae-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4bfae-119">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4bfae-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4bfae-120">Vea también</span><span class="sxs-lookup"><span data-stu-id="4bfae-120">See also</span></span>


[<span data-ttu-id="4bfae-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4bfae-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



