---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método SendConfigurationApplyAsync de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="65aa3-103">Método SendConfigurationApplyAsync de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="65aa3-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="65aa3-104">Envía el documento de configuración de forma asincrónica al nodo administrado y usa el agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="65aa3-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="65aa3-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="65aa3-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="65aa3-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="65aa3-106">Parameters</span></span>
----------

<span data-ttu-id="65aa3-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="65aa3-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="65aa3-108">Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="65aa3-108">The environment data for the configuration.</span></span>

<span data-ttu-id="65aa3-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="65aa3-109">*force* \[in\]</span></span>  
<span data-ttu-id="65aa3-110">**true** para forzar la configuración que se detendrá.</span><span class="sxs-lookup"><span data-stu-id="65aa3-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="65aa3-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="65aa3-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="65aa3-112">Identificador del trabajo al que se enviará la configuración.</span><span class="sxs-lookup"><span data-stu-id="65aa3-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="65aa3-113">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="65aa3-113">Return value</span></span>
------------

<span data-ttu-id="65aa3-114">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="65aa3-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="65aa3-115">Observaciones</span><span class="sxs-lookup"><span data-stu-id="65aa3-115">Remarks</span></span>

<span data-ttu-id="65aa3-116">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="65aa3-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="65aa3-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65aa3-117">Requirements</span></span>
------------
><span data-ttu-id="65aa3-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="65aa3-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="65aa3-119">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="65aa3-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="65aa3-120">Vea también</span><span class="sxs-lookup"><span data-stu-id="65aa3-120">See also</span></span>


[<span data-ttu-id="65aa3-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="65aa3-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



