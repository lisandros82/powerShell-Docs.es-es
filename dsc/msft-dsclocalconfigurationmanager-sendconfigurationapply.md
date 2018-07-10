---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfigurationApply de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893178"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="13ee4-103">Método SendConfigurationApply de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="13ee4-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="13ee4-104">Envía el documento de configuración al nodo administrado y usa al agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="13ee4-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="13ee4-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="13ee4-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="13ee4-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="13ee4-106">Parameters</span></span>

<span data-ttu-id="13ee4-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="13ee4-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="13ee4-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="13ee4-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="13ee4-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="13ee4-109">Return value</span></span>

<span data-ttu-id="13ee4-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="13ee4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="13ee4-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="13ee4-111">Remarks</span></span>

<span data-ttu-id="13ee4-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="13ee4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="13ee4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13ee4-113">Requirements</span></span>

<span data-ttu-id="13ee4-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="13ee4-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="13ee4-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="13ee4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="13ee4-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="13ee4-116">See also</span></span>

[<span data-ttu-id="13ee4-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="13ee4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)