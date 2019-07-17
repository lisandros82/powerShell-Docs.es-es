---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetConfiguration
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734527"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="60c19-103">Método GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="60c19-103">GetConfiguration method</span></span>

<span data-ttu-id="60c19-104">Envía el documento de configuración al nodo administrado y usa el método **Get** del agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="60c19-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="60c19-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="60c19-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="60c19-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="60c19-106">Parameters</span></span>

<span data-ttu-id="60c19-107">*configurationData* \[in\] Especifica los datos de configuración que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="60c19-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="60c19-108">*configurations* \[out\] En la devolución, contiene una instancia insertada de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="60c19-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="60c19-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="60c19-109">Return value</span></span>

<span data-ttu-id="60c19-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="60c19-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="60c19-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="60c19-111">Remarks</span></span>

<span data-ttu-id="60c19-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="60c19-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="60c19-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60c19-113">Requirements</span></span>

<span data-ttu-id="60c19-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="60c19-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="60c19-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="60c19-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="60c19-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="60c19-116">See also</span></span>

[<span data-ttu-id="60c19-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="60c19-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
