---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfigurationApply
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727004"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="38d1b-103">Método SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="38d1b-103">SendConfigurationApply method</span></span>

<span data-ttu-id="38d1b-104">Envía el documento de configuración al nodo administrado y usa al agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="38d1b-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="38d1b-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="38d1b-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="38d1b-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="38d1b-106">Parameters</span></span>

<span data-ttu-id="38d1b-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="38d1b-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="38d1b-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="38d1b-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="38d1b-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="38d1b-109">Return value</span></span>

<span data-ttu-id="38d1b-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="38d1b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="38d1b-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="38d1b-111">Remarks</span></span>

<span data-ttu-id="38d1b-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="38d1b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="38d1b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38d1b-113">Requirements</span></span>

<span data-ttu-id="38d1b-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="38d1b-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="38d1b-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="38d1b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="38d1b-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="38d1b-116">See also</span></span>

[<span data-ttu-id="38d1b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="38d1b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
