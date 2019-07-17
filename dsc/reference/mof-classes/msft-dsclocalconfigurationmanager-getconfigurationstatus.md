---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetConfigurationStatus
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734515"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="aaeef-103">Método GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="aaeef-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="aaeef-104">Obtiene el historial de estado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="aaeef-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="aaeef-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="aaeef-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="aaeef-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="aaeef-106">Parameters</span></span>

<span data-ttu-id="aaeef-107">*All* \[in\] **true** si este método debe devolver información sobre toda la configuración que se ejecuta en la máquina, incluidas la aplicación de configuración y la comprobación de coherencia.</span><span class="sxs-lookup"><span data-stu-id="aaeef-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="aaeef-108">*configurationStatus* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_DSCConfigurationStatus** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="aaeef-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="aaeef-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="aaeef-109">Return value</span></span>

<span data-ttu-id="aaeef-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="aaeef-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="aaeef-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="aaeef-111">Remarks</span></span>

<span data-ttu-id="aaeef-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="aaeef-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="aaeef-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aaeef-113">Requirements</span></span>

<span data-ttu-id="aaeef-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="aaeef-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="aaeef-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="aaeef-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="aaeef-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="aaeef-116">See also</span></span>

[<span data-ttu-id="aaeef-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="aaeef-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
