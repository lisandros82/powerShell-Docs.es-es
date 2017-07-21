---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método ResourceTest de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 73d7d543505a3768a0660084345d3858e055514f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="51983-103">Método ResourceTest de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="51983-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="51983-104">Llama directamente al método **Test** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="51983-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="51983-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="51983-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="51983-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="51983-106">Parameters</span></span>
----------

<span data-ttu-id="51983-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="51983-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="51983-108">Nombre del recurso al que se llamará.</span><span class="sxs-lookup"><span data-stu-id="51983-108">The name of the resource to call.</span></span>

<span data-ttu-id="51983-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="51983-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="51983-110">Nombre del módulo que contiene el recurso al que se llamará.</span><span class="sxs-lookup"><span data-stu-id="51983-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="51983-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="51983-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="51983-112">Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="51983-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="51983-113">Use el cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) para descubrir las propiedades del recurso y sus tipos.</span><span class="sxs-lookup"><span data-stu-id="51983-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="51983-114">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="51983-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="51983-115">En la devolución, esta propiedad se establece en **true** si el nodo de destino está en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="51983-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="51983-116">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="51983-116">Return value</span></span>
------------

<span data-ttu-id="51983-117">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="51983-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="51983-118">Observaciones</span><span class="sxs-lookup"><span data-stu-id="51983-118">Remarks</span></span>

<span data-ttu-id="51983-119">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="51983-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="51983-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51983-120">Requirements</span></span>
------------
><span data-ttu-id="51983-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="51983-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="51983-122">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="51983-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="51983-123">Vea también</span><span class="sxs-lookup"><span data-stu-id="51983-123">See also</span></span>


[<span data-ttu-id="51983-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="51983-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



