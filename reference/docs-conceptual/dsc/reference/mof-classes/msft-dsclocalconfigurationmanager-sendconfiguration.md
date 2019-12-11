---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfiguration
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953392"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="9d7f7-103">Método SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="9d7f7-103">SendConfiguration method</span></span>

<span data-ttu-id="9d7f7-104">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="9d7f7-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d7f7-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9d7f7-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="9d7f7-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9d7f7-106">Parameters</span></span>

<span data-ttu-id="9d7f7-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="9d7f7-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="9d7f7-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="9d7f7-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9d7f7-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="9d7f7-109">Return value</span></span>

<span data-ttu-id="9d7f7-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="9d7f7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d7f7-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9d7f7-111">Remarks</span></span>

<span data-ttu-id="9d7f7-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="9d7f7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d7f7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d7f7-113">Requirements</span></span>

<span data-ttu-id="9d7f7-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9d7f7-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9d7f7-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9d7f7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9d7f7-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="9d7f7-116">See also</span></span>

[<span data-ttu-id="9d7f7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9d7f7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
