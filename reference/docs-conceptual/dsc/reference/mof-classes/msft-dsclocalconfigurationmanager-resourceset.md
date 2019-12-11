---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método ResourceSet
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954962"
---
# <a name="resourceset-method"></a><span data-ttu-id="350d9-103">Método ResourceSet</span><span class="sxs-lookup"><span data-stu-id="350d9-103">ResourceSet method</span></span>

<span data-ttu-id="350d9-104">Llama directamente al método **Set** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="350d9-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="350d9-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="350d9-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="350d9-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="350d9-106">Parameters</span></span>

<span data-ttu-id="350d9-107">*ResourceType* \[in\] Nombre del recurso al que se va a llamar.</span><span class="sxs-lookup"><span data-stu-id="350d9-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="350d9-108">*ModuleName* \[in\] Nombre del módulo que contiene el recurso al que se va a llamar.</span><span class="sxs-lookup"><span data-stu-id="350d9-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="350d9-109">*resourceProperty* \[in\] Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="350d9-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="350d9-110">Use el cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) para descubrir las propiedades del recurso y sus tipos.</span><span class="sxs-lookup"><span data-stu-id="350d9-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="350d9-111">*RebootRequired* \[out\] En la devolución, esta propiedad se establece en **true** si el nodo de destino debe reiniciarse.</span><span class="sxs-lookup"><span data-stu-id="350d9-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="350d9-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="350d9-112">Return value</span></span>

<span data-ttu-id="350d9-113">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="350d9-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="350d9-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="350d9-114">Remarks</span></span>

<span data-ttu-id="350d9-115">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="350d9-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="350d9-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="350d9-116">Requirements</span></span>

<span data-ttu-id="350d9-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="350d9-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="350d9-118">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="350d9-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="350d9-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="350d9-119">See also</span></span>

[<span data-ttu-id="350d9-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="350d9-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
