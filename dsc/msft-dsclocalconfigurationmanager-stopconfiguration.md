---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método StopConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c71d1-103">Método StopConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c71d1-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c71d1-104">Detiene el cambio de configuración que está en curso.</span><span class="sxs-lookup"><span data-stu-id="c71d1-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="c71d1-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c71d1-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="c71d1-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c71d1-106">Parameters</span></span>
----------

<span data-ttu-id="c71d1-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c71d1-107">*force* \[in\]</span></span>  
<span data-ttu-id="c71d1-108">**true** para forzar la configuración que se detendrá.</span><span class="sxs-lookup"><span data-stu-id="c71d1-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c71d1-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="c71d1-109">Return value</span></span>
------------

<span data-ttu-id="c71d1-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="c71d1-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c71d1-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="c71d1-111">Remarks</span></span>

<span data-ttu-id="c71d1-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="c71d1-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c71d1-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c71d1-113">Requirements</span></span>
------------
><span data-ttu-id="c71d1-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c71d1-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c71d1-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c71d1-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c71d1-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="c71d1-116">See also</span></span>


[<span data-ttu-id="c71d1-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c71d1-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



