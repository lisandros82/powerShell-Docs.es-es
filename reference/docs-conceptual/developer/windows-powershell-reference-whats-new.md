---
title: 'Referencia de Windows PowerShell: novedades'
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366094"
---
# <a name="whats-new"></a><span data-ttu-id="06dbc-102">Novedades</span><span class="sxs-lookup"><span data-stu-id="06dbc-102">What's New</span></span>

<span data-ttu-id="06dbc-103">Windows PowerShell 2,0 proporciona las siguientes características nuevas para su uso al escribir cmdlets, proveedores y aplicaciones host.</span><span class="sxs-lookup"><span data-stu-id="06dbc-103">Windows PowerShell 2.0 provides the following new features for use when writing cmdlets, providers, and host applications.</span></span>

## <a name="modules"></a><span data-ttu-id="06dbc-104">Módulos</span><span class="sxs-lookup"><span data-stu-id="06dbc-104">Modules</span></span>

<span data-ttu-id="06dbc-105">Ahora puede empaquetar y distribuir soluciones de Windows PowerShell mediante el uso de módulos.</span><span class="sxs-lookup"><span data-stu-id="06dbc-105">You can now package and distribute Windows PowerShell solutions by using modules.</span></span> <span data-ttu-id="06dbc-106">Los módulos le permiten particionar, organizar y abstraer el código de Windows PowerShell en unidades reutilizables independientes.</span><span class="sxs-lookup"><span data-stu-id="06dbc-106">Modules allow you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="06dbc-107">Para obtener más información sobre los módulos, consulte escribir un módulo de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06dbc-107">For more information about modules, see Writing a Windows PowerShell Module.</span></span>

## <a name="the-powershell-class"></a><span data-ttu-id="06dbc-108">La clase de PowerShell</span><span class="sxs-lookup"><span data-stu-id="06dbc-108">The PowerShell class</span></span>

<span data-ttu-id="06dbc-109">La clase de PowerShell proporciona una solución más sencilla para crear aplicaciones, denominadas aplicaciones host, que ejecutan comandos mediante programación.</span><span class="sxs-lookup"><span data-stu-id="06dbc-109">The PowerShell class provides a simpler solution for creating applications, referred to as host applications, that programmatically run commands.</span></span> <span data-ttu-id="06dbc-110">Esta clase permite crear una canalización de comandos, especificar el espacio de ejecución que se usa para ejecutar los comandos y especificar invocar los comandos de forma sincrónica o asincrónica.</span><span class="sxs-lookup"><span data-stu-id="06dbc-110">This class allows you to create a pipeline of commands, specify the runspace that is used to run the commands, and specify invoking the commands synchronously or asynchronously.</span></span>

## <a name="the-runspacepool-class"></a><span data-ttu-id="06dbc-111">La clase RunspacePool</span><span class="sxs-lookup"><span data-stu-id="06dbc-111">The RunspacePool class</span></span>

<span data-ttu-id="06dbc-112">Los grupos de espacio de ejecución permiten crear varios espacios de ejecución mediante una sola llamada.</span><span class="sxs-lookup"><span data-stu-id="06dbc-112">Runspace pools allow you to create multiple runspaces by using a single call.</span></span> <span data-ttu-id="06dbc-113">El método CreateRunspacePool proporciona varias sobrecargas que se pueden usar para crear espacios de inicio que tienen las mismas características, como el mismo host, el estado de sesión inicial y la información de conexión.</span><span class="sxs-lookup"><span data-stu-id="06dbc-113">The CreateRunspacePool method provides several overloads that can be used to create runspaces that have the same features, such as the same host, initial session state, and connection information.</span></span>

## <a name="the-initialsessionstate-class"></a><span data-ttu-id="06dbc-114">La clase InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="06dbc-114">The InitialSessionState class</span></span>

<span data-ttu-id="06dbc-115">La clase InitialSessionState permite crear una configuración de estado de sesión que se utiliza cuando se abre un espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="06dbc-115">The InitialSessionState class allows you to create a session state configuration that is used when a runspace is opened.</span></span> <span data-ttu-id="06dbc-116">Puede crear una configuración personalizada, una configuración predeterminada que incluye los comandos proporcionados por mshshort y una configuración cuyos comandos están restringidos en función de las capacidades de la sesión.</span><span class="sxs-lookup"><span data-stu-id="06dbc-116">You can create a custom configuration, a default configuration that includes the commands provided by mshshort, and a configuration whose commands are restricted based on the capabilities of the session.</span></span>

## <a name="remote-runspaces"></a><span data-ttu-id="06dbc-117">Espacios de control remotos</span><span class="sxs-lookup"><span data-stu-id="06dbc-117">Remote runspaces</span></span>

<span data-ttu-id="06dbc-118">Ahora puede crear espacios de ejecución que se puedan abrir en equipos remotos, lo que le permite ejecutar comandos en el equipo remoto y recopilar los resultados de forma local.</span><span class="sxs-lookup"><span data-stu-id="06dbc-118">You can now create runspaces that can be opened on remote computers, allowing you to run commands on the remote machine and collect the results locally.</span></span> <span data-ttu-id="06dbc-119">Para crear un espacio de ejecución remoto, debe especificar información sobre la conexión remota al crear el espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="06dbc-119">To create a remote runspace, you must specify information about the remote connection when creating the runspace.</span></span> <span data-ttu-id="06dbc-120">Vea los métodos CreateRunspace y CreateRunspacePool para obtener ejemplos.</span><span class="sxs-lookup"><span data-stu-id="06dbc-120">See the CreateRunspace and CreateRunspacePool methods for examples.</span></span> <span data-ttu-id="06dbc-121">La información de conexión se define mediante la clase RunspaceConnectionInfo.</span><span class="sxs-lookup"><span data-stu-id="06dbc-121">The connection information is defined by the RunspaceConnectionInfo class.</span></span>

## <a name="private-runspace-elements"></a><span data-ttu-id="06dbc-122">Elementos Private runspace</span><span class="sxs-lookup"><span data-stu-id="06dbc-122">Private runspace elements</span></span>

<span data-ttu-id="06dbc-123">Ahora puede crear espacios de espacios cuyos elementos sean públicos o privados.</span><span class="sxs-lookup"><span data-stu-id="06dbc-123">You can now create runspaces whose elements are public or private.</span></span> <span data-ttu-id="06dbc-124">Esto permite crear espacios de ejecución cuyos elementos están disponibles en el espacio de ejecución, pero no están disponibles para el usuario.</span><span class="sxs-lookup"><span data-stu-id="06dbc-124">This allows you to create runspaces whose elements are available to the runspace, but are not available to the user.</span></span> <span data-ttu-id="06dbc-125">Vea la clase ConstrainedSessionStateEntry para averiguar qué elementos del espacio de ejecución se pueden convertir en privados.</span><span class="sxs-lookup"><span data-stu-id="06dbc-125">See the ConstrainedSessionStateEntry class to find out which elements of the runspace can be made private.</span></span>

## <a name="runspace-threading-modes-and-apartment-state"></a><span data-ttu-id="06dbc-126">Modos de subproceso de espacio de ejecución y estado de apartamento</span><span class="sxs-lookup"><span data-stu-id="06dbc-126">Runspace threading modes and apartment state</span></span>

<span data-ttu-id="06dbc-127">Ahora puede especificar cómo se crean y se usan los subprocesos cuando se ejecutan comandos en un espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="06dbc-127">You can now specify how threads are created and used when running commands in a runspace.</span></span> <span data-ttu-id="06dbc-128">Vea las propiedades System. Management. Automation. espacios de ejecución. ThreadOptions y System. Management. Automation. runspace. RunspacePool. ThreadOptions.</span><span class="sxs-lookup"><span data-stu-id="06dbc-128">See the System.Management.Automation.Runspaces.Runspace.ThreadOptions and System.Management.Automation.Runspaces.RunspacePool.ThreadOptions properties.</span></span>

<span data-ttu-id="06dbc-129">Ahora puede obtener el estado de apartamento de los subprocesos que se usan para ejecutar comandos en un espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="06dbc-129">You can now get the apartment state of the threads that are used to run commands in a runspace.</span></span> <span data-ttu-id="06dbc-130">Vea las propiedades System. Management. Automation. Runspace. Runspace. ApartmentState y System. Management. Automation. runspace. RunspacePool. ApartmentState.</span><span class="sxs-lookup"><span data-stu-id="06dbc-130">See the System.Management.Automation.Runspaces.Runspace.ApartmentState and System.Management.Automation.Runspaces.RunspacePool.ApartmentState properties.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="06dbc-131">Cmdlets de transacciones</span><span class="sxs-lookup"><span data-stu-id="06dbc-131">Transaction cmdlets</span></span>

<span data-ttu-id="06dbc-132">Ahora puede crear cmdlets que se pueden usar dentro de una transacción.</span><span class="sxs-lookup"><span data-stu-id="06dbc-132">You can now create cmdlets that can be used within a transaction.</span></span> <span data-ttu-id="06dbc-133">Cuando se usa un cmdlet en una transacción, sus acciones son temporales y pueden ser aceptadas o rechazadas por los cmdlets de transacciones proporcionados por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06dbc-133">When a cmdlet is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="06dbc-134">Para obtener más información acerca de las transacciones, consulte How to Support Transactions.</span><span class="sxs-lookup"><span data-stu-id="06dbc-134">For more information about transactions, see How to Support Transactions.</span></span>

## <a name="transaction-provider"></a><span data-ttu-id="06dbc-135">Proveedor de transacciones</span><span class="sxs-lookup"><span data-stu-id="06dbc-135">Transaction provider</span></span>

<span data-ttu-id="06dbc-136">Ahora puede crear proveedores que se pueden usar dentro de una transacción.</span><span class="sxs-lookup"><span data-stu-id="06dbc-136">You can now create providers that can be used within a transaction.</span></span> <span data-ttu-id="06dbc-137">Similar a los cmdlets, cuando un proveedor se usa en una transacción, sus acciones son temporales y pueden ser aceptadas o rechazadas por los cmdlets de transacciones proporcionados por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06dbc-137">Similar to cmdlets, when a provider is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="06dbc-138">Para obtener más información sobre cómo especificar la compatibilidad con la transacción en una clase de proveedor, vea la propiedad System. Management. Automation. Provider. CmdletProviderAttribute. ProviderCapabilities.</span><span class="sxs-lookup"><span data-stu-id="06dbc-138">For more information about specifying support for transaction within a provider class, see the System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities property.</span></span>

## <a name="job-cmdlets"></a><span data-ttu-id="06dbc-139">Cmdlets de trabajo</span><span class="sxs-lookup"><span data-stu-id="06dbc-139">Job cmdlets</span></span>

<span data-ttu-id="06dbc-140">Ahora puede escribir cmdlets que pueden realizar su acción como un trabajo.</span><span class="sxs-lookup"><span data-stu-id="06dbc-140">You can now write cmdlets that can perform their action as a job.</span></span> <span data-ttu-id="06dbc-141">Estos trabajos se ejecutan en segundo plano sin interactuar con la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="06dbc-141">These jobs are run in the background without interacting with the current session.</span></span> <span data-ttu-id="06dbc-142">Para obtener más información acerca de cómo Windows PowerShell admite trabajos, consulte trabajos en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="06dbc-142">For more information about how Windows PowerShell supports jobs, see Background Jobs.</span></span>

## <a name="cmdlet-output-types"></a><span data-ttu-id="06dbc-143">Tipos de salida de cmdlet</span><span class="sxs-lookup"><span data-stu-id="06dbc-143">Cmdlet output types</span></span>

<span data-ttu-id="06dbc-144">Ahora puede especificar los tipos de .NET Framework devueltos por los cmdlets declarando el atributo OutputType al escribir los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="06dbc-144">You can now specify the .NET Framework types that are returned by your cmdlets by declaring the OutputType attribute when writing your cmdlets.</span></span> <span data-ttu-id="06dbc-145">Esto permitirá que otros usuarios determinen qué tipo de objetos devuelve un cmdlet examinando la propiedad OutputType del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="06dbc-145">This will allow others to determine what type of objects are returned by a cmdlet by looking at the OutputType property of the cmdlet.</span></span>

## <a name="event-support"></a><span data-ttu-id="06dbc-146">Compatibilidad con eventos</span><span class="sxs-lookup"><span data-stu-id="06dbc-146">Event support</span></span>

<span data-ttu-id="06dbc-147">Ahora puede escribir cmdlets que agreguen y consuman eventos.</span><span class="sxs-lookup"><span data-stu-id="06dbc-147">You can now write cmdlets that add and consume events.</span></span> <span data-ttu-id="06dbc-148">Vea la clase PSEvent.</span><span class="sxs-lookup"><span data-stu-id="06dbc-148">See the PSEvent class.</span></span>

## <a name="proxy-commands"></a><span data-ttu-id="06dbc-149">Comandos de proxy</span><span class="sxs-lookup"><span data-stu-id="06dbc-149">Proxy commands</span></span>

<span data-ttu-id="06dbc-150">Ahora puede escribir comandos de proxy que se pueden usar para ejecutar otro comando.</span><span class="sxs-lookup"><span data-stu-id="06dbc-150">You can now write proxy commands that can be used to run another command.</span></span> <span data-ttu-id="06dbc-151">Un comando proxy permite controlar qué funcionalidad del cmdlet de origen está disponible para el usuario.</span><span class="sxs-lookup"><span data-stu-id="06dbc-151">A proxy command allows you to control what functionality of the source cmdlet is available to the user.</span></span> <span data-ttu-id="06dbc-152">Por ejemplo, puede crear un comando de proxy que quite un parámetro proporcionado por el comando de origen.</span><span class="sxs-lookup"><span data-stu-id="06dbc-152">For example, you can create a proxy command that removes a parameter that is supplied by the source command.</span></span> <span data-ttu-id="06dbc-153">Vea la clase ProxyCommand.</span><span class="sxs-lookup"><span data-stu-id="06dbc-153">See the ProxyCommand class.</span></span>

## <a name="multiple-choice-prompts"></a><span data-ttu-id="06dbc-154">Solicitudes de varias opciones</span><span class="sxs-lookup"><span data-stu-id="06dbc-154">Multiple choice prompts</span></span>

<span data-ttu-id="06dbc-155">Ahora puede escribir aplicaciones que puedan proporcionar mensajes que permitan al usuario seleccionar varias opciones.</span><span class="sxs-lookup"><span data-stu-id="06dbc-155">You can now write applications that can provide prompts that allow the user to select multiple choices.</span></span> <span data-ttu-id="06dbc-156">Vea la interfaz IHostUISupportsMultipleChoiceSelection</span><span class="sxs-lookup"><span data-stu-id="06dbc-156">See the IHostUISupportsMultipleChoiceSelection interface</span></span>

## <a name="interactive-sessions"></a><span data-ttu-id="06dbc-157">Sesiones interactivas</span><span class="sxs-lookup"><span data-stu-id="06dbc-157">Interactive sessions</span></span>

<span data-ttu-id="06dbc-158">Ahora puede escribir aplicaciones que pueden iniciar y detener una sesión interactiva en un equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="06dbc-158">You can now write applications that can start and stop an interactive session on a remote computer.</span></span>
<span data-ttu-id="06dbc-159">Vea la interfaz IHostSupportsInteractiveSession.</span><span class="sxs-lookup"><span data-stu-id="06dbc-159">See the IHostSupportsInteractiveSession interface.</span></span>

## <a name="custom-cmdlet-help-for-providers"></a><span data-ttu-id="06dbc-160">Ayuda de cmdlet personalizada para proveedores</span><span class="sxs-lookup"><span data-stu-id="06dbc-160">Custom Cmdlet Help for Providers</span></span>

<span data-ttu-id="06dbc-161">Ahora puede crear temas de ayuda personalizados para los cmdlets de proveedor.</span><span class="sxs-lookup"><span data-stu-id="06dbc-161">You can now create customized Help topics for the provider cmdlets.</span></span> <span data-ttu-id="06dbc-162">Los temas de ayuda de los cmdlets personalizados pueden explicar cómo funciona el cmdlet en la ruta de acceso del proveedor y documentar las características especiales, incluidos los parámetros dinámicos que el proveedor agrega al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="06dbc-162">Custom cmdlet help topics can explain how the cmdlet works in the provider path and document special features, including the dynamic parameters that the provider adds to the cmdlet.</span></span>