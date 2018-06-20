---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221772"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5a24d-103">Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5a24d-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5a24d-104">Obtiene el historial de estado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="5a24d-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="5a24d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5a24d-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="5a24d-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5a24d-106">Parameters</span></span>
----------

<span data-ttu-id="5a24d-107">*All* \[in\] **true** si este método debe devolver información sobre toda la configuración que se ejecuta en la máquina, incluidas la aplicación de configuración y la comprobación de coherencia.</span><span class="sxs-lookup"><span data-stu-id="5a24d-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="5a24d-108">*configurationStatus* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_DSCConfigurationStatus** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="5a24d-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="5a24d-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="5a24d-109">Return value</span></span>
------------

<span data-ttu-id="5a24d-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="5a24d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a24d-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5a24d-111">Remarks</span></span>

<span data-ttu-id="5a24d-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="5a24d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a24d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a24d-113">Requirements</span></span>
------------
><span data-ttu-id="5a24d-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5a24d-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5a24d-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a24d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5a24d-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="5a24d-116">See also</span></span>


[<span data-ttu-id="5a24d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5a24d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)