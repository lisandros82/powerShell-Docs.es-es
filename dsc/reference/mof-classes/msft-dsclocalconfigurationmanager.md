---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 09b30edd48384c0e8412e0e6ee926a719249c5b8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726892"
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="dd8ce-103">Clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="dd8ce-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="dd8ce-104">Administrador de configuración Local (LCM) que controla los estados de los archivos de configuración y usa al agente de configuración para aplicar las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="dd8ce-105">La siguiente sintaxis se simplifica desde el código de Managed Object Format (MOF) e incluye todas las propiedades heredadas.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd8ce-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="dd8ce-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="dd8ce-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="dd8ce-107">Members</span></span>

<span data-ttu-id="dd8ce-108">La clase **MSFT_DSCLocalConfigurationManager** tiene los miembros siguientes:</span><span class="sxs-lookup"><span data-stu-id="dd8ce-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="dd8ce-109">[Métodos][]</span><span class="sxs-lookup"><span data-stu-id="dd8ce-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="dd8ce-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="dd8ce-110">Methods</span></span>

<span data-ttu-id="dd8ce-111">La clase **MSFT_DSCLocalConfigurationManager** tiene estos métodos.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="dd8ce-112">Método</span><span class="sxs-lookup"><span data-stu-id="dd8ce-112">Method</span></span> |<span data-ttu-id="dd8ce-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="dd8ce-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="dd8ce-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd8ce-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="dd8ce-115">Usa el agente de configuración para aplicar la configuración que está pendiente.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="dd8ce-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd8ce-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="dd8ce-117">Deshabilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="dd8ce-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd8ce-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="dd8ce-119">Habilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="dd8ce-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd8ce-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="dd8ce-121">Envía el documento de configuración al nodo administrado y usa el método **Get** del agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="dd8ce-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="dd8ce-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="dd8ce-123">Obtiene la salida del agente de configuración relacionada con un trabajo específico.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="dd8ce-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="dd8ce-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="dd8ce-125">Obtiene el historial de estado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="dd8ce-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd8ce-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="dd8ce-127">Obtiene la configuración del LCM que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="dd8ce-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="dd8ce-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="dd8ce-129">Inicia la comprobación de coherencia.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="dd8ce-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd8ce-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="dd8ce-131">Quita los archivos de configuración.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="dd8ce-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="dd8ce-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="dd8ce-133">Llama directamente al método **Get** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="dd8ce-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="dd8ce-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="dd8ce-135">Llama directamente al método **Set** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="dd8ce-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="dd8ce-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="dd8ce-137">Llama directamente al método **Test** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="dd8ce-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="dd8ce-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="dd8ce-139">Revierte una configuración anterior.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="dd8ce-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd8ce-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="dd8ce-141">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="dd8ce-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="dd8ce-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="dd8ce-143">Envía el documento de configuración al nodo administrado y usa al agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="dd8ce-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="dd8ce-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="dd8ce-145">Envía el documento de configuración al nodo administrado y empieza a usar el agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="dd8ce-146">Usa GetConfigurationResultOutput para recuperar la salida de resultados.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="dd8ce-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="dd8ce-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="dd8ce-148">Establece la configuración del LCM que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="dd8ce-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd8ce-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="dd8ce-150">Detiene la configuración que está en curso.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="dd8ce-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd8ce-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="dd8ce-152">Envía el documento de configuración al nodo administrado y prueba la configuración actual frente al documento.</span><span class="sxs-lookup"><span data-stu-id="dd8ce-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="dd8ce-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd8ce-153">Requirements</span></span>

<span data-ttu-id="dd8ce-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="dd8ce-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="dd8ce-155">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd8ce-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>
