---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método SendConfigurationApplyAsync de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e680bfd1c5b39d364c90cf5ef6b43d0a568af23a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="efd8e-103">Método SendConfigurationApplyAsync de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="efd8e-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="efd8e-104">Envía el documento de configuración de forma asincrónica al nodo administrado y usa el agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="efd8e-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="efd8e-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="efd8e-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="efd8e-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="efd8e-106">Parameters</span></span>
----------

<span data-ttu-id="efd8e-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="efd8e-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="efd8e-108">Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="efd8e-108">The environment data for the configuration.</span></span>

<span data-ttu-id="efd8e-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="efd8e-109">*force* \[in\]</span></span>  
<span data-ttu-id="efd8e-110">**true** para forzar la configuración que se detendrá.</span><span class="sxs-lookup"><span data-stu-id="efd8e-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="efd8e-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="efd8e-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="efd8e-112">Identificador del trabajo al que se enviará la configuración.</span><span class="sxs-lookup"><span data-stu-id="efd8e-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="efd8e-113">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="efd8e-113">Return value</span></span>
------------

<span data-ttu-id="efd8e-114">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="efd8e-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="efd8e-115">Observaciones</span><span class="sxs-lookup"><span data-stu-id="efd8e-115">Remarks</span></span>

<span data-ttu-id="efd8e-116">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="efd8e-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="efd8e-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="efd8e-117">Requirements</span></span>
------------
><span data-ttu-id="efd8e-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="efd8e-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="efd8e-119">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="efd8e-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="efd8e-120">Vea también</span><span class="sxs-lookup"><span data-stu-id="efd8e-120">See also</span></span>


[<span data-ttu-id="efd8e-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="efd8e-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



