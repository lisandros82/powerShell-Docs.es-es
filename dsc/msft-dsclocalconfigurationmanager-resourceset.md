---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Método ResourceSet de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b5f437a123bd38df21f30d11e71d2c3b36bc9f3a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1ae4b-103">Método ResourceSet de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1ae4b-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1ae4b-104">Llama directamente al método **Set** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="1ae4b-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1ae4b-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="1ae4b-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1ae4b-106">Parameters</span></span>
----------

<span data-ttu-id="1ae4b-107">*ResourceType* \[in\] Nombre del recurso al que se va a llamar.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="1ae4b-108">*ModuleName* \[in\] Nombre del módulo que contiene el recurso al que se va a llamar.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="1ae4b-109">*resourceProperty* \[in\] Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="1ae4b-110">Use el cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) para descubrir las propiedades del recurso y sus tipos.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="1ae4b-111">*RebootRequired* \[out\] En la devolución, esta propiedad se establece en **true** si el nodo de destino debe reiniciarse.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="1ae4b-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1ae4b-112">Return value</span></span>
------------

<span data-ttu-id="1ae4b-113">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ae4b-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1ae4b-114">Remarks</span></span>

<span data-ttu-id="1ae4b-115">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ae4b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ae4b-116">Requirements</span></span>
------------
><span data-ttu-id="1ae4b-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1ae4b-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1ae4b-118">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1ae4b-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1ae4b-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="1ae4b-119">See also</span></span>


[<span data-ttu-id="1ae4b-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1ae4b-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)