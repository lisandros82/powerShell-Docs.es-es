---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Procedimientos recomendados del servidor de extracción
ms.openlocfilehash: 5cb47598b11f7884dddf1440cec21afeab49bebb
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417729"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="70533-103">Procedimientos recomendados del servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="70533-103">Pull server best practices</span></span>

<span data-ttu-id="70533-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="70533-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70533-105">El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="70533-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="70533-106">Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](/powershell/scripting/dsc/pull-server/pullserver#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="70533-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](/powershell/scripting/dsc/pull-server/pullserver#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="70533-107">Resumen: El objetivo de este documento es incluir el proceso y la extensibilidad para ayudar a los ingenieros que se estén preparando para la solución.</span><span class="sxs-lookup"><span data-stu-id="70533-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="70533-108">En los detalles se deberían ofrecer procedimientos recomendados identificados por los clientes y después validados por el equipo del producto para garantizar que estén orientados al futuro y se consideren estables.</span><span class="sxs-lookup"><span data-stu-id="70533-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="70533-109">Información del documento</span><span class="sxs-lookup"><span data-stu-id="70533-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="70533-110">Autor</span><span class="sxs-lookup"><span data-stu-id="70533-110">Author</span></span> | <span data-ttu-id="70533-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="70533-111">Michael Greene</span></span>
<span data-ttu-id="70533-112">Revisores</span><span class="sxs-lookup"><span data-stu-id="70533-112">Reviewers</span></span> | <span data-ttu-id="70533-113">Ben Gelens, Ravikanth Chaganti y Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="70533-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="70533-114">Publicado</span><span class="sxs-lookup"><span data-stu-id="70533-114">Published</span></span> | <span data-ttu-id="70533-115">Abril de 2015</span><span class="sxs-lookup"><span data-stu-id="70533-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="70533-116">Resumen</span><span class="sxs-lookup"><span data-stu-id="70533-116">Abstract</span></span>

<span data-ttu-id="70533-117">Este documento está diseñado para proporcionar orientación oficial a cualquiera que esté planeando una implementación de servidor de extracción de la configuración de estado deseado de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70533-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="70533-118">Un servidor de extracción es un servicio sencillo cuya implementación solo debería llevar unos minutos.</span><span class="sxs-lookup"><span data-stu-id="70533-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="70533-119">Aunque en este documento se ofrece orientación técnica de procedimientos que se puede usar durante una implementación, su valor es constituir una referencia de procedimientos recomendados y de aspectos que se deben tener en cuenta antes de implementar.</span><span class="sxs-lookup"><span data-stu-id="70533-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="70533-120">Los lectores deberían tener conocimientos básicos de DSC y de los términos empleados para describir los componentes incluidos en una implementación de DSC.</span><span class="sxs-lookup"><span data-stu-id="70533-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="70533-121">Para más información, vea el tema [Información general sobre la configuración de estado deseado de Windows PowerShell](/powershell/scripting/dsc/overview).</span><span class="sxs-lookup"><span data-stu-id="70533-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview)  topic.</span></span>
<span data-ttu-id="70533-122">Dado que se espera que DSC evolucione al ritmo de la nube, también se espera que la tecnología subyacente, incluido el servidor de extracción, evolucione e incorpore nuevas características.</span><span class="sxs-lookup"><span data-stu-id="70533-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="70533-123">Este documento incluye una tabla de versiones en el apéndice que proporciona referencias a versiones anteriores y a soluciones futuras para fomentar diseños orientados al futuro.</span><span class="sxs-lookup"><span data-stu-id="70533-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="70533-124">Las dos secciones principales de este documento son estas:</span><span class="sxs-lookup"><span data-stu-id="70533-124">The two major sections of this document:</span></span>

- <span data-ttu-id="70533-125">Planeamiento de configuración</span><span class="sxs-lookup"><span data-stu-id="70533-125">Configuration Planning</span></span>
- <span data-ttu-id="70533-126">Guía de instalación</span><span class="sxs-lookup"><span data-stu-id="70533-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="70533-127">Versiones de Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="70533-127">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="70533-128">La información de este documento se aplica a Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="70533-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="70533-129">Aunque no se necesita WMF 5.0 para implementar ni usar un servidor de extracción, la versión 5.0 es el centro de este documento.</span><span class="sxs-lookup"><span data-stu-id="70533-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="70533-130">Configuración de estado deseado de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="70533-130">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="70533-131">Configuración de estado deseado (DSC) es una plataforma de administración que permite implementar y administrar datos de configuración mediante una sintaxis del sector denominada Managed Object Format (MOF) para describir el Modelo de información común (CIM).</span><span class="sxs-lookup"><span data-stu-id="70533-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="70533-132">Existe un proyecto de código abierto, Infraestructura de administración abierta (OMI), para seguir desarrollando estos estándares en plataformas como Linux y sistemas operativos de hardware de red.</span><span class="sxs-lookup"><span data-stu-id="70533-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="70533-133">Para más información, vea la [página de DMTF con los vínculos a las especificaciones de MOF](https://www.dmtf.org/standards/cim) y los [documentos y el código de OMI](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="70533-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="70533-134">Windows PowerShell proporciona un conjunto de extensiones de lenguaje para Configuración de estado deseado que puede usar para crear y administrar configuraciones declarativas.</span><span class="sxs-lookup"><span data-stu-id="70533-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="70533-135">Rol de servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="70533-135">Pull server role</span></span>

<span data-ttu-id="70533-136">Un servidor de extracción proporciona un servicio centralizado para almacenar configuraciones que sean accesibles a los nodos de destino.</span><span class="sxs-lookup"><span data-stu-id="70533-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="70533-137">El rol de servidor de extracción puede implementarse como una instancia de servidor web o como un recurso compartido de archivos SMB.</span><span class="sxs-lookup"><span data-stu-id="70533-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="70533-138">La característica de servidor web incluye una interfaz OData y opcionalmente puede incluir capacidades para que los nodos de destino confirmen el éxito o el error a medida que se apliquen las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="70533-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="70533-139">Esta funcionalidad es útil en entornos donde hay muchos nodos de destino.</span><span class="sxs-lookup"><span data-stu-id="70533-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="70533-140">Después de configurar un nodo de destino (también conocido como cliente) para que apunte al servidor de extracción, se descargan y se aplican los datos de configuración más recientes y los scripts necesarios.</span><span class="sxs-lookup"><span data-stu-id="70533-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="70533-141">Puede ser como una implementación única o como un trabajo recurrente, lo que también convierte al servidor de extracción en un activo importante para administrar el cambio a escala.</span><span class="sxs-lookup"><span data-stu-id="70533-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="70533-142">Para más información, consulte [ Windows PowerShell Desired State Configuration Pull Servers ](/powershell/scripting/dsc/pullServer/pullserver) (Servidores de incorporación de cambios de la configuración de estado deseado de Windows PowerShell) y</span><span class="sxs-lookup"><span data-stu-id="70533-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](/powershell/scripting/dsc/pullServer/pullserver) and</span></span>

<span data-ttu-id="70533-143">[Push and Pull Configuration Modes](/powershell/scripting/dsc/pullServer/pullserver) (Modos de configuración de inserción y extracción).</span><span class="sxs-lookup"><span data-stu-id="70533-143">[Push and Pull Configuration Modes](/powershell/scripting/dsc/pullServer/pullserver).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="70533-144">Planeamiento de configuración</span><span class="sxs-lookup"><span data-stu-id="70533-144">Configuration planning</span></span>

<span data-ttu-id="70533-145">En cualquier implementación de software empresarial hay información que se puede recopilar de antemano para ayudar a planear la arquitectura correcta y a estar preparado para los pasos necesarios de implementación.</span><span class="sxs-lookup"><span data-stu-id="70533-145">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="70533-146">En las secciones siguientes se proporciona información sobre cómo prepararse y sobre las conexiones organizativas que probablemente tengan que realizarse de antemano.</span><span class="sxs-lookup"><span data-stu-id="70533-146">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="70533-147">Requisitos de software</span><span class="sxs-lookup"><span data-stu-id="70533-147">Software requirements</span></span>

<span data-ttu-id="70533-148">La implementación de un servidor de extracción exige la característica Servicio de DSC de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="70533-148">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="70533-149">Esta característica se presentó en Windows Server 2012 y se ha actualizado en las versiones siguientes de Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="70533-149">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="70533-150">Descargas de software</span><span class="sxs-lookup"><span data-stu-id="70533-150">Software downloads</span></span>

<span data-ttu-id="70533-151">Además de instalar el contenido más reciente desde Windows Update, hay dos descargas consideradas procedimientos recomendados para implementar un servidor de extracción de DSC: la versión más reciente de Windows Management Framework y un módulo de DSC para automatizar el aprovisionamiento del servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="70533-151">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="70533-152">WMF</span><span class="sxs-lookup"><span data-stu-id="70533-152">WMF</span></span>

<span data-ttu-id="70533-153">Windows Server 2012 R2 incluye una característica denominada Servicio de DSC.</span><span class="sxs-lookup"><span data-stu-id="70533-153">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="70533-154">La característica Servicio de DSC proporciona la funcionalidad de servidor de extracción, incluidos los archivos binarios que admiten el punto de conexión de OData.</span><span class="sxs-lookup"><span data-stu-id="70533-154">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="70533-155">WMF está incluido en Windows Server y se actualiza a un ritmo ágil entre versiones de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="70533-155">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="70533-156">[Las nuevas versiones de WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) pueden incluir actualizaciones de la característica Servicio de DSC.</span><span class="sxs-lookup"><span data-stu-id="70533-156">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="70533-157">Por esta razón, se recomienda descargar la versión más reciente de WMF y revisar las notas de la versión para determinar si incluye una actualización de dicha característica.</span><span class="sxs-lookup"><span data-stu-id="70533-157">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="70533-158">También debe revisar la sección de notas de la versión que indica si el estado de diseño de un escenario o una actualización es estable o experimental.</span><span class="sxs-lookup"><span data-stu-id="70533-158">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="70533-159">Para permitir un ritmo de versiones ágil, hay características individuales que se pueden declarar estables, lo que indica que están listas para usarse en un entorno de producción, aunque WMF se haya publicado en versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="70533-159">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="70533-160">Otras características que históricamente se han actualizado con las versiones de WMF (vea las Notas de la versión de WMF para obtener más detalles):</span><span class="sxs-lookup"><span data-stu-id="70533-160">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="70533-161">Entorno de scripting integrado (ISE) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="70533-161">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="70533-162">Servicios web de Windows PowerShell (Extensión IIS Management OData)</span><span class="sxs-lookup"><span data-stu-id="70533-162">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="70533-163">Configuración de estado deseado (DSC) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="70533-163">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="70533-164">Administración remota de Windows (WinRM) Instrumental de administración de Windows (WMI)</span><span class="sxs-lookup"><span data-stu-id="70533-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="70533-165">Recurso de DSC</span><span class="sxs-lookup"><span data-stu-id="70533-165">DSC resource</span></span>

<span data-ttu-id="70533-166">Una implementación de servidor de extracción se puede simplificar mediante el aprovisionamiento del servicio con un script de configuración DSC.</span><span class="sxs-lookup"><span data-stu-id="70533-166">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="70533-167">En este documento se incluyen scripts de configuración que pueden usarse para implementar un nodo de servidor listo para producción.</span><span class="sxs-lookup"><span data-stu-id="70533-167">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="70533-168">Para usar los scripts de configuración, se necesita un módulo de DSC que no está incluido en Windows Server.</span><span class="sxs-lookup"><span data-stu-id="70533-168">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="70533-169">El nombre del módulo necesario es **xPSDesiredStateConfiguration**, que incluye el recurso de DSC **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="70533-169">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="70533-170">El módulo xPSDesiredStateConfiguration se puede descargar [aquí](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="70533-170">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="70533-171">Use el cmdlet `Install-Module` del módulo **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="70533-171">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="70533-172">El módulo **PowerShellGet** descargará el módulo en:</span><span class="sxs-lookup"><span data-stu-id="70533-172">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="70533-173">Tarea de planeamiento</span><span class="sxs-lookup"><span data-stu-id="70533-173">Planning task</span></span>|
---|
<span data-ttu-id="70533-174">¿Tiene acceso a los archivos de instalación de Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="70533-174">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="70533-175">¿El entorno de implementación tendrá acceso a Internet para descargar WMF y el módulo desde la galería en línea?</span><span class="sxs-lookup"><span data-stu-id="70533-175">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="70533-176">¿Cómo se instalarán las actualizaciones de seguridad más recientes después de instalar el sistema operativo?</span><span class="sxs-lookup"><span data-stu-id="70533-176">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="70533-177">¿El entorno tendrá acceso a Internet para obtener actualizaciones o tendrá un servidor local de Windows Server Update Services (WSUS)?</span><span class="sxs-lookup"><span data-stu-id="70533-177">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="70533-178">¿Tiene acceso a archivos de instalación de Windows Server que ya incluyen actualizaciones mediante inserción sin conexión?</span><span class="sxs-lookup"><span data-stu-id="70533-178">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="70533-179">Requisitos de hardware</span><span class="sxs-lookup"><span data-stu-id="70533-179">Hardware requirements</span></span>

<span data-ttu-id="70533-180">Las implementaciones de servidor de extracción se admiten tanto en servidores físicos como virtuales.</span><span class="sxs-lookup"><span data-stu-id="70533-180">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="70533-181">Los requisitos de tamaño del servidor de extracción están en línea con los requisitos de Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="70533-181">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="70533-182">CPU: procesador de 64 bits a 1,4 GHz Memoria: 512 MB Espacio en disco: 32 GB Red: adaptador Gigabit Ethernet</span><span class="sxs-lookup"><span data-stu-id="70533-182">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="70533-183">Tarea de planeamiento</span><span class="sxs-lookup"><span data-stu-id="70533-183">Planning task</span></span>|
---|
<span data-ttu-id="70533-184">¿Va a implementar en hardware físico o en una plataforma de virtualización?</span><span class="sxs-lookup"><span data-stu-id="70533-184">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="70533-185">¿Cuál es el proceso para solicitar un nuevo servidor para el entorno de destino?</span><span class="sxs-lookup"><span data-stu-id="70533-185">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="70533-186">¿Cuál es el tiempo de respuesta medio para que un servidor esté disponible?</span><span class="sxs-lookup"><span data-stu-id="70533-186">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="70533-187">¿Qué servidor de tamaño va a solicitar?</span><span class="sxs-lookup"><span data-stu-id="70533-187">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="70533-188">Cuentas</span><span class="sxs-lookup"><span data-stu-id="70533-188">Accounts</span></span>

<span data-ttu-id="70533-189">No hay ningún requisito de cuenta de servicio para implementar una instancia de servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="70533-189">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="70533-190">Pero hay escenarios donde el sitio web podría ejecutarse en el contexto de una cuenta de usuario local.</span><span class="sxs-lookup"><span data-stu-id="70533-190">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="70533-191">Por ejemplo, si hay que acceder a un recurso compartido de almacenamiento de contenido del sitio web y Windows Server o el dispositivo que hospeda el recurso compartido de almacenamiento no están unidos a dominio.</span><span class="sxs-lookup"><span data-stu-id="70533-191">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="70533-192">Registros DNS</span><span class="sxs-lookup"><span data-stu-id="70533-192">DNS records</span></span>

<span data-ttu-id="70533-193">Al configurar clientes para trabajar con un entorno de servidor de extracción, tendrá que usar un nombre de servidor.</span><span class="sxs-lookup"><span data-stu-id="70533-193">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="70533-194">En entornos de prueba, normalmente se usa el nombre de host del servidor o, si la resolución de nombres DNS no está disponible, se puede usar la dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="70533-194">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="70533-195">En entornos de producción o en un entorno de laboratorio que sirve para representar una implementación de producción, el procedimiento recomendado es crear un registro CNAME DNS.</span><span class="sxs-lookup"><span data-stu-id="70533-195">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="70533-196">Un CNAME DNS le permite crear un alias para hacer referencia al registro de host (A).</span><span class="sxs-lookup"><span data-stu-id="70533-196">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="70533-197">El objetivo del registro de nombre adicional es aumentar la flexibilidad por si se necesitara un cambio en el futuro.</span><span class="sxs-lookup"><span data-stu-id="70533-197">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="70533-198">Un CNAME puede ayudar a aislar la configuración del cliente para que los cambios en el entorno de servidor, como la sustitución de un servidor de extracción o la adición de servidores adicionales de extracción, no exijan un cambio correspondiente en la configuración del cliente.</span><span class="sxs-lookup"><span data-stu-id="70533-198">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="70533-199">Al elegir un nombre para el registro DNS, tenga en cuenta la arquitectura de la solución.</span><span class="sxs-lookup"><span data-stu-id="70533-199">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="70533-200">Si usa equilibrio de carga, el certificado empleado para proteger el tráfico a través de HTTPS tendrá que llevar el mismo nombre que el registro DNS.</span><span class="sxs-lookup"><span data-stu-id="70533-200">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="70533-201">Escenario</span><span class="sxs-lookup"><span data-stu-id="70533-201">Scenario</span></span> |<span data-ttu-id="70533-202">Procedimiento recomendado</span><span class="sxs-lookup"><span data-stu-id="70533-202">Best Practice</span></span>
:---|:---
<span data-ttu-id="70533-203">Entorno de prueba</span><span class="sxs-lookup"><span data-stu-id="70533-203">Test Environment</span></span> |<span data-ttu-id="70533-204">Si es posible, reproduzca el entorno de producción planeado.</span><span class="sxs-lookup"><span data-stu-id="70533-204">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="70533-205">Un nombre de host del servidor es adecuado para configuraciones sencillas.</span><span class="sxs-lookup"><span data-stu-id="70533-205">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="70533-206">Si DNS no está disponible, se puede usar una dirección IP en lugar de un nombre de host.</span><span class="sxs-lookup"><span data-stu-id="70533-206">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="70533-207">Implementación de un solo nodo</span><span class="sxs-lookup"><span data-stu-id="70533-207">Single Node Deployment</span></span> |<span data-ttu-id="70533-208">Cree un registro CNAME DNS que apunte al nombre de host del servidor.</span><span class="sxs-lookup"><span data-stu-id="70533-208">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="70533-209">Para más información, vea [Configuring DNS Round Robin in Windows Server (Configuración de round robin de DNS en Windows Server)](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="70533-209">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="70533-210">Tarea de planeamiento</span><span class="sxs-lookup"><span data-stu-id="70533-210">Planning task</span></span>|
---|
<span data-ttu-id="70533-211">¿Sabe con quién tiene que ponerse en contacto para crear y cambiar registros DNS?</span><span class="sxs-lookup"><span data-stu-id="70533-211">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="70533-212">¿Cuál es el tiempo de respuesta medio de una solicitud de registro DNS?</span><span class="sxs-lookup"><span data-stu-id="70533-212">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="70533-213">¿Necesita solicitar registros estáticos de nombre de host (A) para servidores?</span><span class="sxs-lookup"><span data-stu-id="70533-213">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="70533-214">¿Qué va a solicitar como CNAME?</span><span class="sxs-lookup"><span data-stu-id="70533-214">What will you request as a CNAME?</span></span>|
<span data-ttu-id="70533-215">En caso necesario, ¿qué tipo de solución de equilibrio de carga usaría?</span><span class="sxs-lookup"><span data-stu-id="70533-215">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="70533-216">(vea la sección Equilibrio de carga para obtener detalles)</span><span class="sxs-lookup"><span data-stu-id="70533-216">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="70533-217">Infraestructura de clave pública</span><span class="sxs-lookup"><span data-stu-id="70533-217">Public Key Infrastructure</span></span>

<span data-ttu-id="70533-218">Hoy en día la mayoría de las organizaciones exigen que el tráfico de red, especialmente aquel que incluye datos confidenciales tales como la forma en que los servidores están configurados, se valide o se cifre durante el tránsito.</span><span class="sxs-lookup"><span data-stu-id="70533-218">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="70533-219">Aunque es posible implementar un servidor de extracción mediante HTTP, que permite las solicitudes de cliente en texto sin cifrar, el procedimiento recomendado es proteger el tráfico mediante HTTPS.</span><span class="sxs-lookup"><span data-stu-id="70533-219">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="70533-220">El servicio se puede configurar de modo que use HTTPS con un conjunto de parámetros en el recurso de DSC **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="70533-220">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="70533-221">Los requisitos de certificado para proteger el tráfico HTTPS del servidor de extracción no difieren de la protección de cualquier otro sitio web HTTPS.</span><span class="sxs-lookup"><span data-stu-id="70533-221">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="70533-222">La plantilla **servidor web** de Servicios de servidor de certificados de Windows Server satisface las capacidades necesarias.</span><span class="sxs-lookup"><span data-stu-id="70533-222">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="70533-223">Tarea de planeamiento</span><span class="sxs-lookup"><span data-stu-id="70533-223">Planning task</span></span>|
---|
<span data-ttu-id="70533-224">Si las solicitudes de certificado no están automatizadas, ¿con quién tiene que ponerse en contacto para solicitar un certificado?</span><span class="sxs-lookup"><span data-stu-id="70533-224">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="70533-225">¿Cuál es el tiempo de respuesta medio de la solicitud?</span><span class="sxs-lookup"><span data-stu-id="70533-225">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="70533-226">¿Cómo se le transferirá el archivo de certificado?</span><span class="sxs-lookup"><span data-stu-id="70533-226">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="70533-227">¿Cómo se le transferirá la clave privada del certificado?</span><span class="sxs-lookup"><span data-stu-id="70533-227">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="70533-228">¿Cuál es el periodo de expiración predeterminado?</span><span class="sxs-lookup"><span data-stu-id="70533-228">How long is the default expiration time?</span></span>|
<span data-ttu-id="70533-229">¿Ha decidido un nombre DNS para el entorno de servidor de extracción que pueda usar para el nombre de certificado?</span><span class="sxs-lookup"><span data-stu-id="70533-229">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="70533-230">Elección de una arquitectura</span><span class="sxs-lookup"><span data-stu-id="70533-230">Choosing an architecture</span></span>

<span data-ttu-id="70533-231">Un servidor de extracción se puede implementar mediante un servicio web hospedado en IIS o un recurso compartido de archivos SMB.</span><span class="sxs-lookup"><span data-stu-id="70533-231">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="70533-232">En la mayoría de los casos, la opción del servicio web proporcionará mayor flexibilidad.</span><span class="sxs-lookup"><span data-stu-id="70533-232">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="70533-233">No es raro que el tráfico HTTPS atraviese límites de red, mientras que el tráfico SMB se suele filtrar o bloquear entre redes.</span><span class="sxs-lookup"><span data-stu-id="70533-233">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="70533-234">El servicio web también ofrece la opción de incluir un servidor de conformidad o un administrador de informes web (ambos temas se tratarán en una versión futura de este documento) que proporcionan un mecanismo para que los clientes informen del estado a un servidor para una visibilidad centralizada.</span><span class="sxs-lookup"><span data-stu-id="70533-234">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="70533-235">SMB proporciona una opción para entornos donde la directiva determina que no se debe usar un servidor web y para otros requisitos de entorno que convierten a un rol de servidor web en no deseado.</span><span class="sxs-lookup"><span data-stu-id="70533-235">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="70533-236">En cualquier caso, no olvide evaluar los requisitos de firma y cifrado del tráfico.</span><span class="sxs-lookup"><span data-stu-id="70533-236">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="70533-237">HTTPS, firma SMB y directivas IPSEC son opciones que vale la pena tener en cuenta.</span><span class="sxs-lookup"><span data-stu-id="70533-237">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="70533-238">Equilibrio de carga</span><span class="sxs-lookup"><span data-stu-id="70533-238">Load balancing</span></span>

<span data-ttu-id="70533-239">Los clientes que interactúan con el servicio web realizan una solicitud de información que se devuelve en una sola respuesta.</span><span class="sxs-lookup"><span data-stu-id="70533-239">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="70533-240">No se necesitan solicitudes secuenciales, por lo que no es necesario que la plataforma de equilibrio de carga garantice el mantenimiento de las sesiones en un único servidor en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="70533-240">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="70533-241">Tarea de planeamiento</span><span class="sxs-lookup"><span data-stu-id="70533-241">Planning task</span></span>|
---|
<span data-ttu-id="70533-242">¿Qué solución se usará para equilibrar el tráfico entre servidores?</span><span class="sxs-lookup"><span data-stu-id="70533-242">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="70533-243">Si usa un equilibrador de carga de hardware, ¿quién recibirá la solicitud de agregar una nueva configuración al dispositivo?</span><span class="sxs-lookup"><span data-stu-id="70533-243">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="70533-244">¿Cuál es el tiempo de respuesta medio de una solicitud para configurar un nuevo servicio web de equilibrio de carga?</span><span class="sxs-lookup"><span data-stu-id="70533-244">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="70533-245">¿Qué información será necesaria para la solicitud?</span><span class="sxs-lookup"><span data-stu-id="70533-245">What information will be required for the request?</span></span>|
<span data-ttu-id="70533-246">¿Habrá que solicitar una dirección IP adicional o el equipo responsable del equilibrio de carga se ocupará de eso?</span><span class="sxs-lookup"><span data-stu-id="70533-246">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="70533-247">¿Tiene los registros DNS necesarios y el equipo responsable de configurar la solución de equilibrio de carga los necesitará?</span><span class="sxs-lookup"><span data-stu-id="70533-247">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="70533-248">¿La solución de equilibrio de carga exige que el dispositivo administre la PKI o puede equilibrar la carga de tráfico HTTPS siempre que no haya ningún requisito de sesión?</span><span class="sxs-lookup"><span data-stu-id="70533-248">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="70533-249">Preconfiguración de configuraciones y módulos en el servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="70533-249">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="70533-250">Como parte del planeamiento de configuración, debe pensar en los módulos y configuraciones de DSC que hospedará el servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="70533-250">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="70533-251">A efectos del planeamiento de configuración, es importante tener un conocimiento básico de cómo preparar e implementar contenido en un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="70533-251">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="70533-252">En el futuro, esta sección se ampliará y se incluirá en una guía de funcionamiento del servidor de extracción de DSC.</span><span class="sxs-lookup"><span data-stu-id="70533-252">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="70533-253">En esa guía se hablará del proceso cotidiano de administrar módulos y configuraciones a lo largo del tiempo mediante automatización.</span><span class="sxs-lookup"><span data-stu-id="70533-253">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="70533-254">Módulos de DSC</span><span class="sxs-lookup"><span data-stu-id="70533-254">DSC modules</span></span>

<span data-ttu-id="70533-255">Los clientes que soliciten una configuración necesitarán los módulos de DSC necesarios.</span><span class="sxs-lookup"><span data-stu-id="70533-255">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="70533-256">Una funcionalidad del servidor de extracción es automatizar la distribución a petición de módulos de DSC a los clientes.</span><span class="sxs-lookup"><span data-stu-id="70533-256">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="70533-257">Si está implementando un servidor de extracción por primera vez, quizás como laboratorio o prueba de concepto, es probable que vaya a depender de los módulos de DSC que hay disponibles en repositorios públicos, como la Galería de PowerShell, o los repositorios GitHub de PowerShell.org para los módulos de DSC.</span><span class="sxs-lookup"><span data-stu-id="70533-257">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="70533-258">Es fundamental recordar que cualquier módulo descargado de un repositorio público, incluso orígenes en línea de confianza como la Galería de PowerShell, debe ser revisado por alguien con experiencia en PowerShell y conocimiento del entorno donde se van a usar los módulos antes de que estos se empleen en producción.</span><span class="sxs-lookup"><span data-stu-id="70533-258">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="70533-259">Mientras se realiza esta tarea, es buen momento para buscar cualquier carga adicional en el módulo que pueda quitarse, como scripts de ejemplo y documentación.</span><span class="sxs-lookup"><span data-stu-id="70533-259">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="70533-260">Esto reducirá el ancho de banda de red por cliente en la primera solicitud, cuando los módulos se descarguen a través de la red desde el servidor al cliente.</span><span class="sxs-lookup"><span data-stu-id="70533-260">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="70533-261">Cada módulo se debe empaquetar en un formato concreto, un archivo ZIP denominado NombreMódulo_Versión.zip que contiene la carga del módulo.</span><span class="sxs-lookup"><span data-stu-id="70533-261">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="70533-262">Una vez que el archivo se ha copiado en el servidor, se debe crear un archivo de suma de comprobación.</span><span class="sxs-lookup"><span data-stu-id="70533-262">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="70533-263">Cuando los clientes se conectan al servidor, la suma de comprobación se usa para comprobar que el contenido del módulo de DSC no ha cambiado desde que se publicó.</span><span class="sxs-lookup"><span data-stu-id="70533-263">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="70533-264">Tarea de planeamiento</span><span class="sxs-lookup"><span data-stu-id="70533-264">Planning task</span></span>|
---|
<span data-ttu-id="70533-265">Si está planeando un entorno de prueba o laboratorio, ¿qué escenarios es fundamental validar?</span><span class="sxs-lookup"><span data-stu-id="70533-265">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="70533-266">¿Hay módulos disponibles públicamente que contengan recursos para cubrir todo lo que necesita o va a tener que crear sus propios recursos?</span><span class="sxs-lookup"><span data-stu-id="70533-266">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="70533-267">¿El entorno tendrá acceso a Internet para recuperar módulos públicos?</span><span class="sxs-lookup"><span data-stu-id="70533-267">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="70533-268">¿Quién será responsable de revisar los módulos de DSC?</span><span class="sxs-lookup"><span data-stu-id="70533-268">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="70533-269">Si está planeando un entorno de producción, ¿qué usará como repositorio local para almacenar los módulos de DSC?</span><span class="sxs-lookup"><span data-stu-id="70533-269">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="70533-270">¿Habrá un equipo central que acepte los módulos de DSC de los equipos solicitantes?</span><span class="sxs-lookup"><span data-stu-id="70533-270">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="70533-271">¿Cuál será el proceso?</span><span class="sxs-lookup"><span data-stu-id="70533-271">What will the process be?</span></span>|
<span data-ttu-id="70533-272">¿Se automatizará el empaquetado, la copia y la creación de una suma de comprobación para los módulos de DSC listos para producción que van al servidor desde el repositorio de origen?</span><span class="sxs-lookup"><span data-stu-id="70533-272">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="70533-273">¿El equipo también será responsable de administrar la plataforma de automatización?</span><span class="sxs-lookup"><span data-stu-id="70533-273">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="70533-274">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="70533-274">DSC configurations</span></span>

<span data-ttu-id="70533-275">El fin de un servidor de extracción es proporcionar un mecanismo centralizado para distribuir configuraciones DSC a nodos cliente.</span><span class="sxs-lookup"><span data-stu-id="70533-275">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="70533-276">Las configuraciones se almacenan en el servidor como documentos MOF.</span><span class="sxs-lookup"><span data-stu-id="70533-276">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="70533-277">Cada documento tendrá como nombre un **GUID** único.</span><span class="sxs-lookup"><span data-stu-id="70533-277">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="70533-278">Cuando se configuran los clientes para conectar con un servidor de extracción, se les da el **GUID** de la configuración que deben solicitar.</span><span class="sxs-lookup"><span data-stu-id="70533-278">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="70533-279">Este sistema para hacer referencia a las configuraciones por **GUID** garantiza la exclusividad global y es flexible, de modo que una configuración se puede aplicar con granularidad por nodo o como una configuración de rol que abarca varios servidores que deben tener configuraciones idénticas.</span><span class="sxs-lookup"><span data-stu-id="70533-279">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="70533-280">GUID</span><span class="sxs-lookup"><span data-stu-id="70533-280">Guids</span></span>

<span data-ttu-id="70533-281">El planeamiento de **GUID** de configuración merece atención adicional cuando se piensa en una implementación de servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="70533-281">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="70533-282">No hay ningún requisito específico para cómo administrar **GUID** y el proceso es probable que sea único para cada entorno.</span><span class="sxs-lookup"><span data-stu-id="70533-282">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="70533-283">El proceso puede ir desde sencillo a complejo: un archivo CSV almacenado centralmente, una tabla SQL simple, una CMDB o una solución compleja que exija integración con otra herramienta o solución de software.</span><span class="sxs-lookup"><span data-stu-id="70533-283">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="70533-284">Hay dos enfoques generales:</span><span class="sxs-lookup"><span data-stu-id="70533-284">There are two general approaches:</span></span>

- <span data-ttu-id="70533-285">**Asignar GUID por servidor**: ofrece una forma de garantizar que cada configuración de servidor se controla individualmente.</span><span class="sxs-lookup"><span data-stu-id="70533-285">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="70533-286">Esto proporciona un nivel de precisión en torno a las actualizaciones y puede funcionar bien en entornos con pocos servidores.</span><span class="sxs-lookup"><span data-stu-id="70533-286">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="70533-287">**Asignar GUID por rol de servidor**: todos los servidores que realizan la misma función, como los servidores web, usan el mismo GUID para hacer referencia a los datos de configuración necesarios.</span><span class="sxs-lookup"><span data-stu-id="70533-287">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="70533-288">Tenga en cuenta que si hay muchos servidores que compartan el mismo GUID, todos ellos se actualizarían simultáneamente cuando cambiara la configuración.</span><span class="sxs-lookup"><span data-stu-id="70533-288">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="70533-289">El GUID debería considerarse información confidencial, porque podría ser aprovechado por alguien con malas intenciones para obtener datos sobre cómo están implementados y configurados los servidores en el entorno.</span><span class="sxs-lookup"><span data-stu-id="70533-289">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="70533-290">Para más información, vea [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/) (Asignación segura de GUID en modo de extracción de la configuración de estado deseado de PowerShell).</span><span class="sxs-lookup"><span data-stu-id="70533-290">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="70533-291">Tarea de planeamiento</span><span class="sxs-lookup"><span data-stu-id="70533-291">Planning task</span></span>|
---|
<span data-ttu-id="70533-292">¿Quién será responsable de copiar las configuraciones en la carpeta del servidor de extracción cuando estén listas?</span><span class="sxs-lookup"><span data-stu-id="70533-292">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="70533-293">Si un equipo solicitante crea configuraciones, ¿cuál será el proceso para entregarlas?</span><span class="sxs-lookup"><span data-stu-id="70533-293">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="70533-294">¿Aprovechará un repositorio para almacenar las configuraciones a medida que se crean para todos los equipos?</span><span class="sxs-lookup"><span data-stu-id="70533-294">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="70533-295">¿Automatizará el proceso de copiar las configuraciones en el servidor y de crear una suma de comprobación cuando estén listas?</span><span class="sxs-lookup"><span data-stu-id="70533-295">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="70533-296">¿Cómo se asignarán los GUID a los servidores o roles y dónde se almacenarán?</span><span class="sxs-lookup"><span data-stu-id="70533-296">How will you map Guids to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="70533-297">¿Qué proceso usará para configurar equipos cliente y cómo se integrará con el proceso para crear y almacenar GUID de configuración?</span><span class="sxs-lookup"><span data-stu-id="70533-297">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="70533-298">Guía de instalación</span><span class="sxs-lookup"><span data-stu-id="70533-298">Installation Guide</span></span>

<span data-ttu-id="70533-299">*Los scripts de este documento son ejemplos estables. Revise siempre los scripts detenidamente antes de ejecutarlos en un entorno de producción.*</span><span class="sxs-lookup"><span data-stu-id="70533-299">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="70533-300">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="70533-300">Prerequisites</span></span>

<span data-ttu-id="70533-301">Para comprobar la versión de PowerShell del servidor, use el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="70533-301">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="70533-302">Si es posible, actualice a la versión más reciente de Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="70533-302">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="70533-303">Luego, ejecute el módulo `xPsDesiredStateConfiguration` con el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="70533-303">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="70533-304">El comando le pedirá su aprobación antes de descargar el módulo.</span><span class="sxs-lookup"><span data-stu-id="70533-304">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="70533-305">Scripts de instalación y configuración</span><span class="sxs-lookup"><span data-stu-id="70533-305">Installation and configuration scripts</span></span>

<span data-ttu-id="70533-306">El mejor método para implementar un servidor de extracción de DSC es usar un script de configuración de DSC.</span><span class="sxs-lookup"><span data-stu-id="70533-306">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="70533-307">En este documento se presentan los scripts incluyendo tanto la configuración básica que configuraría solo el servicio web de DSC como la configuración avanzada que configuraría un servidor descentralizado de Windows Server, incluido un servicio web de DSC.</span><span class="sxs-lookup"><span data-stu-id="70533-307">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="70533-308">Nota:  De momento, el módulo `xPSDesiredStateConfiguration` de DSC exige que la configuración regional del servidor sea EN-US.</span><span class="sxs-lookup"><span data-stu-id="70533-308">Note:  Currently the `xPSDesiredStateConfiguration` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="70533-309">Configuración básica de Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="70533-309">Basic configuration for Windows Server 2012</span></span>

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="70533-310">Configuración avanzada de Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="70533-310">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="70533-311">Comprobar funcionalidad de servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="70533-311">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="70533-312">Configurar clientes</span><span class="sxs-lookup"><span data-stu-id="70533-312">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="70533-313">Referencias, fragmentos de código y ejemplos adicionales</span><span class="sxs-lookup"><span data-stu-id="70533-313">Additional references, snippets, and examples</span></span>

<span data-ttu-id="70533-314">En este ejemplo se muestra cómo iniciar manualmente una conexión de cliente (necesita WMF5) para realizar pruebas.</span><span class="sxs-lookup"><span data-stu-id="70533-314">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="70533-315">Se usa el cmdlet [DnsServerResourceRecordName agregar](http://bit.ly/1G1H31L) para agregar un registro CNAME de tipo a una zona DNS.</span><span class="sxs-lookup"><span data-stu-id="70533-315">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="70533-316">La función de PowerShell para [crear una suma de comprobación y publicar el MOF de DSC en el servidor de extracción SMB](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) genera automáticamente la suma de comprobación necesaria y, luego, copia los archivos de suma de comprobación y de configuración MOF en el servidor de extracción SMB.</span><span class="sxs-lookup"><span data-stu-id="70533-316">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="70533-317">Apéndice - Conceptos básicos de tipos de archivos de datos del servicio ODATA</span><span class="sxs-lookup"><span data-stu-id="70533-317">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="70533-318">Se almacena un archivo de datos para crear información durante la implementación de un servidor de extracción que incluye el servicio web OData.</span><span class="sxs-lookup"><span data-stu-id="70533-318">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="70533-319">El tipo de archivo depende del sistema operativo, como se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="70533-319">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="70533-320">**Windows Server 2012** El tipo de archivo siempre será .mdb.</span><span class="sxs-lookup"><span data-stu-id="70533-320">**Windows Server 2012** The file type will always be   .mdb</span></span>
- <span data-ttu-id="70533-321">**Windows Server 2012 R2** El tipo de archivo será .edb a menos que se especifique un tipo .mdb en la configuración.</span><span class="sxs-lookup"><span data-stu-id="70533-321">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="70533-322">En el [script de ejemplo avanzado](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) para instalar un servidor de extracción, también encontrará un ejemplo de cómo controlar automáticamente la configuración del archivo web.config para evitar cualquier posibilidad de error causado por el tipo de archivo.</span><span class="sxs-lookup"><span data-stu-id="70533-322">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
