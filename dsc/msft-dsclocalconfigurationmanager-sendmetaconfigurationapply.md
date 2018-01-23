---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método SendMetaConfigurationApply de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 350555220757b1939b1de34ab423e963635eb53c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="15530-103">Método SendMetaConfigurationApply de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="15530-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="15530-104">Establece la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="15530-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="15530-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="15530-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="15530-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="15530-106">Parameters</span></span>
----------

<span data-ttu-id="15530-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="15530-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="15530-108">Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="15530-108">The environment data for the configuration.</span></span>

<span data-ttu-id="15530-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="15530-109">*force* \[in\]</span></span>  
<span data-ttu-id="15530-110">**true** para forzar la configuración que se detendrá.</span><span class="sxs-lookup"><span data-stu-id="15530-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="15530-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="15530-111">Return value</span></span>
------------

<span data-ttu-id="15530-112">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="15530-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="15530-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="15530-113">Remarks</span></span>

<span data-ttu-id="15530-114">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="15530-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="15530-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="15530-115">Requirements</span></span>
------------
><span data-ttu-id="15530-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="15530-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="15530-117">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="15530-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="15530-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="15530-118">See also</span></span>


[<span data-ttu-id="15530-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="15530-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



