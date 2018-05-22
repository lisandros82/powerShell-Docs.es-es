---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método ResourceGet de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 30cbaa907d4dc3a921c9e5fe61ffddc5d61c2347
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7f8d6-103">Método ResourceGet de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7f8d6-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7f8d6-104">Llama directamente al método **Get** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="7f8d6-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="7f8d6-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7f8d6-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="7f8d6-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7f8d6-106">Parameters</span></span>
----------

<span data-ttu-id="7f8d6-107">*ResourceType* \[in\] Nombre del recurso al que se va a llamar.</span><span class="sxs-lookup"><span data-stu-id="7f8d6-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="7f8d6-108">*ModuleName* \[in\] Nombre del módulo que contiene el recurso al que se va a llamar.</span><span class="sxs-lookup"><span data-stu-id="7f8d6-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="7f8d6-109">*resourceProperty* \[in\] Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="7f8d6-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="7f8d6-110">Use el cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) para descubrir las propiedades del recurso y sus tipos.</span><span class="sxs-lookup"><span data-stu-id="7f8d6-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="7f8d6-111">*configurations* \[out\] En la devolución, contiene una instancia insertada de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="7f8d6-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="7f8d6-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="7f8d6-112">Return value</span></span>
------------

<span data-ttu-id="7f8d6-113">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="7f8d6-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f8d6-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7f8d6-114">Remarks</span></span>

<span data-ttu-id="7f8d6-115">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="7f8d6-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7f8d6-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f8d6-116">Requirements</span></span>
------------
><span data-ttu-id="7f8d6-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7f8d6-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7f8d6-118">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7f8d6-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7f8d6-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="7f8d6-119">See also</span></span>


[<span data-ttu-id="7f8d6-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7f8d6-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)