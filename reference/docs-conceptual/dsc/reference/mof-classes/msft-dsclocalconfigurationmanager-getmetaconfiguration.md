---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetMetaConfiguration
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953412"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="164d3-103">Método GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="164d3-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="164d3-104">Obtiene la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="164d3-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="164d3-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="164d3-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="164d3-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="164d3-106">Parameters</span></span>

<span data-ttu-id="164d3-107">*MetaConfiguration* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_DSCMetaConfiguration** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="164d3-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="164d3-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="164d3-108">Return value</span></span>

<span data-ttu-id="164d3-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="164d3-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="164d3-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="164d3-110">Remarks</span></span>

<span data-ttu-id="164d3-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="164d3-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="164d3-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="164d3-112">Requirements</span></span>

<span data-ttu-id="164d3-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="164d3-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="164d3-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="164d3-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="164d3-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="164d3-115">See also</span></span>

[<span data-ttu-id="164d3-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="164d3-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
