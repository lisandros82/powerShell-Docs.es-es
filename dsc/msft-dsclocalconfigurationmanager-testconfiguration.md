---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método TestConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 04f0f3146473dc71f492086449d9dce5467c55db
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7c3ee-103">Método TestConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7c3ee-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7c3ee-104">Envía el documento de configuración al nodo administrado y prueba la configuración actual frente al documento.</span><span class="sxs-lookup"><span data-stu-id="7c3ee-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="7c3ee-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7c3ee-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="7c3ee-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7c3ee-106">Parameters</span></span>
----------

<span data-ttu-id="7c3ee-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7c3ee-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="7c3ee-108">Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="7c3ee-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="7c3ee-109">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="7c3ee-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="7c3ee-110">En la devolución, especifica si el nodo administrado está en el estado especificado por el documento de configuración.</span><span class="sxs-lookup"><span data-stu-id="7c3ee-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="7c3ee-111">*ResourcesInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="7c3ee-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="7c3ee-112">En la devolución, contiene una instancia incrustada de la clase **MSFT_ResourceInDesiredState**, que especifica los recursos que están en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="7c3ee-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="7c3ee-113">*ResourcesNotInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="7c3ee-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="7c3ee-114">En la devolución, contiene una instancia incrustada de la clase **MSFT_ResourceNotInDesiredState**, que especifica los recursos que no están en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="7c3ee-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="7c3ee-115">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="7c3ee-115">Return value</span></span>
------------

<span data-ttu-id="7c3ee-116">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="7c3ee-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c3ee-117">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7c3ee-117">Remarks</span></span>

<span data-ttu-id="7c3ee-118">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="7c3ee-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7c3ee-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c3ee-119">Requirements</span></span>
------------
><span data-ttu-id="7c3ee-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7c3ee-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7c3ee-121">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7c3ee-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7c3ee-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="7c3ee-122">See also</span></span>


[<span data-ttu-id="7c3ee-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7c3ee-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



