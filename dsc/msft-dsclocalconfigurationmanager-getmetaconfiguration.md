---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Método GetMetaConfiguration de la clase MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3dec7-103">Método GetMetaConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3dec7-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3dec7-104">Obtiene la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="3dec7-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="3dec7-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3dec7-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="3dec7-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3dec7-106">Parameters</span></span>
----------

<span data-ttu-id="3dec7-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="3dec7-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="3dec7-108">En la devolución, contiene una instancia incrustada de la clase **MSFT_DSCMetaConfiguration** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="3dec7-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="3dec7-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="3dec7-109">Return value</span></span>
------------

<span data-ttu-id="3dec7-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="3dec7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3dec7-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3dec7-111">Remarks</span></span>

<span data-ttu-id="3dec7-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="3dec7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3dec7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3dec7-113">Requirements</span></span>
------------
><span data-ttu-id="3dec7-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3dec7-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3dec7-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3dec7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3dec7-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="3dec7-116">See also</span></span>


[<span data-ttu-id="3dec7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3dec7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



