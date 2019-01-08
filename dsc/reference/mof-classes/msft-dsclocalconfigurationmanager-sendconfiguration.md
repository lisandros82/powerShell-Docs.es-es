---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047552"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="93475-103">Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="93475-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="93475-104">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="93475-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="93475-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="93475-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="93475-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="93475-106">Parameters</span></span>

<span data-ttu-id="93475-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="93475-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="93475-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="93475-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="93475-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="93475-109">Return value</span></span>

<span data-ttu-id="93475-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="93475-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="93475-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="93475-111">Remarks</span></span>

<span data-ttu-id="93475-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="93475-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="93475-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93475-113">Requirements</span></span>

<span data-ttu-id="93475-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="93475-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="93475-115">Espacio de nombres {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="93475-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="93475-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="93475-116">See also</span></span>

[<span data-ttu-id="93475-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="93475-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)