---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 35f732698fcc58f7bd43945edd10c143ffb79af9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d4bdb-103">Clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d4bdb-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d4bdb-104">Administrador de configuración Local (LCM) que controla los estados de los archivos de configuración y usa al agente de configuración para aplicar las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="d4bdb-105">La siguiente sintaxis se simplifica desde el código de Managed Object Format (MOF) e incluye todas las propiedades heredadas.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4bdb-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d4bdb-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="d4bdb-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="d4bdb-107">Members</span></span>
-------

<span data-ttu-id="d4bdb-108">La clase **MSFT_DSCLocalConfigurationManager** tiene los miembros siguientes:</span><span class="sxs-lookup"><span data-stu-id="d4bdb-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="d4bdb-109">[Métodos][]</span><span class="sxs-lookup"><span data-stu-id="d4bdb-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="d4bdb-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="d4bdb-110">Methods</span></span>

<span data-ttu-id="d4bdb-111">La clase **MSFT_DSCLocalConfigurationManager** tiene estos métodos.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="d4bdb-112">Método</span><span class="sxs-lookup"><span data-stu-id="d4bdb-112">Method</span></span> |<span data-ttu-id="d4bdb-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="d4bdb-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="d4bdb-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="d4bdb-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="d4bdb-115">Usa el agente de configuración para aplicar la configuración que está pendiente.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>| 
| [<span data-ttu-id="d4bdb-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="d4bdb-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="d4bdb-117">Deshabilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-117">Disables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="d4bdb-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="d4bdb-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="d4bdb-119">Habilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-119">Enables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="d4bdb-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="d4bdb-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="d4bdb-121">Envía el documento de configuración al nodo administrado y usa el método **Get** del agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="d4bdb-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="d4bdb-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="d4bdb-123">Obtiene la salida del agente de configuración relacionada con un trabajo específico.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-123">Gets the Configuration Agent output relating to a specific job.</span></span>| 
| [<span data-ttu-id="d4bdb-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="d4bdb-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="d4bdb-125">Obtiene el historial de estado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-125">Get the configuration status history.</span></span>| 
| [<span data-ttu-id="d4bdb-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="d4bdb-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="d4bdb-127">Obtiene la configuración del LCM que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>| 
| [<span data-ttu-id="d4bdb-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="d4bdb-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="d4bdb-129">Inicia la comprobación de coherencia.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-129">Starts the consistency check.</span></span>| 
| [<span data-ttu-id="d4bdb-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="d4bdb-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="d4bdb-131">Quita los archivos de configuración.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-131">Removes the configuration files.</span></span>| 
| [<span data-ttu-id="d4bdb-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="d4bdb-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="d4bdb-133">Llama directamente al método **Get** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-133">Directly calls the **Get** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="d4bdb-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="d4bdb-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="d4bdb-135">Llama directamente al método **Set** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-135">Directly calls the **Set** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="d4bdb-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="d4bdb-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="d4bdb-137">Llama directamente al método **Test** de un recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-137">Directly calls the **Test** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="d4bdb-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="d4bdb-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="d4bdb-139">Revierte una configuración anterior.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-139">Rolls back to a previous configuration.</span></span>| 
| [<span data-ttu-id="d4bdb-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="d4bdb-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="d4bdb-141">Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>| 
| [<span data-ttu-id="d4bdb-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="d4bdb-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="d4bdb-143">Envía el documento de configuración al nodo administrado y usa al agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="d4bdb-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="d4bdb-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="d4bdb-145">Envía el documento de configuración al nodo administrado y empieza a usar el agente de configuración para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="d4bdb-146">Usa GetConfigurationResultOutput para recuperar la salida de resultados.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>| 
| [<span data-ttu-id="d4bdb-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="d4bdb-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="d4bdb-148">Establece la configuración del LCM que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>| 
| [<span data-ttu-id="d4bdb-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="d4bdb-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="d4bdb-150">Detiene la configuración que está en curso.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-150">Stops the configuration that is in progress.</span></span>| 
| [<span data-ttu-id="d4bdb-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="d4bdb-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="d4bdb-152">Envía el documento de configuración al nodo administrado y prueba la configuración actual frente al documento.</span><span class="sxs-lookup"><span data-stu-id="d4bdb-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>| 



 

## <a name="requirements"></a><span data-ttu-id="d4bdb-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d4bdb-153">Requirements</span></span>
------------
><span data-ttu-id="d4bdb-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d4bdb-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d4bdb-155">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d4bdb-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>



 

 



