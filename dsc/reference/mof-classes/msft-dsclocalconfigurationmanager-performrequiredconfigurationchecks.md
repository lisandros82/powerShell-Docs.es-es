---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método PerformRequiredConfigurationChecks
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734409"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="a48cf-103">Método PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="a48cf-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="a48cf-104">Inicia una comprobación de coherencia mediante el Programador de tareas.</span><span class="sxs-lookup"><span data-stu-id="a48cf-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="a48cf-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a48cf-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="a48cf-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a48cf-106">Parameters</span></span>

<span data-ttu-id="a48cf-107">*Flags* \[in\] Máscara de bits que especifica el tipo de comprobación de coherencia que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="a48cf-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="a48cf-108">Los valores siguientes son válidos y se pueden combinar mediante el uso de una operación **O** bit a bit:</span><span class="sxs-lookup"><span data-stu-id="a48cf-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="a48cf-109">Value</span><span class="sxs-lookup"><span data-stu-id="a48cf-109">Value</span></span> |<span data-ttu-id="a48cf-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="a48cf-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="a48cf-111">**1**</span><span class="sxs-lookup"><span data-stu-id="a48cf-111">**1**</span></span> | <span data-ttu-id="a48cf-112">Comprobación de coherencia normal.</span><span class="sxs-lookup"><span data-stu-id="a48cf-112">A normal consistency check.</span></span> |
|<span data-ttu-id="a48cf-113">**2**</span><span class="sxs-lookup"><span data-stu-id="a48cf-113">**2**</span></span> | <span data-ttu-id="a48cf-114">Continuación de una comprobación de coherencia después de reiniciar el equipo.</span><span class="sxs-lookup"><span data-stu-id="a48cf-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="a48cf-115">Este valor no debe combinarse con otros valores.</span><span class="sxs-lookup"><span data-stu-id="a48cf-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="a48cf-116">**4**</span><span class="sxs-lookup"><span data-stu-id="a48cf-116">**4**</span></span> | <span data-ttu-id="a48cf-117">Debe extraerse la configuración del servidor de extracción especificado en la metaconfiguración del nodo.</span><span class="sxs-lookup"><span data-stu-id="a48cf-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="a48cf-118">Este valor siempre debe combinarse con **1**, para un valor de **5**.</span><span class="sxs-lookup"><span data-stu-id="a48cf-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="a48cf-119">**8**</span><span class="sxs-lookup"><span data-stu-id="a48cf-119">**8**</span></span> | <span data-ttu-id="a48cf-120">Envía el estado al servidor de informes.</span><span class="sxs-lookup"><span data-stu-id="a48cf-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="a48cf-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="a48cf-121">Return value</span></span>

<span data-ttu-id="a48cf-122">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="a48cf-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a48cf-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="a48cf-123">Remarks</span></span>

<span data-ttu-id="a48cf-124">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="a48cf-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a48cf-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a48cf-125">Requirements</span></span>

<span data-ttu-id="a48cf-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a48cf-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a48cf-127">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a48cf-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a48cf-128">Vea también</span><span class="sxs-lookup"><span data-stu-id="a48cf-128">See also</span></span>

[<span data-ttu-id="a48cf-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a48cf-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
