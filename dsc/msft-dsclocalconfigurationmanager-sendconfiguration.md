---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 72c59b5aad293fa561146e5ad6822f27f40f321f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ea8cb-103">Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ea8cb-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ea8cb-104">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="ea8cb-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="ea8cb-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ea8cb-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="ea8cb-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ea8cb-106">Parameters</span></span>
----------

<span data-ttu-id="ea8cb-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ea8cb-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="ea8cb-108">Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="ea8cb-108">The environment data for the configuration.</span></span>

<span data-ttu-id="ea8cb-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ea8cb-109">*force* \[in\]</span></span>  
<span data-ttu-id="ea8cb-110">**true** para forzar la configuración que se detendrá.</span><span class="sxs-lookup"><span data-stu-id="ea8cb-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ea8cb-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="ea8cb-111">Return value</span></span>
------------

<span data-ttu-id="ea8cb-112">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="ea8cb-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea8cb-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ea8cb-113">Remarks</span></span>

<span data-ttu-id="ea8cb-114">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="ea8cb-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea8cb-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea8cb-115">Requirements</span></span>
------------
><span data-ttu-id="ea8cb-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ea8cb-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ea8cb-117">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ea8cb-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ea8cb-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea8cb-118">See also</span></span>


[<span data-ttu-id="ea8cb-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ea8cb-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



