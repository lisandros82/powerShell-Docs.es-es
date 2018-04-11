---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 07d7db9dcc4288e6b72d5df37d82e44eb6f72ad2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e42c7-103">Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e42c7-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e42c7-104">Envía el documento de configuración al nodo administrado y usa el método **Get** del agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="e42c7-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="e42c7-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e42c7-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="e42c7-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e42c7-106">Parameters</span></span>
----------

<span data-ttu-id="e42c7-107">*configurationData* \[in\] Especifica los datos de configuración que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="e42c7-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="e42c7-108">*configurations* \[out\] En la devolución, contiene una instancia insertada de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="e42c7-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="e42c7-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="e42c7-109">Return value</span></span>
------------

<span data-ttu-id="e42c7-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="e42c7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e42c7-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e42c7-111">Remarks</span></span>

<span data-ttu-id="e42c7-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="e42c7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e42c7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e42c7-113">Requirements</span></span>
------------
><span data-ttu-id="e42c7-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e42c7-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e42c7-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e42c7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e42c7-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="e42c7-116">See also</span></span>


[<span data-ttu-id="e42c7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e42c7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)