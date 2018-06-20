---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 46eec896df643996bea5f2c371a9294034caae6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218423"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5734f-103">Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5734f-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5734f-104">Envía el documento de configuración al nodo administrado y usa el método **Get** del agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="5734f-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="5734f-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5734f-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="5734f-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5734f-106">Parameters</span></span>
----------

<span data-ttu-id="5734f-107">*configurationData* \[in\] Especifica los datos de configuración que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="5734f-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="5734f-108">*configurations* \[out\] En la devolución, contiene una instancia insertada de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="5734f-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="5734f-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="5734f-109">Return value</span></span>
------------

<span data-ttu-id="5734f-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="5734f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5734f-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5734f-111">Remarks</span></span>

<span data-ttu-id="5734f-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="5734f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5734f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5734f-113">Requirements</span></span>
------------
><span data-ttu-id="5734f-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5734f-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5734f-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5734f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5734f-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="5734f-116">See also</span></span>


[<span data-ttu-id="5734f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5734f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)