---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendMetaConfigurationApply de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682445"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b5050-103">Método SendMetaConfigurationApply de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b5050-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b5050-104">Establece la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="b5050-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5050-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b5050-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="b5050-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b5050-106">Parameters</span></span>

<span data-ttu-id="b5050-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="b5050-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="b5050-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="b5050-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="b5050-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="b5050-109">Return value</span></span>

<span data-ttu-id="b5050-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="b5050-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5050-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b5050-111">Remarks</span></span>

<span data-ttu-id="b5050-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="b5050-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b5050-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5050-113">Requirements</span></span>

<span data-ttu-id="b5050-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b5050-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b5050-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b5050-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b5050-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="b5050-116">See also</span></span>

[<span data-ttu-id="b5050-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b5050-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)