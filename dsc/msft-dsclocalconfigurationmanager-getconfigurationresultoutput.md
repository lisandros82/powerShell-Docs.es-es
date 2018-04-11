---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f4c2ddaa37cdafeff1a442f3f1fa656788a1c6c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ab4e1-103">Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ab4e1-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ab4e1-104">Obtiene la salida del agente de configuración asociada con un trabajo específico.</span><span class="sxs-lookup"><span data-stu-id="ab4e1-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="ab4e1-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ab4e1-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="ab4e1-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ab4e1-106">Parameters</span></span>
----------

<span data-ttu-id="ab4e1-107">*jobId* \[in\] Identificador del trabajo del que quiere obtener datos de salida.</span><span class="sxs-lookup"><span data-stu-id="ab4e1-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="ab4e1-108">*resumeOutputBookmark* \[in\] Especifica que la salida debe ser una continuación de un marcador anterior.</span><span class="sxs-lookup"><span data-stu-id="ab4e1-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="ab4e1-109">*output* \[out\] Salida del trabajo especificado.</span><span class="sxs-lookup"><span data-stu-id="ab4e1-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="ab4e1-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="ab4e1-110">Return value</span></span>
------------

<span data-ttu-id="ab4e1-111">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="ab4e1-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab4e1-112">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ab4e1-112">Remarks</span></span>

<span data-ttu-id="ab4e1-113">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="ab4e1-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ab4e1-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab4e1-114">Requirements</span></span>
------------
><span data-ttu-id="ab4e1-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ab4e1-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ab4e1-116">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab4e1-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ab4e1-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="ab4e1-117">See also</span></span>


[<span data-ttu-id="ab4e1-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ab4e1-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)