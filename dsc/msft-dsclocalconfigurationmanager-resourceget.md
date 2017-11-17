---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método ResourceGet de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 7d8b185c49778253dcb4e983ad948775c4cb0842
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0b537-103">Método ResourceGet de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0b537-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0b537-104">Llama directamente al método **Get** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="0b537-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="0b537-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0b537-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="0b537-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0b537-106">Parameters</span></span>
----------

<span data-ttu-id="0b537-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0b537-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="0b537-108">Nombre del recurso al que se llamará.</span><span class="sxs-lookup"><span data-stu-id="0b537-108">The name of the resource to call.</span></span>

<span data-ttu-id="0b537-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0b537-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="0b537-110">Nombre del módulo que contiene el recurso al que se llamará.</span><span class="sxs-lookup"><span data-stu-id="0b537-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="0b537-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0b537-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="0b537-112">Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0b537-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="0b537-113">Use el cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) para descubrir las propiedades del recurso y sus tipos.</span><span class="sxs-lookup"><span data-stu-id="0b537-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="0b537-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="0b537-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="0b537-115">En la devolución, contiene una instancia incrustada de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="0b537-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="0b537-116">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0b537-116">Return value</span></span>
------------

<span data-ttu-id="0b537-117">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="0b537-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0b537-118">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0b537-118">Remarks</span></span>

<span data-ttu-id="0b537-119">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="0b537-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0b537-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b537-120">Requirements</span></span>
------------
><span data-ttu-id="0b537-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0b537-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0b537-122">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0b537-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0b537-123">Vea también</span><span class="sxs-lookup"><span data-stu-id="0b537-123">See also</span></span>


[<span data-ttu-id="0b537-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0b537-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



