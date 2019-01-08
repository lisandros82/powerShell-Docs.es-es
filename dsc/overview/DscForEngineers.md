---
ms.date: 10/13/2017
keywords: dsc,powershell,configuration,setup
title: Información general sobre la configuración de estado deseado para ingenieros
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403113"
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="2f9bd-103">Información general sobre la configuración de estado deseado para ingenieros</span><span class="sxs-lookup"><span data-stu-id="2f9bd-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="2f9bd-104">Este documento está pensado para que los equipos de operaciones y desarrolladores comprendan los beneficios de la configuración de estado deseado (DSC) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="2f9bd-105">Para una vista de nivel superior del valor que ofrece DSC, consulte [Información general sobre la configuración de estado deseado para responsables de toma de decisiones](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="2f9bd-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="2f9bd-106">Beneficios de la configuración de estado deseado</span><span class="sxs-lookup"><span data-stu-id="2f9bd-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="2f9bd-107">DSC existe para:</span><span class="sxs-lookup"><span data-stu-id="2f9bd-107">DSC exists to:</span></span>

- <span data-ttu-id="2f9bd-108">Disminuir la complejidad del scripting en Windows</span><span class="sxs-lookup"><span data-stu-id="2f9bd-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="2f9bd-109">Aumentar la velocidad de la iteración</span><span class="sxs-lookup"><span data-stu-id="2f9bd-109">Increase the speed of iteration</span></span>

<span data-ttu-id="2f9bd-110">El concepto de "implementación continua" es cada vez más importante.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="2f9bd-111">La implementación continua se refiere a la capacidad de realizar implementaciones con frecuencia, potencialmente muchas veces al día.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="2f9bd-112">El propósito de estas implementaciones no es corregir algo, sino publicar rápidamente algún contenido.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="2f9bd-113">Al obtener características nuevas durante todo el desarrollo y hasta la operación de la manera más fluida y confiable posible, puede disminuir el tiempo para recuperar la inversión de la nueva lógica de negocios.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="2f9bd-114">La migración hacia la informática en la nube implica una solución de implementación que use un modelo de plantilla "declarativa", donde se declare un entorno de estado final como texto y se publique en un motor de implementación.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="2f9bd-115">Esta técnica de implementación permite realizar un cambio rápido, a gran escala, que resista la amenaza de errores, porque en cualquier momento la implementación se puede repetir de manera coherente para garantizar un estado final.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="2f9bd-116">La creación de las herramientas y los servicios que admiten este estilo de operaciones mediante la automatización es una respuesta a estos cambios.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="2f9bd-117">DSC es una plataforma que ofrece implementación, configuración y cumplimiento declarativos e idempotentes (repetibles).</span><span class="sxs-lookup"><span data-stu-id="2f9bd-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="2f9bd-118">La plataforma de DSC le permite asegurarse de que los componentes del centro de datos tienen la configuración correcta, lo que permite evitar errores y previene costosas fallas en la implementación.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="2f9bd-119">Si las configuraciones de DSC se tratan como parte del código de la aplicación, DSC permite la implementación continua.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="2f9bd-120">La configuración de DSC se debe actualizar como parte de la aplicación, lo que garantiza que el conocimiento necesario para implementar la aplicación siempre esté actualizado y listo para usar.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="2f9bd-121">"Ya tengo PowerShell. ¿Por qué necesito la configuración de estado deseado?"</span><span class="sxs-lookup"><span data-stu-id="2f9bd-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="2f9bd-122">La configuración de DSC separa la intención ("lo que quiero hacer") de la ejecución ("cómo quiero hacerlo").</span><span class="sxs-lookup"><span data-stu-id="2f9bd-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="2f9bd-123">Esto significa que la lógica de ejecución está contenida en los recursos.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="2f9bd-124">No es necesario que los usuarios sepan cómo implementar una característica si hay disponible un recurso de DSC para esa característica.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="2f9bd-125">Esto permite que el usuario se centre en la estructura de la implementación.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="2f9bd-126">Como ejemplo, los scripts de PowerShell deben verse similares al siguiente:</span><span class="sxs-lookup"><span data-stu-id="2f9bd-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="2f9bd-127">Este script es simple, entendible y sencillo.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="2f9bd-128">Sin embargo, si intenta poner ese script en el entorno de producción, se encontrará con varios problemas.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="2f9bd-129">¿Qué sucede si el script se ejecuta dos veces seguidas?</span><span class="sxs-lookup"><span data-stu-id="2f9bd-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="2f9bd-130">¿Qué pasa sin Antonio tenía anteriormente acceso completo al recurso compartido?</span><span class="sxs-lookup"><span data-stu-id="2f9bd-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="2f9bd-131">Para compensar por estos problemas, una versión "real" del script se verá un poco más similar a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="2f9bd-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="2f9bd-132">Este script es más complejo, con un importante control de errores y lógica.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="2f9bd-133">El script es más complejo porque ya no indica lo que desea hacer, sino *cómo hacerlo*.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="2f9bd-134">DSC le permite indicar qué es lo que quiere que se haga y la lógica subyacente se abstrae.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="2f9bd-135">El script tiene un formato limpio y es fácil de leer.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="2f9bd-136">El control de errores y las rutas lógicas siguen presentes en la implementación de [recursos](../resources/resources.md), pero son invisibles para el autor del script.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-136">The logic paths and error handling are still present in the [resource](../resources/resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="2f9bd-137">Separación del entorno de la estructura</span><span class="sxs-lookup"><span data-stu-id="2f9bd-137">Separating Environment from Structure</span></span>

<span data-ttu-id="2f9bd-138">Un patrón común en DevOps es tener varios entornos para la implementación.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="2f9bd-139">Por ejemplo, es posible que haya un entorno "dev" (desarrollo) que se usa para crear un prototipo de código nuevo.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="2f9bd-140">El código del entorno "dev" (desarrollo) pasa a un entorno "test" (prueba), en el que otras personas comprueban la funcionalidad nueva.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="2f9bd-141">Finalmente, el código pasa a "prod" (producción), el entorno de producción del sitio activo.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="2f9bd-142">Las configuraciones de DSC adaptan esta canalización de dev-test-prod a través del uso de los [datos de configuración](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="2f9bd-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](../configurations/configData.md).</span></span>
<span data-ttu-id="2f9bd-143">Esto abstrae aún más la diferencia entre la estructura de la configuración de los nodos que se administran.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="2f9bd-144">Por ejemplo, puede definir una configuración que requiere un servidor SQL Server, un servidor IIS y un servidor de nivel intermedio.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="2f9bd-145">Independientemente de cuáles son los nodos que reciben las distintas partes de esta configuración, siempre existirán estos tres elementos.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="2f9bd-146">Puede usar los datos de configuración para apuntar los tres elementos a la misma máquina en un entorno de desarrollo, separarlos a tres máquinas distintas en un entorno de prueba y, por último, a todos los servidores de producción del entorno de producción.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="2f9bd-147">Para implementar los distintos entornos, puede invocar **Start-DscConfiguration** con los datos de configuración correctos correspondientes al entorno que desea tener como destino.</span><span class="sxs-lookup"><span data-stu-id="2f9bd-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f9bd-148">Véase también</span><span class="sxs-lookup"><span data-stu-id="2f9bd-148">See Also</span></span>

[<span data-ttu-id="2f9bd-149">Configuraciones</span><span class="sxs-lookup"><span data-stu-id="2f9bd-149">Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="2f9bd-150">Datos de configuración</span><span class="sxs-lookup"><span data-stu-id="2f9bd-150">Configuration Data</span></span>](../configurations/configData.md)

[<span data-ttu-id="2f9bd-151">Recursos</span><span class="sxs-lookup"><span data-stu-id="2f9bd-151">Resources</span></span>](../resources/resources.md)
