---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7f6aaf209601e99b0120407eb301d32fcfda9eb8
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048045"
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cee2d-103">Clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cee2d-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cee2d-104">Administrador de configuración Local (LCM) que controla los estados de los archivos de configuración y usa al agente de configuración para aplicar las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="cee2d-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="cee2d-105">La siguiente sintaxis se simplifica desde el código de Managed Object Format (MOF) e incluye todas las propiedades heredadas.</span><span class="sxs-lookup"><span data-stu-id="cee2d-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="cee2d-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cee2d-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="cee2d-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="cee2d-107">Members</span></span>

<span data-ttu-id="cee2d-108">La clase **MSFT_DSCLocalConfigurationManager** tiene los miembros siguientes:</span><span class="sxs-lookup"><span data-stu-id="cee2d-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="cee2d-109">[Métodos][]</span><span class="sxs-lookup"><span data-stu-id="cee2d-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="cee2d-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="cee2d-110">Methods</span></span>

<span data-ttu-id="cee2d-111">La clase **MSFT_DSCLocalConfigurationManager** tiene estos métodos.</span><span class="sxs-lookup"><span data-stu-id="cee2d-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="cee2d-112">Método</span><span class="sxs-lookup"><span data-stu-id="cee2d-112">Method</span></span> |<span data-ttu-id="cee2d-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="cee2d-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="cee2d-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="cee2d-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="cee2d-115">Usa el agente de configuración para aplicar la configuración que está pendiente.</span><span class="sxs-lookup"><span data-stu-id="cee2d-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="cee2d-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="cee2d-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="cee2d-117">Deshabilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="cee2d-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="cee2d-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="cee2d-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="cee2d-119">Habilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="cee2d-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="cee2d-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="cee2d-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="cee2d-121">Envía el documento de configuración al nodo administrado y usa el método **Get** del agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="cee2d-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="cee2d-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="cee2d-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="cee2d-123">Obtiene la salida del agente de configuración relacionada con un trabajo específico.</span><span class="sxs-lookup"><span data-stu-id="cee2d-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="cee2d-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="cee2d-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="cee2d-125">Obtiene el historial de estado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="cee2d-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="cee2d-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="cee2d-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="cee2d-127">Obtiene la configuración del LCM que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="cee2d-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="cee2d-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="cee2d-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="cee2d-129">Inicia la comprobación de coherencia.</span><span class="sxs-lookup"><span data-stu-id="cee2d-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="cee2d-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="cee2d-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="cee2d-131">Quita los archivos de configuración.</span><span class="sxs-lookup"><span data-stu-id="cee2d-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="cee2d-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="cee2d-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="cee2d-133">Llama directamente al método **Get** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="cee2d-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="cee2d-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="cee2d-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="cee2d-135">Llama directamente al método **Set** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="cee2d-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="cee2d-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="cee2d-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="cee2d-137">Llama directamente al método **Test** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="cee2d-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="cee2d-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="cee2d-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="cee2d-139">Revierte una configuración anterior.</span><span class="sxs-lookup"><span data-stu-id="cee2d-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="cee2d-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="cee2d-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="cee2d-141">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="cee2d-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="cee2d-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="cee2d-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="cee2d-143">Envía el documento de configuración al nodo administrado y usa al agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="cee2d-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="cee2d-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="cee2d-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="cee2d-145">Envía el documento de configuración al nodo administrado y empieza a usar el agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="cee2d-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="cee2d-146">Usa GetConfigurationResultOutput para recuperar la salida de resultados.</span><span class="sxs-lookup"><span data-stu-id="cee2d-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="cee2d-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="cee2d-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="cee2d-148">Establece la configuración del LCM que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="cee2d-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="cee2d-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="cee2d-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="cee2d-150">Detiene la configuración que está en curso.</span><span class="sxs-lookup"><span data-stu-id="cee2d-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="cee2d-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="cee2d-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="cee2d-152">Envía el documento de configuración al nodo administrado y prueba la configuración actual frente al documento.</span><span class="sxs-lookup"><span data-stu-id="cee2d-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="cee2d-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cee2d-153">Requirements</span></span>

<span data-ttu-id="cee2d-154">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cee2d-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cee2d-155">Espacio de nombres {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cee2d-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>