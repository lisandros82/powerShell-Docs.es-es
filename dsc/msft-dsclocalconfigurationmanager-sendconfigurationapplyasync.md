---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfigurationApplyAsync de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: acd8f380f1c49eb008563398c2c3de3fce5477f9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186684"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fd393-103">Método SendConfigurationApplyAsync de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fd393-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fd393-104">Envía el documento de configuración de forma asincrónica al nodo administrado y usa el agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="fd393-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="fd393-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fd393-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="fd393-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="fd393-106">Parameters</span></span>
----------

<span data-ttu-id="fd393-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="fd393-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="fd393-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="fd393-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="fd393-109">*jobId* \[in\] Identificador del trabajo al que se va a enviar la configuración.</span><span class="sxs-lookup"><span data-stu-id="fd393-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="fd393-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="fd393-110">Return value</span></span>
------------

<span data-ttu-id="fd393-111">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="fd393-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd393-112">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fd393-112">Remarks</span></span>

<span data-ttu-id="fd393-113">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="fd393-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fd393-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd393-114">Requirements</span></span>
------------
><span data-ttu-id="fd393-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fd393-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="fd393-116">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fd393-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="fd393-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="fd393-117">See also</span></span>


[<span data-ttu-id="fd393-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fd393-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)