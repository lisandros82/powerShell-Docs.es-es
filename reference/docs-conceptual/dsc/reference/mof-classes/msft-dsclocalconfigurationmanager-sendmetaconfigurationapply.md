---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendMetaConfigurationApply
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954882"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="5c336-103">Método SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="5c336-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="5c336-104">Establece la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="5c336-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="5c336-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5c336-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5c336-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5c336-106">Parameters</span></span>

<span data-ttu-id="5c336-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="5c336-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="5c336-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="5c336-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="5c336-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="5c336-109">Return value</span></span>

<span data-ttu-id="5c336-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="5c336-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c336-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5c336-111">Remarks</span></span>

<span data-ttu-id="5c336-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="5c336-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5c336-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c336-113">Requirements</span></span>

<span data-ttu-id="5c336-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5c336-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5c336-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5c336-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5c336-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="5c336-116">See also</span></span>

[<span data-ttu-id="5c336-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5c336-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
