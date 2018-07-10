---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfigurationApplyAsync de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893905"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="da6e0-103">Método SendConfigurationApplyAsync de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="da6e0-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="da6e0-104">Envía el documento de configuración de forma asincrónica al nodo administrado y usa el agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="da6e0-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="da6e0-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="da6e0-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="da6e0-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="da6e0-106">Parameters</span></span>

<span data-ttu-id="da6e0-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="da6e0-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="da6e0-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="da6e0-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="da6e0-109">*jobId* \[in\] Identificador del trabajo al que se va a enviar la configuración.</span><span class="sxs-lookup"><span data-stu-id="da6e0-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="da6e0-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="da6e0-110">Return value</span></span>

<span data-ttu-id="da6e0-111">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="da6e0-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="da6e0-112">Observaciones</span><span class="sxs-lookup"><span data-stu-id="da6e0-112">Remarks</span></span>

<span data-ttu-id="da6e0-113">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="da6e0-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="da6e0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da6e0-114">Requirements</span></span>

<span data-ttu-id="da6e0-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="da6e0-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="da6e0-116">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="da6e0-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="da6e0-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="da6e0-117">See also</span></span>

[<span data-ttu-id="da6e0-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="da6e0-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)