---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método ResourceGet
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727114"
---
# <a name="resourceget-method"></a><span data-ttu-id="0d351-103">Método ResourceGet</span><span class="sxs-lookup"><span data-stu-id="0d351-103">ResourceGet method</span></span>

<span data-ttu-id="0d351-104">Llama directamente al método **Get** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="0d351-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d351-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0d351-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="0d351-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d351-106">Parameters</span></span>

<span data-ttu-id="0d351-107">*ResourceType* \[in\] Nombre del recurso al que se va a llamar.</span><span class="sxs-lookup"><span data-stu-id="0d351-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="0d351-108">*ModuleName* \[in\] Nombre del módulo que contiene el recurso al que se va a llamar.</span><span class="sxs-lookup"><span data-stu-id="0d351-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="0d351-109">*resourceProperty* \[in\] Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0d351-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="0d351-110">Use el cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) para descubrir las propiedades del recurso y sus tipos.</span><span class="sxs-lookup"><span data-stu-id="0d351-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="0d351-111">*configurations* \[out\] En la devolución, contiene una instancia insertada de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="0d351-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d351-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0d351-112">Return value</span></span>

<span data-ttu-id="0d351-113">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="0d351-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d351-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0d351-114">Remarks</span></span>

<span data-ttu-id="0d351-115">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="0d351-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d351-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d351-116">Requirements</span></span>

<span data-ttu-id="0d351-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0d351-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0d351-118">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0d351-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0d351-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="0d351-119">See also</span></span>

[<span data-ttu-id="0d351-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0d351-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
