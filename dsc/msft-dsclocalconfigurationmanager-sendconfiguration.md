---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 07ae48dd456e68be4ad0b09127ba9801359fd101
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1d778-103">Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1d778-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1d778-104">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="1d778-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="1d778-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1d778-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="1d778-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1d778-106">Parameters</span></span>
----------

<span data-ttu-id="1d778-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="1d778-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="1d778-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="1d778-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="1d778-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1d778-109">Return value</span></span>
------------

<span data-ttu-id="1d778-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="1d778-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d778-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1d778-111">Remarks</span></span>

<span data-ttu-id="1d778-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="1d778-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1d778-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d778-113">Requirements</span></span>
------------
><span data-ttu-id="1d778-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1d778-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1d778-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1d778-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1d778-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="1d778-116">See also</span></span>


[<span data-ttu-id="1d778-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1d778-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)