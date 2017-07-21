---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método SendMetaConfigurationApply de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c2bcb-103">Método SendMetaConfigurationApply de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c2bcb-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c2bcb-104">Establece la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="c2bcb-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="c2bcb-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c2bcb-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="c2bcb-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c2bcb-106">Parameters</span></span>
----------

<span data-ttu-id="c2bcb-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c2bcb-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="c2bcb-108">Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="c2bcb-108">The environment data for the configuration.</span></span>

<span data-ttu-id="c2bcb-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c2bcb-109">*force* \[in\]</span></span>  
<span data-ttu-id="c2bcb-110">**true** para forzar la configuración que se detendrá.</span><span class="sxs-lookup"><span data-stu-id="c2bcb-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c2bcb-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="c2bcb-111">Return value</span></span>
------------

<span data-ttu-id="c2bcb-112">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="c2bcb-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2bcb-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="c2bcb-113">Remarks</span></span>

<span data-ttu-id="c2bcb-114">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="c2bcb-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c2bcb-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2bcb-115">Requirements</span></span>
------------
><span data-ttu-id="c2bcb-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c2bcb-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c2bcb-117">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c2bcb-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c2bcb-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="c2bcb-118">See also</span></span>


[<span data-ttu-id="c2bcb-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c2bcb-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



