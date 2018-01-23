---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método ResourceGet de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: df90cb6859413c94be992c8cbc30171e9bd3d6de
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d8732-103">Método ResourceGet de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d8732-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d8732-104">Llama directamente al método **Get** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="d8732-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="d8732-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d8732-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="d8732-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d8732-106">Parameters</span></span>
----------

<span data-ttu-id="d8732-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d8732-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="d8732-108">Nombre del recurso al que se llamará.</span><span class="sxs-lookup"><span data-stu-id="d8732-108">The name of the resource to call.</span></span>

<span data-ttu-id="d8732-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d8732-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="d8732-110">Nombre del módulo que contiene el recurso al que se llamará.</span><span class="sxs-lookup"><span data-stu-id="d8732-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="d8732-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d8732-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="d8732-112">Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d8732-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="d8732-113">Use el cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) para descubrir las propiedades del recurso y sus tipos.</span><span class="sxs-lookup"><span data-stu-id="d8732-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="d8732-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="d8732-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="d8732-115">En la devolución, contiene una instancia incrustada de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="d8732-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="d8732-116">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="d8732-116">Return value</span></span>
------------

<span data-ttu-id="d8732-117">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="d8732-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8732-118">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d8732-118">Remarks</span></span>

<span data-ttu-id="d8732-119">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="d8732-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8732-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8732-120">Requirements</span></span>
------------
><span data-ttu-id="d8732-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d8732-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d8732-122">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8732-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d8732-123">Vea también</span><span class="sxs-lookup"><span data-stu-id="d8732-123">See also</span></span>


[<span data-ttu-id="d8732-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d8732-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



