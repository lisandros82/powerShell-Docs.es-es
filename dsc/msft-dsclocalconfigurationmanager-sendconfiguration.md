---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892450"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="83bcc-103">Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="83bcc-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="83bcc-104">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="83bcc-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="83bcc-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="83bcc-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="83bcc-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="83bcc-106">Parameters</span></span>

<span data-ttu-id="83bcc-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="83bcc-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="83bcc-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="83bcc-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="83bcc-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="83bcc-109">Return value</span></span>

<span data-ttu-id="83bcc-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="83bcc-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="83bcc-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="83bcc-111">Remarks</span></span>

<span data-ttu-id="83bcc-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="83bcc-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="83bcc-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83bcc-113">Requirements</span></span>

<span data-ttu-id="83bcc-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="83bcc-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="83bcc-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="83bcc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="83bcc-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="83bcc-116">See also</span></span>

[<span data-ttu-id="83bcc-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="83bcc-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)