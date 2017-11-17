---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 96676a76a0302543e5e4a214c82ed952d7f52a71
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fe84a-103">Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fe84a-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fe84a-104">Envía el documento de configuración al nodo administrado y usa el método **Get** del agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="fe84a-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="fe84a-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fe84a-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="fe84a-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="fe84a-106">Parameters</span></span>
----------

<span data-ttu-id="fe84a-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="fe84a-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="fe84a-108">Especifica los datos de configuración que se enviarán.</span><span class="sxs-lookup"><span data-stu-id="fe84a-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="fe84a-109">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="fe84a-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="fe84a-110">En la devolución, contiene una instancia incrustada de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="fe84a-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="fe84a-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="fe84a-111">Return value</span></span>
------------

<span data-ttu-id="fe84a-112">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="fe84a-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe84a-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fe84a-113">Remarks</span></span>

<span data-ttu-id="fe84a-114">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="fe84a-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fe84a-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe84a-115">Requirements</span></span>
------------
><span data-ttu-id="fe84a-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fe84a-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="fe84a-117">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fe84a-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="fe84a-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="fe84a-118">See also</span></span>


[<span data-ttu-id="fe84a-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fe84a-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



