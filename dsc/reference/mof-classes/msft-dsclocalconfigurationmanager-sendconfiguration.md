---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfiguration
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734328"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="20e4e-103">Método SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="20e4e-103">SendConfiguration method</span></span>

<span data-ttu-id="20e4e-104">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="20e4e-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="20e4e-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="20e4e-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="20e4e-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="20e4e-106">Parameters</span></span>

<span data-ttu-id="20e4e-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="20e4e-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="20e4e-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="20e4e-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="20e4e-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="20e4e-109">Return value</span></span>

<span data-ttu-id="20e4e-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="20e4e-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="20e4e-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="20e4e-111">Remarks</span></span>

<span data-ttu-id="20e4e-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="20e4e-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="20e4e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20e4e-113">Requirements</span></span>

<span data-ttu-id="20e4e-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="20e4e-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="20e4e-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="20e4e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="20e4e-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="20e4e-116">See also</span></span>

[<span data-ttu-id="20e4e-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="20e4e-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
