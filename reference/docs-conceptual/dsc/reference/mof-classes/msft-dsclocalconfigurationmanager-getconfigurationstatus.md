---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetConfigurationStatus
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955022"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="de508-103">Método GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="de508-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="de508-104">Obtiene el historial de estado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="de508-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="de508-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="de508-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="de508-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="de508-106">Parameters</span></span>

<span data-ttu-id="de508-107">*All* \[in\] **true** si este método debe devolver información sobre toda la configuración que se ejecuta en la máquina, incluidas la aplicación de configuración y la comprobación de coherencia.</span><span class="sxs-lookup"><span data-stu-id="de508-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="de508-108">*configurationStatus* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_DSCConfigurationStatus** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="de508-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="de508-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="de508-109">Return value</span></span>

<span data-ttu-id="de508-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="de508-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="de508-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="de508-111">Remarks</span></span>

<span data-ttu-id="de508-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="de508-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="de508-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de508-113">Requirements</span></span>

<span data-ttu-id="de508-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="de508-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="de508-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="de508-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="de508-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="de508-116">See also</span></span>

[<span data-ttu-id="de508-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="de508-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
