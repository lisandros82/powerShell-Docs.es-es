---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método ResourceTest de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 799b1cd91dfacf25c0e5e734ca96d20a776103f0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="52674-103">Método ResourceTest de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="52674-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="52674-104">Llama directamente al método **Test** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="52674-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="52674-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="52674-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="52674-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="52674-106">Parameters</span></span>
----------

<span data-ttu-id="52674-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="52674-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="52674-108">Nombre del recurso al que se llamará.</span><span class="sxs-lookup"><span data-stu-id="52674-108">The name of the resource to call.</span></span>

<span data-ttu-id="52674-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="52674-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="52674-110">Nombre del módulo que contiene el recurso al que se llamará.</span><span class="sxs-lookup"><span data-stu-id="52674-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="52674-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="52674-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="52674-112">Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="52674-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="52674-113">Use el cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) para descubrir las propiedades del recurso y sus tipos.</span><span class="sxs-lookup"><span data-stu-id="52674-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="52674-114">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="52674-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="52674-115">En la devolución, esta propiedad se establece en **true** si el nodo de destino está en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="52674-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="52674-116">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="52674-116">Return value</span></span>
------------

<span data-ttu-id="52674-117">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="52674-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="52674-118">Observaciones</span><span class="sxs-lookup"><span data-stu-id="52674-118">Remarks</span></span>

<span data-ttu-id="52674-119">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="52674-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="52674-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52674-120">Requirements</span></span>
------------
><span data-ttu-id="52674-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="52674-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="52674-122">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="52674-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="52674-123">Vea también</span><span class="sxs-lookup"><span data-stu-id="52674-123">See also</span></span>


[<span data-ttu-id="52674-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="52674-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



