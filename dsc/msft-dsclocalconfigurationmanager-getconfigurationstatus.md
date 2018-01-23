---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="41afb-103">Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="41afb-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="41afb-104">Obtiene el historial de estado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="41afb-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="41afb-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="41afb-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="41afb-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="41afb-106">Parameters</span></span>
----------

<span data-ttu-id="41afb-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="41afb-107">*All* \[in\]</span></span>  
<span data-ttu-id="41afb-108">**true** si este método debe devolver información sobre toda la configuración que se ejecuta en el equipo, incluidas la aplicación de configuración y la comprobación de coherencia.</span><span class="sxs-lookup"><span data-stu-id="41afb-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="41afb-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="41afb-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="41afb-110">En la devolución, contiene una instancia incrustada de la clase **MSFT_DSCConfigurationStatus** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="41afb-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="41afb-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="41afb-111">Return value</span></span>
------------

<span data-ttu-id="41afb-112">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="41afb-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="41afb-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="41afb-113">Remarks</span></span>

<span data-ttu-id="41afb-114">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="41afb-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="41afb-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41afb-115">Requirements</span></span>
------------
><span data-ttu-id="41afb-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="41afb-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="41afb-117">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="41afb-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="41afb-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="41afb-118">See also</span></span>


[<span data-ttu-id="41afb-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="41afb-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



