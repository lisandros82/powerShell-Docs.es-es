---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 72fbedf30e5058d8003ed620400d6b443d50dff6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="48e25-103">Método ApplyConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="48e25-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="48e25-104">Usa el agente de configuración para aplicar la configuración que está pendiente.</span><span class="sxs-lookup"><span data-stu-id="48e25-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="48e25-105">Si no hay ninguna configuración pendiente, este método vuelve a aplicar la configuración actual.</span><span class="sxs-lookup"><span data-stu-id="48e25-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="48e25-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="48e25-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="48e25-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="48e25-107">Parameters</span></span>
----------

<span data-ttu-id="48e25-108">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="48e25-108">*force* \[in\]</span></span>  
<span data-ttu-id="48e25-109">Si es **true**, se vuelve a aplicar la configuración actual, incluso si hay una configuración pendiente.</span><span class="sxs-lookup"><span data-stu-id="48e25-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="48e25-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="48e25-110">Return value</span></span>
------------

<span data-ttu-id="48e25-111">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="48e25-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="48e25-112">Observaciones</span><span class="sxs-lookup"><span data-stu-id="48e25-112">Remarks</span></span>

<span data-ttu-id="48e25-113">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="48e25-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="48e25-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48e25-114">Requirements</span></span>
------------
><span data-ttu-id="48e25-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="48e25-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="48e25-116">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="48e25-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="48e25-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="48e25-117">See also</span></span>


[<span data-ttu-id="48e25-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="48e25-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



