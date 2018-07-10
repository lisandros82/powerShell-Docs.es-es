---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método TestConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893933"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d98b6-103">Método TestConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d98b6-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d98b6-104">Envía el documento de configuración al nodo administrado y prueba la configuración actual frente al documento.</span><span class="sxs-lookup"><span data-stu-id="d98b6-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="d98b6-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d98b6-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="d98b6-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d98b6-106">Parameters</span></span>

<span data-ttu-id="d98b6-107">*configurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="d98b6-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="d98b6-108">*InDesiredState* \[out\] En la devolución, especifica si el nodo administrado está en el estado especificado por el documento de configuración.</span><span class="sxs-lookup"><span data-stu-id="d98b6-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="d98b6-109">*ResourcesInDesiredState* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_ResourceInDesiredState**, que especifica los recursos que están en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="d98b6-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="d98b6-110">*ResourcesNotInDesiredState* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_ResourceNotInDesiredState**, que especifica los recursos que no están en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="d98b6-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="d98b6-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="d98b6-111">Return value</span></span>

<span data-ttu-id="d98b6-112">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="d98b6-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d98b6-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d98b6-113">Remarks</span></span>

<span data-ttu-id="d98b6-114">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="d98b6-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d98b6-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d98b6-115">Requirements</span></span>

<span data-ttu-id="d98b6-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d98b6-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d98b6-117">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d98b6-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d98b6-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="d98b6-118">See also</span></span>

[<span data-ttu-id="d98b6-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d98b6-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)