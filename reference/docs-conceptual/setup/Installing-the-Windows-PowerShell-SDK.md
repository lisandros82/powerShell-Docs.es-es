---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Instalar el SDK de Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953572"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="2f428-103">Instalar el SDK de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f428-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="2f428-104">En el siguiente tema se describe cómo instalar PowerShell SDK en distintas versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="2f428-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="2f428-105">Instalar el SDK de Windows PowerShell 3.0 para Windows 8 y Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="2f428-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="2f428-106">Windows PowerShell 3.0 se instala automáticamente con Windows 8 y Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="2f428-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="2f428-107">Además, puede descargar e instalar los ensamblados de referencia para Windows PowerShell 3.0 como parte de Windows 8 SDK.</span><span class="sxs-lookup"><span data-stu-id="2f428-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="2f428-108">Estos ensamblados le permiten escribir cmdlets, proveedores y programas host para Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="2f428-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="2f428-109">Al instalar Windows SDK para Windows 8, los ensamblados de Windows PowerShell se instalan automáticamente en la carpeta de ensamblados de referencia, en \Archivos de programa (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span><span class="sxs-lookup"><span data-stu-id="2f428-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span></span>
<span data-ttu-id="2f428-110">Para obtener más información, consulte el [sitio de descarga del SDK de Windows 8](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-110">For more information, see the [Windows 8 SDK download site](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span></span>
<span data-ttu-id="2f428-111">También hay disponibles ejemplos de código de Windows PowerShell en el Centro de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="2f428-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="2f428-112">Para obtener más información, consulte la página de ejemplos de código de escritorio en el [sitio del Centro de desarrollo](http://code.msdn.microsoft.com/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="2f428-112">For more information, see the Desktop code sample page on the [Dev center site](http://code.msdn.microsoft.com/windowsdesktop/).</span></span>

<span data-ttu-id="2f428-113">Además, Windows PowerShell 3.0 también es compatible con Windows PowerShell 2.0 SDK, que incluye varios ejemplos de código.</span><span class="sxs-lookup"><span data-stu-id="2f428-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="2f428-114">Más abajo le indicamos cómo descargar Windows PowerShell 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="2f428-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="2f428-115">(Tenga en cuenta que, a pesar de que los ejemplos de código de la versión 2.0 son compatibles con Windows 8 y Windows PowerShell 3.0, no puede instalar Windows PowerShell 2.0 en una plataforma de Windows 8).</span><span class="sxs-lookup"><span data-stu-id="2f428-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="2f428-116">Instalar el SDK de Windows PowerShell 3.0 para Windows 7 y Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="2f428-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="2f428-117">Windows 7 y Windows Server 2008 R2 tienen instalado automáticamente PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="2f428-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="2f428-118">Además, puede instalar PowerShell 3.0 en estos sistemas.</span><span class="sxs-lookup"><span data-stu-id="2f428-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="2f428-119">(Para obtener más información, consulte [Instalación de Windows PowerShell](Installing-Windows-PowerShell.md)).</span><span class="sxs-lookup"><span data-stu-id="2f428-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="2f428-120">Tal como se ha descrito anteriormente, también puede instalar Windows 8 SDK en Windows 7 y Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="2f428-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="2f428-121">Instalar el SDK de Windows PowerShell 2.0 para Windows 7, Vista, XP, Server 2003 y Server 2008</span><span class="sxs-lookup"><span data-stu-id="2f428-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="2f428-122">El SDK de Windows PowerShell 2.0 proporciona los ensamblados de referencia necesarios para escribir cmdlets, proveedores y aplicaciones host, así como código de ejemplo en C# que se puede usar como punto de partida para comenzar a escribir código.</span><span class="sxs-lookup"><span data-stu-id="2f428-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="2f428-123">Para instalar este SDK, consulte [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611) (SDK de Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="2f428-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="2f428-124">Ensamblados de referencia</span><span class="sxs-lookup"><span data-stu-id="2f428-124">Reference assemblies</span></span>

<span data-ttu-id="2f428-125">Los ensamblados de referencia se instalan de forma predeterminada en la siguiente ubicación: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="2f428-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> <span data-ttu-id="2f428-126">**Nota**: El código compilado con los ensamblados de Windows PowerShell 2.0 no puede cargarse en instalaciones de Windows PowerShell 1.0.</span><span class="sxs-lookup"><span data-stu-id="2f428-126">**Note**: Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
><span data-ttu-id="2f428-127">Sin embargo, el código compilado con los ensamblados de Windows PowerShell 1.0 sí puede cargarse en las instalaciones de Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="2f428-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="2f428-128">muestras</span><span class="sxs-lookup"><span data-stu-id="2f428-128">Samples</span></span>

<span data-ttu-id="2f428-129">Los ejemplos de código se instalan de forma predeterminada en la siguiente ubicación: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="2f428-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="2f428-130">En las secciones siguientes, se proporciona una breve descripción de lo que hace cada ejemplo.</span><span class="sxs-lookup"><span data-stu-id="2f428-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="2f428-131">Ejemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f428-131">Cmdlet samples</span></span>
<span data-ttu-id="2f428-132">**GetProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="2f428-132">**GetProcessSample01**</span></span>

<span data-ttu-id="2f428-133">Muestra cómo escribir un cmdlet sencillo que obtiene todos los procesos en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="2f428-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

<span data-ttu-id="2f428-134">**GetProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="2f428-134">**GetProcessSample02**</span></span>

<span data-ttu-id="2f428-135">Muestra cómo agregar parámetros al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f428-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="2f428-136">El cmdlet toma uno o más nombres de proceso y devuelve los procesos coincidentes.</span><span class="sxs-lookup"><span data-stu-id="2f428-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

<span data-ttu-id="2f428-137">**GetProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="2f428-137">**GetProcessSample03**</span></span>

<span data-ttu-id="2f428-138">Muestra cómo agregar parámetros que aceptan la entrada desde la canalización.</span><span class="sxs-lookup"><span data-stu-id="2f428-138">Shows how to add parameters that accept input from the pipeline.</span></span>

<span data-ttu-id="2f428-139">**GetProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="2f428-139">**GetProcessSample04**</span></span>

<span data-ttu-id="2f428-140">Muestra cómo controlar errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="2f428-140">Shows how to handle nonterminating errors.</span></span>

<span data-ttu-id="2f428-141">**GetProcessSample05**</span><span class="sxs-lookup"><span data-stu-id="2f428-141">**GetProcessSample05**</span></span>

<span data-ttu-id="2f428-142">Muestra cómo mostrar una lista de procesos especificados.</span><span class="sxs-lookup"><span data-stu-id="2f428-142">Shows how to display a list of specified processes.</span></span>

<span data-ttu-id="2f428-143">**SelectObject**</span><span class="sxs-lookup"><span data-stu-id="2f428-143">**SelectObject**</span></span>

<span data-ttu-id="2f428-144">Muestra cómo escribir un filtro para seleccionar solo determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="2f428-144">Shows how to write a filter to select only certain objects.</span></span>

<span data-ttu-id="2f428-145">**SelectString**</span><span class="sxs-lookup"><span data-stu-id="2f428-145">**SelectString**</span></span>

<span data-ttu-id="2f428-146">Muestra cómo buscar patrones específicos en archivos.</span><span class="sxs-lookup"><span data-stu-id="2f428-146">Shows how to search files for specified patterns.</span></span>

<span data-ttu-id="2f428-147">**StopProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="2f428-147">**StopProcessSample01**</span></span>

<span data-ttu-id="2f428-148">Muestra cómo implementar un parámetro *PassThru* y cómo solicitar comentarios de los usuarios mediante llamadas a los métodos [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) y [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) and [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) methods.</span></span>
<span data-ttu-id="2f428-149">Los usuarios especifican el parámetro *PassThru* cuando quieren forzar al cmdlet a devolver un objeto.</span><span class="sxs-lookup"><span data-stu-id="2f428-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

<span data-ttu-id="2f428-150">**StopProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="2f428-150">**StopProcessSample02**</span></span>

<span data-ttu-id="2f428-151">Muestra cómo detener un proceso específico.</span><span class="sxs-lookup"><span data-stu-id="2f428-151">Shows how to stop a specific process.</span></span>

<span data-ttu-id="2f428-152">**StopProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="2f428-152">**StopProcessSample03**</span></span>

<span data-ttu-id="2f428-153">Muestra cómo declarar los alias de parámetros y cómo agregar compatibilidad con caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="2f428-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

<span data-ttu-id="2f428-154">**StopProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="2f428-154">**StopProcessSample04**</span></span>

<span data-ttu-id="2f428-155">Muestra cómo declarar los conjuntos de parámetros y el objeto que el cmdlet toma como entrada, y también cómo especificar el parámetro predeterminado configurado para usarse.</span><span class="sxs-lookup"><span data-stu-id="2f428-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="2f428-156">Ejemplos de comunicación remota</span><span class="sxs-lookup"><span data-stu-id="2f428-156">Remoting samples</span></span>

<span data-ttu-id="2f428-157">**RemoteRunspace01**</span><span class="sxs-lookup"><span data-stu-id="2f428-157">**RemoteRunspace01**</span></span>

<span data-ttu-id="2f428-158">Muestra cómo crear un espacio de ejecución remoto que se usa para establecer una conexión remota.</span><span class="sxs-lookup"><span data-stu-id="2f428-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

<span data-ttu-id="2f428-159">**RemoteRunspacePool01**</span><span class="sxs-lookup"><span data-stu-id="2f428-159">**RemoteRunspacePool01**</span></span>

<span data-ttu-id="2f428-160">Muestra cómo crear un grupo de espacio de ejecución remoto y cómo ejecutar varios comandos simultáneamente mediante el uso de este grupo.</span><span class="sxs-lookup"><span data-stu-id="2f428-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

<span data-ttu-id="2f428-161">**Serialization01**</span><span class="sxs-lookup"><span data-stu-id="2f428-161">**Serialization01**</span></span>

<span data-ttu-id="2f428-162">Muestra cómo examinar una clase .NET existente y cómo asegurarse de que se conserva la información de las propiedades públicas seleccionadas de esta clase a través de la serialización o deserialización.</span><span class="sxs-lookup"><span data-stu-id="2f428-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

<span data-ttu-id="2f428-163">**Serialization02**</span><span class="sxs-lookup"><span data-stu-id="2f428-163">**Serialization02**</span></span>

<span data-ttu-id="2f428-164">Muestra cómo examinar una clase .NET existente y cómo asegurarse de que la información de la instancia de esta clase se conserva en la serialización o deserialización cuando la información no está disponible en las propiedades públicas de la clase.</span><span class="sxs-lookup"><span data-stu-id="2f428-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

<span data-ttu-id="2f428-165">**Serialization03**</span><span class="sxs-lookup"><span data-stu-id="2f428-165">**Serialization03**</span></span>

<span data-ttu-id="2f428-166">Muestra cómo examinar una clase .NET existente y cómo asegurarse de que las instancias de esta clase y de las clases derivadas se deserializan (rehidratan) en objetos .NET dinámicos.</span><span class="sxs-lookup"><span data-stu-id="2f428-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="2f428-167">Ejemplos de eventos</span><span class="sxs-lookup"><span data-stu-id="2f428-167">Event samples</span></span>

<span data-ttu-id="2f428-168">**Event01**</span><span class="sxs-lookup"><span data-stu-id="2f428-168">**Event01**</span></span>

<span data-ttu-id="2f428-169">Muestra cómo crear un cmdlet para el registro de eventos mediante la derivación de ObjectEventRegistrationBase.</span><span class="sxs-lookup"><span data-stu-id="2f428-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

<span data-ttu-id="2f428-170">**Event02**</span><span class="sxs-lookup"><span data-stu-id="2f428-170">**Event02**</span></span>

<span data-ttu-id="2f428-171">Muestra cómo recibir notificaciones de eventos de Windows PowerShell que se generan en equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="2f428-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="2f428-172">Usa el evento PSEventReceived que se expone a través de la clase [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-172">It uses the PSEventReceived event exposed through the [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="2f428-173">Ejemplos de aplicación host</span><span class="sxs-lookup"><span data-stu-id="2f428-173">Hosting application samples</span></span>

<span data-ttu-id="2f428-174">**Runspace01**</span><span class="sxs-lookup"><span data-stu-id="2f428-174">**Runspace01**</span></span>

<span data-ttu-id="2f428-175">Muestra cómo usar la clase [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para ejecutar el cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) de forma sincrónica.</span><span class="sxs-lookup"><span data-stu-id="2f428-175">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet synchronously.</span></span>
<span data-ttu-id="2f428-176">El cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) devuelve objetos [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) para cada proceso que se ejecuta en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="2f428-176">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

<span data-ttu-id="2f428-177">**Runspace02**</span><span class="sxs-lookup"><span data-stu-id="2f428-177">**Runspace02**</span></span>

<span data-ttu-id="2f428-178">Muestra cómo usar la clase [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para ejecutar los cmdlets [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) y [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) de forma sincrónica.</span><span class="sxs-lookup"><span data-stu-id="2f428-178">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) and [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets synchronously.</span></span>
<span data-ttu-id="2f428-179">El cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) devuelve objetos [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) para cada proceso que se ejecuta en el equipo local y el cmdlet Sort-Object ordena los objetos según su propiedad [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-179">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the Sort-Object sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="2f428-180">Los resultados de estos comandos se muestran mediante un control [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

<span data-ttu-id="2f428-181">**Runspace03**</span><span class="sxs-lookup"><span data-stu-id="2f428-181">**Runspace03**</span></span>

<span data-ttu-id="2f428-182">Muestra cómo usar la clase [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para ejecutar un script de forma sincrónica y cómo controlar los errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="2f428-182">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="2f428-183">El script recibe una lista de nombres de procesos y después los recupera.</span><span class="sxs-lookup"><span data-stu-id="2f428-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="2f428-184">Los resultados del script, incluidos los errores de no terminación generados al ejecutarlo, se muestran en una ventana de consola.</span><span class="sxs-lookup"><span data-stu-id="2f428-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

<span data-ttu-id="2f428-185">**Runspace04**</span><span class="sxs-lookup"><span data-stu-id="2f428-185">**Runspace04**</span></span>

<span data-ttu-id="2f428-186">Muestra cómo usar la clase [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para ejecutar comandos y cómo capturar los errores de terminación que se producen al ejecutar dichos comandos.</span><span class="sxs-lookup"><span data-stu-id="2f428-186">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="2f428-187">Se ejecutan dos comandos; al último, se le pasa un argumento de parámetro que no es válido.</span><span class="sxs-lookup"><span data-stu-id="2f428-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="2f428-188">Como resultado, no se devuelve ningún objeto y se produce un error de terminación.</span><span class="sxs-lookup"><span data-stu-id="2f428-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

<span data-ttu-id="2f428-189">**Runspace05**</span><span class="sxs-lookup"><span data-stu-id="2f428-189">**Runspace05**</span></span>

<span data-ttu-id="2f428-190">Muestra cómo agregar un complemento a un objeto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) para que el cmdlet del complemento esté disponible al abrir el espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="2f428-190">Shows how to add a snap-in to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="2f428-191">El complemento proporciona un cmdlet Get-Proc (definido por el [ejemplo GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) que se ejecuta de forma sincrónica mediante un objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="2f428-192">**Runspace06**</span><span class="sxs-lookup"><span data-stu-id="2f428-192">**Runspace06**</span></span>

<span data-ttu-id="2f428-193">Muestra cómo agregar un módulo a un objeto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) para que el módulo se cargue al abrir el espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="2f428-193">Shows how to add a module to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="2f428-194">El módulo proporciona un cmdlet Get-Proc (definido por el [ejemplo GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) que se ejecuta de forma sincrónica mediante un objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="2f428-195">**Runspace07**</span><span class="sxs-lookup"><span data-stu-id="2f428-195">**Runspace07**</span></span>

<span data-ttu-id="2f428-196">Muestra cómo crear un espacio de ejecución y lo usa para ejecutar dos cmdlets de forma sincrónica mediante un objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="2f428-197">**Runspace08**</span><span class="sxs-lookup"><span data-stu-id="2f428-197">**Runspace08**</span></span>

<span data-ttu-id="2f428-198">Muestra cómo agregar comandos y argumentos a la canalización de un objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) y cómo ejecutar los comandos de forma sincrónica.</span><span class="sxs-lookup"><span data-stu-id="2f428-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the commands synchronously.</span></span>

<span data-ttu-id="2f428-199">**Runspace09**</span><span class="sxs-lookup"><span data-stu-id="2f428-199">**Runspace09**</span></span>

<span data-ttu-id="2f428-200">Muestra cómo agregar un script a la canalización de un objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) y cómo ejecutar el script de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="2f428-200">Shows how to add a script to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="2f428-201">Los eventos se usan para controlar la salida del script.</span><span class="sxs-lookup"><span data-stu-id="2f428-201">Events are used to handle the output of the script.</span></span>

<span data-ttu-id="2f428-202">**Runspace10**</span><span class="sxs-lookup"><span data-stu-id="2f428-202">**Runspace10**</span></span>

<span data-ttu-id="2f428-203">Muestra cómo crear un estado de sesión inicial predeterminado, cómo agregar un cmdlet a [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), cómo crear un espacio de ejecución que use el estado de sesión inicial y cómo ejecutar el comando con un objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="2f428-204">**Runspace11**</span><span class="sxs-lookup"><span data-stu-id="2f428-204">**Runspace11**</span></span>

<span data-ttu-id="2f428-205">Muestra cómo usar la clase [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) para crear un comando de proxy que llama a un cmdlet existente, pero restringe el conjunto de parámetros disponibles.</span><span class="sxs-lookup"><span data-stu-id="2f428-205">Shows how to use the [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="2f428-206">El comando de proxy se agrega entonces a un estado de sesión inicial que se usa para crear un espacio de ejecución restringido.</span><span class="sxs-lookup"><span data-stu-id="2f428-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="2f428-207">Esto significa que el usuario puede tener acceso a la funcionalidad del cmdlet solo mediante el comando de proxy.</span><span class="sxs-lookup"><span data-stu-id="2f428-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

<span data-ttu-id="2f428-208">**PowerShell01**</span><span class="sxs-lookup"><span data-stu-id="2f428-208">**PowerShell01**</span></span>

<span data-ttu-id="2f428-209">Muestra cómo crear un espacio de ejecución restringido mediante un objeto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-209">Shows how to create a constrained runspace using an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object.</span></span>

<span data-ttu-id="2f428-210">**PowerShell02**</span><span class="sxs-lookup"><span data-stu-id="2f428-210">**PowerShell02**</span></span>

<span data-ttu-id="2f428-211">Muestra cómo usar un grupo de espacio de ejecución para ejecutar varios comandos simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="2f428-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="2f428-212">Ejemplos de host</span><span class="sxs-lookup"><span data-stu-id="2f428-212">Host samples</span></span>

<span data-ttu-id="2f428-213">**Host01**</span><span class="sxs-lookup"><span data-stu-id="2f428-213">**Host01**</span></span>

<span data-ttu-id="2f428-214">Muestra cómo implementar una aplicación host que usa un host personalizado.</span><span class="sxs-lookup"><span data-stu-id="2f428-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="2f428-215">En este ejemplo se crea un espacio de ejecución que usa el host personalizado y, después, se usa la API [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para ejecutar un script que llame al código "exit".</span><span class="sxs-lookup"><span data-stu-id="2f428-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="2f428-216">La aplicación host examina después la salida del script e imprime los resultados.</span><span class="sxs-lookup"><span data-stu-id="2f428-216">The host application then looks at the output of the script and prints out the results.</span></span>

<span data-ttu-id="2f428-217">**Host02**</span><span class="sxs-lookup"><span data-stu-id="2f428-217">**Host02**</span></span>

<span data-ttu-id="2f428-218">Muestra cómo escribir una aplicación host que usa el tiempo de ejecución de Windows PowerShell junto con una implementación de host personalizado.</span><span class="sxs-lookup"><span data-stu-id="2f428-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="2f428-219">La aplicación host establece la referencia cultural del host en alemán, ejecuta el cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324), muestra los resultados tal como los vería con pwrsh.exe e imprime los datos y la hora actuales en alemán.</span><span class="sxs-lookup"><span data-stu-id="2f428-219">The host application sets the host culture to German, runs the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

<span data-ttu-id="2f428-220">**Host03**</span><span class="sxs-lookup"><span data-stu-id="2f428-220">**Host03**</span></span>

<span data-ttu-id="2f428-221">Muestra cómo crear una aplicación host basada en consola interactiva que lee los comandos de la línea de comandos, los ejecuta y muestra sus resultados en la consola.</span><span class="sxs-lookup"><span data-stu-id="2f428-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

<span data-ttu-id="2f428-222">**Host04**</span><span class="sxs-lookup"><span data-stu-id="2f428-222">**Host04**</span></span>

<span data-ttu-id="2f428-223">Muestra cómo crear una aplicación host basada en consola interactiva que lee los comandos de la línea de comandos, los ejecuta y muestra sus resultados en la consola.</span><span class="sxs-lookup"><span data-stu-id="2f428-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="2f428-224">Esta aplicación host también permite mostrar avisos para que el usuario pueda especificar varias opciones.</span><span class="sxs-lookup"><span data-stu-id="2f428-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

<span data-ttu-id="2f428-225">**Host05**</span><span class="sxs-lookup"><span data-stu-id="2f428-225">**Host05**</span></span>

<span data-ttu-id="2f428-226">Muestra cómo crear una aplicación host basada en consola interactiva que lee los comandos de la línea de comandos, los ejecuta y muestra sus resultados en la consola.</span><span class="sxs-lookup"><span data-stu-id="2f428-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="2f428-227">Esta aplicación host también admite llamadas a equipos remotos mediante los cmdlets [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) y [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212).</span><span class="sxs-lookup"><span data-stu-id="2f428-227">This host application also supports calls to remote computers by using the [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) and [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.</span></span>

<span data-ttu-id="2f428-228">**Host06**</span><span class="sxs-lookup"><span data-stu-id="2f428-228">**Host06**</span></span>

<span data-ttu-id="2f428-229">Muestra cómo crear una aplicación host basada en consola interactiva que lee los comandos de la línea de comandos, los ejecuta y muestra sus resultados en la consola.</span><span class="sxs-lookup"><span data-stu-id="2f428-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="2f428-230">Además, este ejemplo utiliza las API de Tokenizer para especificar el color del texto que el usuario ha escrito.</span><span class="sxs-lookup"><span data-stu-id="2f428-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="2f428-231">Ejemplos de proveedor</span><span class="sxs-lookup"><span data-stu-id="2f428-231">Provider samples</span></span>

<span data-ttu-id="2f428-232">**AccessDBProviderSample01**</span><span class="sxs-lookup"><span data-stu-id="2f428-232">**AccessDBProviderSample01**</span></span>

<span data-ttu-id="2f428-233">Muestra cómo declarar una clase de proveedor que se deriva directamente de la clase [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) class.</span></span>
<span data-ttu-id="2f428-234">Se incluye aquí solo por cuestiones de integridad.</span><span class="sxs-lookup"><span data-stu-id="2f428-234">It is included here only for completeness.</span></span>

<span data-ttu-id="2f428-235">**AccessDBProviderSample02**</span><span class="sxs-lookup"><span data-stu-id="2f428-235">**AccessDBProviderSample02**</span></span>

<span data-ttu-id="2f428-236">Muestra cómo sobrescribir los métodos [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) y [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) para admitir llamadas a los cmdlets New-PSDrive y Remove-PSDrive.</span><span class="sxs-lookup"><span data-stu-id="2f428-236">Shows how to overwrite the [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) and [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) methods to support calls to the New-PSDrive and Remove-PSDrive cmdlets.</span></span>
<span data-ttu-id="2f428-237">La clase de proveedor de este ejemplo se deriva de la clase [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-237">The provider class in this sample derives from the [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) class.</span></span>

<span data-ttu-id="2f428-238">**AccessDBProviderSample03**</span><span class="sxs-lookup"><span data-stu-id="2f428-238">**AccessDBProviderSample03**</span></span>

<span data-ttu-id="2f428-239">Muestra cómo sobrescribir los métodos [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) y [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) para admitir llamadas a los cmdlets Get-Item y Set-Item.</span><span class="sxs-lookup"><span data-stu-id="2f428-239">Shows how to overwrite the [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) and [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) methods to support calls to the Get-Item and Set-Item cmdlets.</span></span>
<span data-ttu-id="2f428-240">La clase de proveedor de este ejemplo se deriva de la clase [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-240">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="2f428-241">**AccessDBProviderSample04**</span><span class="sxs-lookup"><span data-stu-id="2f428-241">**AccessDBProviderSample04**</span></span>

<span data-ttu-id="2f428-242">Muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a los cmdlets Copy-Item, Get-ChildItem, New-Item y Remove-Item.</span><span class="sxs-lookup"><span data-stu-id="2f428-242">Shows how to overwrite container methods to support calls to the Copy-Item, Get-ChildItem, New-Item, and Remove-Item cmdlets.</span></span>
<span data-ttu-id="2f428-243">Estos métodos deberían implementarse cuando el almacén de datos contengan elementos que son contenedores.</span><span class="sxs-lookup"><span data-stu-id="2f428-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="2f428-244">Un contenedor es un grupo de elementos secundarios con un elemento primario común.</span><span class="sxs-lookup"><span data-stu-id="2f428-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="2f428-245">La clase de proveedor de este ejemplo se deriva de la clase [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-245">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="2f428-246">**AccessDBProviderSample05**</span><span class="sxs-lookup"><span data-stu-id="2f428-246">**AccessDBProviderSample05**</span></span>

<span data-ttu-id="2f428-247">Muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a los cmdlets Move-Item y Join-Path.</span><span class="sxs-lookup"><span data-stu-id="2f428-247">Shows how to overwrite container methods to support calls to the Move-Item and Join-Path cmdlets.</span></span>
<span data-ttu-id="2f428-248">Estos métodos deberían implementarse cuando el usuario necesite mover elementos dentro de un contenedor y si el almacén de datos tiene contenedores anidados.</span><span class="sxs-lookup"><span data-stu-id="2f428-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="2f428-249">La clase de proveedor de este ejemplo se deriva de la clase [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-249">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="2f428-250">**AccessDBProviderSample06**</span><span class="sxs-lookup"><span data-stu-id="2f428-250">**AccessDBProviderSample06**</span></span>

<span data-ttu-id="2f428-251">Muestra cómo sobrescribir métodos de contenido para admitir llamadas a los cmdlets Clear-Content, Get-Content y Set-Content.</span><span class="sxs-lookup"><span data-stu-id="2f428-251">Shows how to overwrite content methods to support calls to the Clear-Content, Get-Content, and Set-Content cmdlets.</span></span>
<span data-ttu-id="2f428-252">Estos métodos deberían implementarse cuando el usuario necesite administrar el contenido de los elementos en el almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="2f428-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="2f428-253">La clase de proveedor de este ejemplo se deriva de la clase [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx); también se implementa la interfaz [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f428-253">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class, and it implements the [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.</span></span>