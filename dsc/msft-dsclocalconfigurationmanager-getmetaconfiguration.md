---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método GetMetaConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="59124-103">Método GetMetaConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="59124-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="59124-104">Obtiene la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="59124-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="59124-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="59124-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="59124-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="59124-106">Parameters</span></span>
----------

<span data-ttu-id="59124-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="59124-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="59124-108">En la devolución, contiene una instancia incrustada de la clase **MSFT_DSCMetaConfiguration** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="59124-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="59124-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="59124-109">Return value</span></span>
------------

<span data-ttu-id="59124-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="59124-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="59124-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="59124-111">Remarks</span></span>

<span data-ttu-id="59124-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="59124-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="59124-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59124-113">Requirements</span></span>
------------
><span data-ttu-id="59124-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="59124-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="59124-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="59124-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="59124-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="59124-116">See also</span></span>


[<span data-ttu-id="59124-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="59124-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



