---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método ResourceGet
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955002"
---
# <a name="resourceget-method"></a><span data-ttu-id="a4bfd-103">Método ResourceGet</span><span class="sxs-lookup"><span data-stu-id="a4bfd-103">ResourceGet method</span></span>

<span data-ttu-id="a4bfd-104">Llama directamente al método **Get** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="a4bfd-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="a4bfd-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a4bfd-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="a4bfd-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a4bfd-106">Parameters</span></span>

<span data-ttu-id="a4bfd-107">*ResourceType* \[in\] Nombre del recurso al que se va a llamar.</span><span class="sxs-lookup"><span data-stu-id="a4bfd-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="a4bfd-108">*ModuleName* \[in\] Nombre del módulo que contiene el recurso al que se va a llamar.</span><span class="sxs-lookup"><span data-stu-id="a4bfd-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="a4bfd-109">*resourceProperty* \[in\] Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a4bfd-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="a4bfd-110">Use el cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) para descubrir las propiedades del recurso y sus tipos.</span><span class="sxs-lookup"><span data-stu-id="a4bfd-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="a4bfd-111">*configurations* \[out\] En la devolución, contiene una instancia insertada de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="a4bfd-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="a4bfd-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="a4bfd-112">Return value</span></span>

<span data-ttu-id="a4bfd-113">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="a4bfd-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4bfd-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="a4bfd-114">Remarks</span></span>

<span data-ttu-id="a4bfd-115">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="a4bfd-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a4bfd-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4bfd-116">Requirements</span></span>

<span data-ttu-id="a4bfd-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a4bfd-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a4bfd-118">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a4bfd-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a4bfd-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="a4bfd-119">See also</span></span>

[<span data-ttu-id="a4bfd-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a4bfd-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
