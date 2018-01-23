---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 60f4b49575dbb28ce74af0500e6982ec5d2e7a66
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="aa897-103">Método GetConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="aa897-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="aa897-104">Envía el documento de configuración al nodo administrado y usa el método **Get** del agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="aa897-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="aa897-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="aa897-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="aa897-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="aa897-106">Parameters</span></span>
----------

<span data-ttu-id="aa897-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="aa897-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="aa897-108">Especifica los datos de configuración que se enviarán.</span><span class="sxs-lookup"><span data-stu-id="aa897-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="aa897-109">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="aa897-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="aa897-110">En la devolución, contiene una instancia incrustada de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="aa897-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="aa897-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="aa897-111">Return value</span></span>
------------

<span data-ttu-id="aa897-112">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="aa897-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa897-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="aa897-113">Remarks</span></span>

<span data-ttu-id="aa897-114">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="aa897-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa897-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa897-115">Requirements</span></span>
------------
><span data-ttu-id="aa897-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="aa897-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="aa897-117">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="aa897-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="aa897-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="aa897-118">See also</span></span>


[<span data-ttu-id="aa897-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="aa897-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



