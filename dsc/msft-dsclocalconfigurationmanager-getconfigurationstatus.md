---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="624d6-103">Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="624d6-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="624d6-104">Obtiene el historial de estado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="624d6-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="624d6-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="624d6-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="624d6-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="624d6-106">Parameters</span></span>
----------

<span data-ttu-id="624d6-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="624d6-107">*All* \[in\]</span></span>  
<span data-ttu-id="624d6-108">**true** si este método debe devolver información sobre toda la configuración que se ejecuta en el equipo, incluidas la aplicación de configuración y la comprobación de coherencia.</span><span class="sxs-lookup"><span data-stu-id="624d6-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="624d6-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="624d6-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="624d6-110">En la devolución, contiene una instancia incrustada de la clase **MSFT_DSCConfigurationStatus** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="624d6-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="624d6-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="624d6-111">Return value</span></span>
------------

<span data-ttu-id="624d6-112">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="624d6-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="624d6-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="624d6-113">Remarks</span></span>

<span data-ttu-id="624d6-114">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="624d6-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="624d6-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="624d6-115">Requirements</span></span>
------------
><span data-ttu-id="624d6-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="624d6-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="624d6-117">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="624d6-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="624d6-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="624d6-118">See also</span></span>


[<span data-ttu-id="624d6-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="624d6-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



