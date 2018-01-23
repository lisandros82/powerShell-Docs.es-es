---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método RollBack de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: a219703389405c0dd457d0b2e0b1c54b9c28f559
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4fac1-103">Método RollBack de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4fac1-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4fac1-104">Revierte la configuración a una versión anterior.</span><span class="sxs-lookup"><span data-stu-id="4fac1-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="4fac1-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4fac1-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="4fac1-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4fac1-106">Parameters</span></span>
----------

<span data-ttu-id="4fac1-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4fac1-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="4fac1-108">Especifica la configuración solicitada.</span><span class="sxs-lookup"><span data-stu-id="4fac1-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="4fac1-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4fac1-109">Return value</span></span>
------------

<span data-ttu-id="4fac1-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="4fac1-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4fac1-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4fac1-111">Remarks</span></span>

<span data-ttu-id="4fac1-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="4fac1-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4fac1-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4fac1-113">Requirements</span></span>
------------
><span data-ttu-id="4fac1-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4fac1-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4fac1-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4fac1-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4fac1-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="4fac1-116">See also</span></span>


[<span data-ttu-id="4fac1-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4fac1-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



