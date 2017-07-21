---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método SendConfigurationApply de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 9552fd5b5feb862fbe8ef95a7746776e7fe2f5c8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ee5c0-103">Método SendConfigurationApply de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ee5c0-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ee5c0-104">Envía el documento de configuración al nodo administrado y usa al agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="ee5c0-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="ee5c0-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ee5c0-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="ee5c0-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ee5c0-106">Parameters</span></span>
----------

<span data-ttu-id="ee5c0-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ee5c0-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="ee5c0-108">Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="ee5c0-108">The environment data for the configuration.</span></span>

<span data-ttu-id="ee5c0-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ee5c0-109">*force* \[in\]</span></span>  
<span data-ttu-id="ee5c0-110">**true** para forzar la configuración que se detendrá.</span><span class="sxs-lookup"><span data-stu-id="ee5c0-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ee5c0-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="ee5c0-111">Return value</span></span>
------------

<span data-ttu-id="ee5c0-112">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="ee5c0-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee5c0-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ee5c0-113">Remarks</span></span>

<span data-ttu-id="ee5c0-114">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="ee5c0-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee5c0-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ee5c0-115">Requirements</span></span>
------------
><span data-ttu-id="ee5c0-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ee5c0-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ee5c0-117">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee5c0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ee5c0-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="ee5c0-118">See also</span></span>


[<span data-ttu-id="ee5c0-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ee5c0-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



