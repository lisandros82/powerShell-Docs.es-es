---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9e2a978f9d16abaed959be022229db4da5fd65bd
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218202"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="331aa-103">Método EnableDebugConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="331aa-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="331aa-104">Habilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="331aa-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="331aa-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="331aa-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="331aa-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="331aa-106">Parameters</span></span>
----------

<span data-ttu-id="331aa-107">*BreakAll* \[in\] Establece un punto de interrupción en cada línea del script de recursos.</span><span class="sxs-lookup"><span data-stu-id="331aa-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="331aa-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="331aa-108">Return value</span></span>
------------

<span data-ttu-id="331aa-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="331aa-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="331aa-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="331aa-110">Remarks</span></span>

<span data-ttu-id="331aa-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="331aa-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="331aa-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="331aa-112">Requirements</span></span>
------------
><span data-ttu-id="331aa-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="331aa-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="331aa-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="331aa-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="331aa-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="331aa-115">See also</span></span>


[<span data-ttu-id="331aa-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="331aa-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)