---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Creación de DSC avanzada para composición y colaboración
ms.openlocfilehash: 3e40ba94de0a53c1c9663553c4ec443b5e0df3fd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681805"
---
# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a><span data-ttu-id="d537b-103">Creación de DSC avanzada para composición y colaboración</span><span class="sxs-lookup"><span data-stu-id="d537b-103">Advanced DSC Authoring for Composition and Collaboration</span></span>

<span data-ttu-id="d537b-104">En este artículo se describen los tipos de enfoques que hay disponibles para combinar configuraciones y recursos.</span><span class="sxs-lookup"><span data-stu-id="d537b-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="d537b-105">El objetivo de cada escenario es el mismo: reducir la complejidad cuando se prefiere que varias configuraciones alcancen un estado final de implementación de servidor.</span><span class="sxs-lookup"><span data-stu-id="d537b-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="d537b-106">Un ejemplo de esto sería cuando varios equipos contribuyen al resultado de una implementación de servidor, como cuando un propietario de la aplicación mantiene el estado de la aplicación y un equipo central libera los cambios realizados en las líneas base de seguridad.</span><span class="sxs-lookup"><span data-stu-id="d537b-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="d537b-107">Aquí se detallan los matices de cada enfoque, incluidas las ventajas y los riesgos.</span><span class="sxs-lookup"><span data-stu-id="d537b-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Canalización](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="d537b-109">Tipos de técnicas de creación colaborativa</span><span class="sxs-lookup"><span data-stu-id="d537b-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="d537b-110">Hay dos soluciones integradas en el Administrador de configuración local para habilitar este concepto:</span><span class="sxs-lookup"><span data-stu-id="d537b-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="d537b-111">Concepto</span><span class="sxs-lookup"><span data-stu-id="d537b-111">Concept</span></span> | <span data-ttu-id="d537b-112">Información detallada</span><span class="sxs-lookup"><span data-stu-id="d537b-112">Detailed Information</span></span>
|-|-
| <span data-ttu-id="d537b-113">Configuraciones parciales</span><span class="sxs-lookup"><span data-stu-id="d537b-113">Partial Configurations</span></span> | [<span data-ttu-id="d537b-114">Documentación</span><span class="sxs-lookup"><span data-stu-id="d537b-114">Documentation</span></span>](../pull-server/partialConfigs.md)
| <span data-ttu-id="d537b-115">Recursos compuestos</span><span class="sxs-lookup"><span data-stu-id="d537b-115">Composite Resources</span></span> | [<span data-ttu-id="d537b-116">Documentación</span><span class="sxs-lookup"><span data-stu-id="d537b-116">Documentation</span></span>](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="d537b-117">Comprender el impacto de cada enfoque</span><span class="sxs-lookup"><span data-stu-id="d537b-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="d537b-118">Cualquiera de estas soluciones pueden usarse para administrar el resultado de una implementación de servidor.</span><span class="sxs-lookup"><span data-stu-id="d537b-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="d537b-119">Pero hay una diferencia importante en el impacto del uso de cada enfoque.</span><span class="sxs-lookup"><span data-stu-id="d537b-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="d537b-120">Configuraciones parciales</span><span class="sxs-lookup"><span data-stu-id="d537b-120">Partial Configurations</span></span>

<span data-ttu-id="d537b-121">Al usar configuraciones parciales, el Administrador de configuración local se configura para administrar varias configuraciones de forma independiente.</span><span class="sxs-lookup"><span data-stu-id="d537b-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="d537b-122">Las configuraciones se compilan de forma independiente y luego se asignan al nodo.</span><span class="sxs-lookup"><span data-stu-id="d537b-122">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="d537b-123">Para ello hace falta que el Administrador de configuración local esté configurado con antelación con el nombre de cada configuración.</span><span class="sxs-lookup"><span data-stu-id="d537b-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](../images/PartialConfiguration.jpg)

<span data-ttu-id="d537b-125">Las configuraciones parciales proporcionan a dos o más equipos el control total de la configuración de un servidor, a menudo sin la ventaja de comunicación o colaboración.</span><span class="sxs-lookup"><span data-stu-id="d537b-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="d537b-126">Los clientes nos han informado de que esto puede dar lugar a conflictos de recursos, reemplazos involuntarios y, en última instancia, la pérdida del verdadero control de la configuración del recurso.</span><span class="sxs-lookup"><span data-stu-id="d537b-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="d537b-127">Los clientes también nos han informado de que cuando se usa este modelo, los cambios de configuración de los equipos de control no suelen someterse pruebas mediante una canalización de publicación, lo que genera resultados inesperados en la producción.</span><span class="sxs-lookup"><span data-stu-id="d537b-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="d537b-128">**Es fundamental que se use una sola canalización para evaluar la publicación de todos los cambios en los servidores.**</span><span class="sxs-lookup"><span data-stu-id="d537b-128">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="d537b-129">En la ilustración de abajo, el equipo B envía su configuración parcial al equipo A. Después, el equipo A realiza sus pruebas en un servidor con las dos configuraciones aplicadas.</span><span class="sxs-lookup"><span data-stu-id="d537b-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="d537b-130">En este modelo, solo una entidad tiene permiso para realizar cambios en producción.</span><span class="sxs-lookup"><span data-stu-id="d537b-130">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

<span data-ttu-id="d537b-132">Cuando se pide al equipo B que realice cambios, este debe enviar una solicitud de incorporación de cambios en el entorno de control de código fuente del equipo A.</span><span class="sxs-lookup"><span data-stu-id="d537b-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="d537b-133">Después, el equipo A revisa los cambios mediante la automatización de pruebas y envía la configuración a producción cuando está seguro de que los cambios no provocarán errores en las aplicaciones o los servicios hospedados por el servidor.</span><span class="sxs-lookup"><span data-stu-id="d537b-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="d537b-134">Recursos compuestos</span><span class="sxs-lookup"><span data-stu-id="d537b-134">Composite Resources</span></span>

<span data-ttu-id="d537b-135">Un recurso compuesto es simplemente una configuración de DSC empaquetada como un recurso.</span><span class="sxs-lookup"><span data-stu-id="d537b-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="d537b-136">No hay ningún requisito especial de configurar el Administrador de configuración local para que acepte los recursos compuestos.</span><span class="sxs-lookup"><span data-stu-id="d537b-136">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="d537b-137">Los recursos se usan dentro de una configuración nueva y una sola compilación da como resultado un archivo MOF.</span><span class="sxs-lookup"><span data-stu-id="d537b-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](../images/CompositeResource.jpg)

<span data-ttu-id="d537b-139">Hay dos escenarios comunes para los recursos compuestos.</span><span class="sxs-lookup"><span data-stu-id="d537b-139">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="d537b-140">El primero consiste en reducir la complejidad y conceptos abstractos únicos.</span><span class="sxs-lookup"><span data-stu-id="d537b-140">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="d537b-141">El segundo es permitir que las líneas base se empaqueten para que un equipo de aplicación pueda implementar de forma segura a través de su canalización de versiones en producción una vez que se hayan superado todas las pruebas.</span><span class="sxs-lookup"><span data-stu-id="d537b-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

<span data-ttu-id="d537b-142">Los recursos compuestos promueven la composición y la colaboración mediante una canalización durante la compilación de madurez operacional</span><span class="sxs-lookup"><span data-stu-id="d537b-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="d537b-143">Es posible que ya esté usando recursos compuestos sin darse cuenta.</span><span class="sxs-lookup"><span data-stu-id="d537b-143">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="d537b-144">Un ejemplo de ello es **ServiceSet**.</span><span class="sxs-lookup"><span data-stu-id="d537b-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="d537b-145">Este recurso administra el estado de varios servicios de Windows sin enumerarlos individualmente.</span><span class="sxs-lookup"><span data-stu-id="d537b-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="d537b-146">La propiedad Name acepta una matriz de cadenas para proporcionar el nombre de cada servicio.</span><span class="sxs-lookup"><span data-stu-id="d537b-146">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="d537b-147">Cuando se compile la configuración, el MOF contendrá una sección Service única para cada uno de los nombres pasados a ServiceSet.</span><span class="sxs-lookup"><span data-stu-id="d537b-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="d537b-148">Las organizaciones pueden tener "agentes" o "middleware" que debe instalarse en todos los servidores.</span><span class="sxs-lookup"><span data-stu-id="d537b-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="d537b-149">Un recurso compuesto es la mejor solución para administrar las dependencias, la instalación y la configuración de dichas herramientas y utilidades.</span><span class="sxs-lookup"><span data-stu-id="d537b-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="d537b-150">La persona o el equipo responsable de las soluciones que abarcan varios servidores crea una configuración que contiene sus requisitos.</span><span class="sxs-lookup"><span data-stu-id="d537b-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="d537b-151">Después, se puede empaquetar la configuración como un recurso compuesto mediante las instrucciones proporcionadas en la documentación del recurso compuesto.</span><span class="sxs-lookup"><span data-stu-id="d537b-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="d537b-152">Por último, el nuevo recurso compuesto se debe publicar en una ubicación como un recurso compartido de archivos o una fuente de NuGet donde los equipos de la aplicación puedan usarlo en sus configuraciones.</span><span class="sxs-lookup"><span data-stu-id="d537b-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="d537b-153">Cada vez que el equipo publica una nueva versión, aumentaría el número de versión en el manifiesto del módulo para su recurso compuesto.</span><span class="sxs-lookup"><span data-stu-id="d537b-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="d537b-154">Los equipos de la aplicación incluyen el recurso compuesto en la configuración que crean para administrar las dependencias de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d537b-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="d537b-155">Cuando los equipos de operaciones/seguridad publican una nueva versión de sus recursos, notifican a los equipos de la aplicación de que hay un cambio nuevo.</span><span class="sxs-lookup"><span data-stu-id="d537b-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="d537b-156">Los equipos de la aplicación podrán desencadenar una versión para producción, donde el único cambio son las líneas base.</span><span class="sxs-lookup"><span data-stu-id="d537b-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="d537b-157">Pero esto ofrece una oportunidad de evaluar el impacto en las aplicaciones antes de correr el riesgo de una interrupción del servicio.</span><span class="sxs-lookup"><span data-stu-id="d537b-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="d537b-158">Nota: Entre los comentarios que hemos recibido sobre el uso de recursos compuestos se criticaba que para hacer cambios hacía falta compilar y publicar un nuevo MOF.</span><span class="sxs-lookup"><span data-stu-id="d537b-158">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="d537b-159">Esto es así por diseño.</span><span class="sxs-lookup"><span data-stu-id="d537b-159">This is by design.</span></span>
<span data-ttu-id="d537b-160">Cada nueva versión de configuración debe incluir una referencia estática a una versión específica de cada recurso, y debe ser validada mediante pruebas antes de alcanzar los nodos del servidor de producción.</span><span class="sxs-lookup"><span data-stu-id="d537b-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="d537b-161">El proceso de probar y publicar cambios desde el control de código fuente crea un entorno seguro para publicar cambios en lotes pequeños pero frecuentes.</span><span class="sxs-lookup"><span data-stu-id="d537b-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="d537b-162">Si quiere saber más sobre el uso de canalizaciones de versiones para administrar la infraestructura básica, vea las notas del producto: [Modelo de canalización de versiones](../further-reading/whitepapers.md).</span><span class="sxs-lookup"><span data-stu-id="d537b-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
