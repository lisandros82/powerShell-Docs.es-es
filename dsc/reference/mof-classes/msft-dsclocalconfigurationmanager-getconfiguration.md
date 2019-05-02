---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078663"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0551d-103">Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0551d-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0551d-104">Envía el documento de configuración al nodo administrado y usa el método **Get** del agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="0551d-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="0551d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0551d-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="0551d-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0551d-106">Parameters</span></span>

<span data-ttu-id="0551d-107">*configurationData* \[in\] Especifica los datos de configuración que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="0551d-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="0551d-108">*configurations* \[out\] En la devolución, contiene una instancia insertada de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="0551d-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="0551d-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0551d-109">Return value</span></span>

<span data-ttu-id="0551d-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="0551d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0551d-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0551d-111">Remarks</span></span>

<span data-ttu-id="0551d-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="0551d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0551d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0551d-113">Requirements</span></span>

<span data-ttu-id="0551d-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0551d-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0551d-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0551d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0551d-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="0551d-116">See also</span></span>

[<span data-ttu-id="0551d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0551d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)