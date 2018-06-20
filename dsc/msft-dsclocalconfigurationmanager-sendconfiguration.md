---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b4d4c901268344ba67d77e4dc982042bfc2abd78
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222214"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a924e-103">Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a924e-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a924e-104">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="a924e-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="a924e-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a924e-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="a924e-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a924e-106">Parameters</span></span>
----------

<span data-ttu-id="a924e-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="a924e-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="a924e-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="a924e-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="a924e-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="a924e-109">Return value</span></span>
------------

<span data-ttu-id="a924e-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="a924e-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a924e-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="a924e-111">Remarks</span></span>

<span data-ttu-id="a924e-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="a924e-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a924e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a924e-113">Requirements</span></span>
------------
><span data-ttu-id="a924e-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a924e-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a924e-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a924e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a924e-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="a924e-116">See also</span></span>


[<span data-ttu-id="a924e-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a924e-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)