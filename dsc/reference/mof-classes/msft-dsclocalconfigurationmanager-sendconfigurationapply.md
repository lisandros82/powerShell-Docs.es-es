---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfigurationApply de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047503"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4c026-103">Método SendConfigurationApply de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4c026-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4c026-104">Envía el documento de configuración al nodo administrado y usa al agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="4c026-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c026-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4c026-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="4c026-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4c026-106">Parameters</span></span>

<span data-ttu-id="4c026-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="4c026-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="4c026-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="4c026-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c026-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4c026-109">Return value</span></span>

<span data-ttu-id="4c026-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="4c026-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c026-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4c026-111">Remarks</span></span>

<span data-ttu-id="4c026-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="4c026-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c026-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c026-113">Requirements</span></span>

<span data-ttu-id="4c026-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4c026-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4c026-115">Espacio de nombres {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4c026-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4c026-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="4c026-116">See also</span></span>

[<span data-ttu-id="4c026-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4c026-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)