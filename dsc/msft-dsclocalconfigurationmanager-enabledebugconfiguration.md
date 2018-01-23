---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: fa34a583af7c3fd46d99307d582973410e4c0e31
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="65bad-103">Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="65bad-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="65bad-104">Habilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="65bad-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="65bad-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="65bad-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="65bad-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="65bad-106">Parameters</span></span>
----------

<span data-ttu-id="65bad-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="65bad-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="65bad-108">Establece un punto de interrupción en cada línea del script de recursos.</span><span class="sxs-lookup"><span data-stu-id="65bad-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="65bad-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="65bad-109">Return value</span></span>
------------

<span data-ttu-id="65bad-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="65bad-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="65bad-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="65bad-111">Remarks</span></span>

<span data-ttu-id="65bad-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="65bad-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="65bad-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65bad-113">Requirements</span></span>
------------
><span data-ttu-id="65bad-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="65bad-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="65bad-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="65bad-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="65bad-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="65bad-116">See also</span></span>


[<span data-ttu-id="65bad-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="65bad-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



