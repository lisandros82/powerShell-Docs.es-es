---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078660"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="25078-103">Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="25078-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="25078-104">Obtiene la salida del agente de configuración asociada con un trabajo específico.</span><span class="sxs-lookup"><span data-stu-id="25078-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="25078-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="25078-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="25078-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="25078-106">Parameters</span></span>

<span data-ttu-id="25078-107">*jobId* \[in\] Identificador del trabajo del que quiere obtener datos de salida.</span><span class="sxs-lookup"><span data-stu-id="25078-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="25078-108">*resumeOutputBookmark* \[in\] Especifica que la salida debe ser una continuación de un marcador anterior.</span><span class="sxs-lookup"><span data-stu-id="25078-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="25078-109">*output* \[out\] Salida del trabajo especificado.</span><span class="sxs-lookup"><span data-stu-id="25078-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="25078-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="25078-110">Return value</span></span>

<span data-ttu-id="25078-111">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="25078-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="25078-112">Observaciones</span><span class="sxs-lookup"><span data-stu-id="25078-112">Remarks</span></span>

<span data-ttu-id="25078-113">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="25078-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="25078-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25078-114">Requirements</span></span>

<span data-ttu-id="25078-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="25078-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="25078-116">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="25078-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="25078-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="25078-117">See also</span></span>

[<span data-ttu-id="25078-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="25078-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)