---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfigurationApply de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680537"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="24916-103">Método SendConfigurationApply de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="24916-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="24916-104">Envía el documento de configuración al nodo administrado y usa al agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="24916-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="24916-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="24916-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="24916-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="24916-106">Parameters</span></span>

<span data-ttu-id="24916-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="24916-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="24916-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="24916-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="24916-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="24916-109">Return value</span></span>

<span data-ttu-id="24916-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="24916-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24916-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="24916-111">Remarks</span></span>

<span data-ttu-id="24916-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="24916-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="24916-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24916-113">Requirements</span></span>

<span data-ttu-id="24916-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="24916-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="24916-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="24916-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="24916-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="24916-116">See also</span></span>

[<span data-ttu-id="24916-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="24916-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)