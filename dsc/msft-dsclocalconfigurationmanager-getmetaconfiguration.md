---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Método GetMetaConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ddc016402239bcdea060a717fbac9ab7ea42698c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d0c2d-103">Método GetMetaConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d0c2d-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d0c2d-104">Obtiene la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="d0c2d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d0c2d-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="d0c2d-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d0c2d-106">Parameters</span></span>
----------

<span data-ttu-id="d0c2d-107">*MetaConfiguration* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_DSCMetaConfiguration** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="d0c2d-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="d0c2d-108">Return value</span></span>
------------

<span data-ttu-id="d0c2d-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0c2d-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d0c2d-110">Remarks</span></span>

<span data-ttu-id="d0c2d-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="d0c2d-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0c2d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0c2d-112">Requirements</span></span>
------------
><span data-ttu-id="d0c2d-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d0c2d-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d0c2d-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d0c2d-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d0c2d-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="d0c2d-115">See also</span></span>


[<span data-ttu-id="d0c2d-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d0c2d-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)