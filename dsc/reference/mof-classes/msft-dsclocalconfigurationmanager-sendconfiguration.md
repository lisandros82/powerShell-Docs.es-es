---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679712"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b5c2b-103">Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b5c2b-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b5c2b-104">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="b5c2b-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5c2b-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b5c2b-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="b5c2b-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b5c2b-106">Parameters</span></span>

<span data-ttu-id="b5c2b-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="b5c2b-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="b5c2b-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="b5c2b-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="b5c2b-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="b5c2b-109">Return value</span></span>

<span data-ttu-id="b5c2b-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="b5c2b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5c2b-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b5c2b-111">Remarks</span></span>

<span data-ttu-id="b5c2b-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="b5c2b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b5c2b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5c2b-113">Requirements</span></span>

<span data-ttu-id="b5c2b-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b5c2b-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b5c2b-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b5c2b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b5c2b-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="b5c2b-116">See also</span></span>

[<span data-ttu-id="b5c2b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b5c2b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)