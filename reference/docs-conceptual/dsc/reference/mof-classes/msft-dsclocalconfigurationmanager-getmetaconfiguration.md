---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetMetaConfiguration
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953412"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="575a9-103">Método GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="575a9-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="575a9-104">Obtiene la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="575a9-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="575a9-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="575a9-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="575a9-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="575a9-106">Parameters</span></span>

<span data-ttu-id="575a9-107">*MetaConfiguration* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_DSCMetaConfiguration** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="575a9-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="575a9-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="575a9-108">Return value</span></span>

<span data-ttu-id="575a9-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="575a9-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="575a9-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="575a9-110">Remarks</span></span>

<span data-ttu-id="575a9-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="575a9-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="575a9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="575a9-112">Requirements</span></span>

<span data-ttu-id="575a9-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="575a9-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="575a9-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="575a9-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="575a9-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="575a9-115">See also</span></span>

[<span data-ttu-id="575a9-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="575a9-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
