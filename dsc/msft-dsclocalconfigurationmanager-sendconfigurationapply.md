---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método SendConfigurationApply de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 20f732d35860cccde4e507dc6916e27d0cf8c5f6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5465c-103">Método SendConfigurationApply de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5465c-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5465c-104">Envía el documento de configuración al nodo administrado y usa al agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="5465c-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="5465c-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5465c-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="5465c-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5465c-106">Parameters</span></span>
----------

<span data-ttu-id="5465c-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="5465c-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="5465c-108">Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="5465c-108">The environment data for the configuration.</span></span>

<span data-ttu-id="5465c-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="5465c-109">*force* \[in\]</span></span>  
<span data-ttu-id="5465c-110">**true** para forzar la configuración que se detendrá.</span><span class="sxs-lookup"><span data-stu-id="5465c-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="5465c-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="5465c-111">Return value</span></span>
------------

<span data-ttu-id="5465c-112">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="5465c-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5465c-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5465c-113">Remarks</span></span>

<span data-ttu-id="5465c-114">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="5465c-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5465c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5465c-115">Requirements</span></span>
------------
><span data-ttu-id="5465c-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5465c-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5465c-117">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5465c-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5465c-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="5465c-118">See also</span></span>


[<span data-ttu-id="5465c-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5465c-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



