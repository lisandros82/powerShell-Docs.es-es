---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9e9fe-103">Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9e9fe-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9e9fe-104">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="9e9fe-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="9e9fe-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9e9fe-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="9e9fe-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9e9fe-106">Parameters</span></span>
----------

<span data-ttu-id="9e9fe-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9e9fe-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="9e9fe-108">Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="9e9fe-108">The environment data for the configuration.</span></span>

<span data-ttu-id="9e9fe-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9e9fe-109">*force* \[in\]</span></span>  
<span data-ttu-id="9e9fe-110">**true** para forzar la configuración que se detendrá.</span><span class="sxs-lookup"><span data-stu-id="9e9fe-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9e9fe-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="9e9fe-111">Return value</span></span>
------------

<span data-ttu-id="9e9fe-112">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="9e9fe-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e9fe-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9e9fe-113">Remarks</span></span>

<span data-ttu-id="9e9fe-114">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="9e9fe-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e9fe-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e9fe-115">Requirements</span></span>
------------
><span data-ttu-id="9e9fe-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9e9fe-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9e9fe-117">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9e9fe-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9e9fe-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="9e9fe-118">See also</span></span>


[<span data-ttu-id="9e9fe-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9e9fe-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



