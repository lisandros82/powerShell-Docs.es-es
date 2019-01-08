---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendMetaConfigurationApply de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048076"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7c8f0-103">Método SendMetaConfigurationApply de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7c8f0-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7c8f0-104">Establece la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="7c8f0-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="7c8f0-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7c8f0-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="7c8f0-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7c8f0-106">Parameters</span></span>

<span data-ttu-id="7c8f0-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="7c8f0-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="7c8f0-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="7c8f0-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="7c8f0-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="7c8f0-109">Return value</span></span>

<span data-ttu-id="7c8f0-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="7c8f0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c8f0-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7c8f0-111">Remarks</span></span>

<span data-ttu-id="7c8f0-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="7c8f0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7c8f0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c8f0-113">Requirements</span></span>

<span data-ttu-id="7c8f0-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7c8f0-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7c8f0-115">Espacio de nombres {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7c8f0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7c8f0-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="7c8f0-116">See also</span></span>

[<span data-ttu-id="7c8f0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7c8f0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)