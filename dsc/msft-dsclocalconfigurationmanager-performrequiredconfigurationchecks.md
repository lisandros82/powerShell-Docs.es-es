---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método PerformRequiredConfigurationChecks de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 687c92f2dac5e8855731713e81390ac67615231e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0155a-103">Método PerformRequiredConfigurationChecks de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0155a-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0155a-104">Inicia una comprobación de coherencia mediante el Programador de tareas.</span><span class="sxs-lookup"><span data-stu-id="0155a-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="0155a-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0155a-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="0155a-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0155a-106">Parameters</span></span>
----------

<span data-ttu-id="0155a-107">*Flags* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0155a-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="0155a-108">Máscara de bits que especifica el tipo de comprobación de coherencia que se ejecutará.</span><span class="sxs-lookup"><span data-stu-id="0155a-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="0155a-109">Los valores siguientes son válidos y se pueden combinar mediante el uso de una operación **O** bit a bit:</span><span class="sxs-lookup"><span data-stu-id="0155a-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="0155a-110">Value</span><span class="sxs-lookup"><span data-stu-id="0155a-110">Value</span></span> |<span data-ttu-id="0155a-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="0155a-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="0155a-112">**1**</span><span class="sxs-lookup"><span data-stu-id="0155a-112">**1**</span></span> | <span data-ttu-id="0155a-113">Comprobación de coherencia normal.</span><span class="sxs-lookup"><span data-stu-id="0155a-113">A normal consistency check.</span></span> |
|<span data-ttu-id="0155a-114">**2**</span><span class="sxs-lookup"><span data-stu-id="0155a-114">**2**</span></span> | <span data-ttu-id="0155a-115">Continuación de una comprobación de coherencia después de reiniciar el equipo.</span><span class="sxs-lookup"><span data-stu-id="0155a-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="0155a-116">Este valor no debe combinarse con otros valores.</span><span class="sxs-lookup"><span data-stu-id="0155a-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="0155a-117">**4**</span><span class="sxs-lookup"><span data-stu-id="0155a-117">**4**</span></span> | <span data-ttu-id="0155a-118">Debe extraerse la configuración del servidor de extracción especificado en la metaconfiguración del nodo.</span><span class="sxs-lookup"><span data-stu-id="0155a-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="0155a-119">Este valor siempre debe combinarse con **1**, para un valor de **5**.</span><span class="sxs-lookup"><span data-stu-id="0155a-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="0155a-120">**8**</span><span class="sxs-lookup"><span data-stu-id="0155a-120">**8**</span></span> | <span data-ttu-id="0155a-121">Envía el estado al servidor de informes.</span><span class="sxs-lookup"><span data-stu-id="0155a-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="0155a-122">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0155a-122">Return value</span></span>
------------

<span data-ttu-id="0155a-123">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="0155a-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0155a-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0155a-124">Remarks</span></span>

<span data-ttu-id="0155a-125">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="0155a-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0155a-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0155a-126">Requirements</span></span>
------------
><span data-ttu-id="0155a-127">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0155a-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0155a-128">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0155a-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0155a-129">Vea también</span><span class="sxs-lookup"><span data-stu-id="0155a-129">See also</span></span>


[<span data-ttu-id="0155a-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0155a-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



