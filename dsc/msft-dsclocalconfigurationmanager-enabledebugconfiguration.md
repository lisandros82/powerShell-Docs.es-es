---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9ba87-103">Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9ba87-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9ba87-104">Habilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="9ba87-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="9ba87-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9ba87-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="9ba87-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ba87-106">Parameters</span></span>
----------

<span data-ttu-id="9ba87-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9ba87-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="9ba87-108">Establece un punto de interrupción en cada línea del script de recursos.</span><span class="sxs-lookup"><span data-stu-id="9ba87-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="9ba87-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="9ba87-109">Return value</span></span>
------------

<span data-ttu-id="9ba87-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="9ba87-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ba87-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9ba87-111">Remarks</span></span>

<span data-ttu-id="9ba87-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="9ba87-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ba87-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ba87-113">Requirements</span></span>
------------
><span data-ttu-id="9ba87-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9ba87-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9ba87-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9ba87-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9ba87-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="9ba87-116">See also</span></span>


[<span data-ttu-id="9ba87-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9ba87-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



