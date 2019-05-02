---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetMetaConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078527"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9cbc5-103">Método GetMetaConfiguration de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9cbc5-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9cbc5-104">Obtiene la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="9cbc5-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="9cbc5-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9cbc5-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="9cbc5-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9cbc5-106">Parameters</span></span>

<span data-ttu-id="9cbc5-107">*MetaConfiguration* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_DSCMetaConfiguration** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="9cbc5-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="9cbc5-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="9cbc5-108">Return value</span></span>

<span data-ttu-id="9cbc5-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="9cbc5-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9cbc5-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9cbc5-110">Remarks</span></span>

<span data-ttu-id="9cbc5-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="9cbc5-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9cbc5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9cbc5-112">Requirements</span></span>

<span data-ttu-id="9cbc5-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9cbc5-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9cbc5-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9cbc5-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9cbc5-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="9cbc5-115">See also</span></span>

[<span data-ttu-id="9cbc5-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9cbc5-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)