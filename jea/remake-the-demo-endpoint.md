---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Recreación del punto de conexión de la demostración"
ms.technology: powershell
ms.openlocfilehash: 4a56272b6f995500d443d441f5e03db85dac6f96
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="remake-the-demo-endpoint"></a><span data-ttu-id="d94a0-103">Recreación del punto de conexión de demostración</span><span class="sxs-lookup"><span data-stu-id="d94a0-103">Remake the Demo Endpoint</span></span>
<span data-ttu-id="d94a0-104">En esta sección obtendrá información sobre cómo generar una réplica exacta del punto de conexión de demostración usado en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="d94a0-104">In this section, you will learn how to generate an exact replica of the demo endpoint you used in the above section.</span></span>
<span data-ttu-id="d94a0-105">Aquí se introducirán conceptos básicos que son necesarios para entender JEA, incluidas las configuraciones de sesión de PowerShell y las funcionalidades de rol.</span><span class="sxs-lookup"><span data-stu-id="d94a0-105">This will introduce core concepts that are necessary to understand JEA, including PowerShell Session Configurations and Role Capabilities.</span></span>

## <a name="powershell-session-configurations"></a><span data-ttu-id="d94a0-106">Configuraciones de sesión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d94a0-106">PowerShell Session Configurations</span></span>
<span data-ttu-id="d94a0-107">Cuando usó JEA en la sección anterior, comenzó ejecutando el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="d94a0-107">When you used JEA in the above section, you started by running the following command:</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

<span data-ttu-id="d94a0-108">Aunque la mayoría de los parámetros se explican por sí solos, el parámetro *ConfigurationName* puede parecer confuso al principio.</span><span class="sxs-lookup"><span data-stu-id="d94a0-108">While most of the parameters are self-explanatory, the *ConfigurationName* parameter may seem confusing at first.</span></span>
<span data-ttu-id="d94a0-109">Este parámetro especifica la configuración de sesión de PowerShell a la que se conecta.</span><span class="sxs-lookup"><span data-stu-id="d94a0-109">That parameter specified the PowerShell Session Configuration to which you were connecting.</span></span>

<span data-ttu-id="d94a0-110">*Configuración de sesión de PowerShell* es un término sofisticado que hace referencia a un punto de conexión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d94a0-110">*PowerShell Session Configuration* is a fancy term for a PowerShell endpoint.</span></span>
<span data-ttu-id="d94a0-111">Es el "lugar" metafórico donde los usuarios se conectan y obtienen acceso a la funcionalidad de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d94a0-111">It is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="d94a0-112">Según cómo haya establecido una configuración de sesión, puede proporcionar una funcionalidad diferente a los usuarios que se conectan.</span><span class="sxs-lookup"><span data-stu-id="d94a0-112">Based on how you set up a Session Configuration, it can provide different functionality to connecting users.</span></span>
<span data-ttu-id="d94a0-113">En el caso de JEA, se usan configuraciones de sesión para restringir PowerShell a un conjunto limitado de funcionalidades y para ejecutar como una cuenta virtual con privilegios.</span><span class="sxs-lookup"><span data-stu-id="d94a0-113">For JEA, we use Session Configurations to restrict PowerShell to a limited set of functionality and to run as a privileged virtual account.</span></span>

<span data-ttu-id="d94a0-114">Ya tiene varias configuraciones de sesión de PowerShell registradas en la máquina, cada una de ellas configurada de manera ligeramente diferente.</span><span class="sxs-lookup"><span data-stu-id="d94a0-114">You already have several registered PowerShell Session Configurations on your machine, each set up slightly differently.</span></span>
<span data-ttu-id="d94a0-115">La mayoría viene con Windows, pero la configuración de sesión "JEA_Demo" se configuró en la sección [Requisitos previos](prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="d94a0-115">Most of them come with Windows, but the "JEA_Demo" Session Configuration was set up in the [prerequisites](prerequisites.md) section.</span></span>
<span data-ttu-id="d94a0-116">Puede ver todas las configuraciones de sesión registradas ejecutando el comando siguiente en un símbolo del sistema de administrador de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d94a0-116">You can see all registered Session Configurations by running the following command in an Administrator PowerShell prompt:</span></span>

```PowerShell
Get-PSSessionConfiguration
```

## <a name="powershell-session-configuration-files"></a><span data-ttu-id="d94a0-117">Archivos de configuración de sesión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d94a0-117">PowerShell Session Configuration Files</span></span>
<span data-ttu-id="d94a0-118">Puede establecer configuraciones de sesión nuevas registrando *archivos nuevos de configuración de sesión de PowerShell*.</span><span class="sxs-lookup"><span data-stu-id="d94a0-118">You can make new Session Configurations by registering new *PowerShell Session Configuration Files*.</span></span>
<span data-ttu-id="d94a0-119">Los archivos de configuración de sesión tienen la extensión de archivo ".pssc".</span><span class="sxs-lookup"><span data-stu-id="d94a0-119">Session Configuration Files have ".pssc" file extensions.</span></span>
<span data-ttu-id="d94a0-120">Puede generar archivos de configuración de sesión con el cmdlet New-PSSessionConfigurationFile.</span><span class="sxs-lookup"><span data-stu-id="d94a0-120">You can generate Session Configuration Files with the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="d94a0-121">Después, creará y registrará una nueva configuración de sesión para JEA.</span><span class="sxs-lookup"><span data-stu-id="d94a0-121">Next, you are going to create and register a new Session Configuration for JEA.</span></span>

## <a name="generate-and-modify-your-powershell-session-configuration"></a><span data-ttu-id="d94a0-122">Generar y modificar la configuración de sesión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d94a0-122">Generate and Modify your PowerShell Session Configuration</span></span>
<span data-ttu-id="d94a0-123">Ejecute el comando siguiente para generar un archivo "esqueleto" de configuración de sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d94a0-123">Run the following command to generate a PowerShell Session Configuration "skeleton" file.</span></span>

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> <span data-ttu-id="d94a0-124">**SUGERENCIA:** En el archivo esqueleto solo se incluyen de forma predeterminada las opciones de configuración más comunes.</span><span class="sxs-lookup"><span data-stu-id="d94a0-124">**TIP:** Only the most common configuration settings are included in the skeleton file by default.</span></span>
> <span data-ttu-id="d94a0-125">Use el parámetro `-Full` para incluir todas las opciones aplicables en el PSSC generado.</span><span class="sxs-lookup"><span data-stu-id="d94a0-125">Use the `-Full` parameter to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="d94a0-126">Abra el archivo en PowerShell ISE o en su editor de texto preferido.</span><span class="sxs-lookup"><span data-stu-id="d94a0-126">Open the file in PowerShell ISE, or your favorite text editor.</span></span>

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="d94a0-127">Actualice los campos siguientes en el archivo con los valores inferiores (recuerde reemplazarlos en su propio grupo de seguridad no administrador):</span><span class="sxs-lookup"><span data-stu-id="d94a0-127">Update the following fields in the file with the values below (remember to substitute in your own non-administrator security group):</span></span>

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

<span data-ttu-id="d94a0-128">Esto es lo que significa cada una de las entradas:</span><span class="sxs-lookup"><span data-stu-id="d94a0-128">Here is what each of those entries mean:</span></span>

1.  <span data-ttu-id="d94a0-129">El campo *SessionType* define la configuración predeterminada que se va a usar con este punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="d94a0-129">The *SessionType* field defines preset default settings to use with this endpoint.</span></span>
<span data-ttu-id="d94a0-130">*RestrictedRemoteServer* define la configuración mínima necesaria para la administración remota.</span><span class="sxs-lookup"><span data-stu-id="d94a0-130">*RestrictedRemoteServer* defines the minimal settings necessary for remote management.</span></span>
<span data-ttu-id="d94a0-131">De forma predeterminada, un punto de conexión *RestrictedRemoteServer* expone Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host y Out-Default.</span><span class="sxs-lookup"><span data-stu-id="d94a0-131">By default, a *RestrictedRemoteServer* endpoint will expose Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host, and Out-Default.</span></span>
<span data-ttu-id="d94a0-132">Establece *ExecutionPolicy* en *RemoteSigned* y *LanguageMode* en *NoLanguage*.</span><span class="sxs-lookup"><span data-stu-id="d94a0-132">It will set the *ExecutionPolicy* to *RemoteSigned*, and the *LanguageMode* to *NoLanguage*.</span></span>
<span data-ttu-id="d94a0-133">El efecto neto de estos valores es un punto de partida seguro y mínimo para configurar el punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="d94a0-133">The net effect of these settings is a secure and minimal starting point for configuring your endpoint.</span></span>

2.  <span data-ttu-id="d94a0-134">El campo *RoleDefinitions* asigna funcionalidades de rol a grupos específicos.</span><span class="sxs-lookup"><span data-stu-id="d94a0-134">The *RoleDefinitions* field assigns Role Capabilities to specific groups.</span></span>
<span data-ttu-id="d94a0-135">Define quién puede hacer qué como una cuenta con privilegios.</span><span class="sxs-lookup"><span data-stu-id="d94a0-135">It defines who can do what as a privileged account.</span></span>
<span data-ttu-id="d94a0-136">Con este campo, puede especificar la funcionalidad disponible para cualquier usuario que se conecte en función de la pertenencia al grupo.</span><span class="sxs-lookup"><span data-stu-id="d94a0-136">With this field, you can specify the functionality available to any connecting user based on group membership.</span></span>
<span data-ttu-id="d94a0-137">Este es el núcleo de la funcionalidad RBAC de JEA.</span><span class="sxs-lookup"><span data-stu-id="d94a0-137">This is the core of JEA's RBAC functionality.</span></span>
<span data-ttu-id="d94a0-138">En este ejemplo, expone el cmdlet RoleCapability "Maintenance" creado con anterioridad a los miembros del grupo "Contoso\JEA_NonAdmin_Operator".</span><span class="sxs-lookup"><span data-stu-id="d94a0-138">In this example, you are exposing the pre-made "Maintenance" RoleCapability to members of the "Contoso\JEA_NonAdmin_Operator" group.</span></span>

3.  <span data-ttu-id="d94a0-139">El campo *RunAsVirtualAccount* indica que PowerShell debe "ejecutarse como" una cuenta virtual en este punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="d94a0-139">The *RunAsVirtualAccount* field indicates that PowerShell should "run as" a Virtual Account at this endpoint.</span></span>
<span data-ttu-id="d94a0-140">De forma predeterminada, la cuenta virtual es miembro del grupo de administradores integrado.</span><span class="sxs-lookup"><span data-stu-id="d94a0-140">By default, the Virtual Account is a member of the built in Administrators group.</span></span>
<span data-ttu-id="d94a0-141">En un controlador de dominio, también es miembro del grupo de administradores de dominio de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="d94a0-141">On a domain controller, it is also a member of the Domain Administrators group by default.</span></span>
<span data-ttu-id="d94a0-142">Más adelante en esta guía, obtendrá información sobre cómo personalizar los privilegios de la cuenta virtual.</span><span class="sxs-lookup"><span data-stu-id="d94a0-142">Later in this guide, you will learn how to customize the privileges of the Virtual Account.</span></span>

4.  <span data-ttu-id="d94a0-143">El campo *TranscriptDirectory* define dónde se guardan las transcripciones "con consentimiento temporal" de PowerShell después de cada sesión remota.</span><span class="sxs-lookup"><span data-stu-id="d94a0-143">The *TranscriptDirectory* field defines where "over-the-shoulder" PowerShell transcripts are saved after each remote session.</span></span>
<span data-ttu-id="d94a0-144">Estas transcripciones permiten inspeccionar las acciones realizadas en cada sesión de manera legible.</span><span class="sxs-lookup"><span data-stu-id="d94a0-144">These transcripts allow you to inspect the actions taken in each session in a readable way.</span></span>
<span data-ttu-id="d94a0-145">Para obtener más información sobre las transcripciones de PowerShell, consulte esta [entrada de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span><span class="sxs-lookup"><span data-stu-id="d94a0-145">For more information about PowerShell transcripts, check out this [blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>
<span data-ttu-id="d94a0-146">Nota: Los Eventos de Windows normales también capturan información sobre lo que cada usuario ejecutó con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d94a0-146">Note: regular Windows Eventing also captures information about what each user ran with PowerShell.</span></span>
<span data-ttu-id="d94a0-147">Las transcripciones son simplemente un poco más legibles.</span><span class="sxs-lookup"><span data-stu-id="d94a0-147">Transcripts are just a bit more readable.</span></span>

<span data-ttu-id="d94a0-148">Por último, guarde los cambios en *JEADemo2.pssc*.</span><span class="sxs-lookup"><span data-stu-id="d94a0-148">Finally, save your changes to *JEADemo2.pssc*.</span></span>

## <a name="apply-the-powershell-session-configuration"></a><span data-ttu-id="d94a0-149">Aplicar la configuración de sesión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d94a0-149">Apply the PowerShell Session Configuration</span></span>

<span data-ttu-id="d94a0-150">Para crear un punto de conexión a partir de un archivo de configuración de sesión, debe registrar el archivo.</span><span class="sxs-lookup"><span data-stu-id="d94a0-150">To create an endpoint from a Session Configuration file, you need to register the file.</span></span>
<span data-ttu-id="d94a0-151">Para ello, se necesita cierta información:</span><span class="sxs-lookup"><span data-stu-id="d94a0-151">This requires a few pieces of information:</span></span>

1. <span data-ttu-id="d94a0-152">La ruta de acceso al archivo de configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="d94a0-152">The path to the Session Configuration file.</span></span>
2. <span data-ttu-id="d94a0-153">El nombre de la configuración de sesión registrada.</span><span class="sxs-lookup"><span data-stu-id="d94a0-153">The name of your registered Session Configuration.</span></span> <span data-ttu-id="d94a0-154">Este es el mismo nombre que los usuarios proporcionan al parámetro "ConfigurationName" cuando se conectan al punto de conexión con `Enter-PSSession` o `New-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="d94a0-154">This is the same name users provide to the "ConfigurationName" parameter when they connect to your endpoint with `Enter-PSSession` or `New-PSSession`.</span></span>

<span data-ttu-id="d94a0-155">Para registrar la configuración de sesión en la máquina local, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="d94a0-155">To register the Session Configuration on your local machine, run the following command:</span></span>

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="d94a0-156">Enhorabuena,</span><span class="sxs-lookup"><span data-stu-id="d94a0-156">Congratulations!</span></span> <span data-ttu-id="d94a0-157">ha configurado el punto de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="d94a0-157">You have set up your JEA endpoint.</span></span>

## <a name="test-out-your-endpoint"></a><span data-ttu-id="d94a0-158">Probar el punto de conexión</span><span class="sxs-lookup"><span data-stu-id="d94a0-158">Test Out Your Endpoint</span></span>
<span data-ttu-id="d94a0-159">Vuelva a ejecutar los pasos enumerados en la sección [Uso de JEA](using-jea.md) con el nuevo punto de conexión para confirmar que funciona según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="d94a0-159">Re-run the steps listed in the [Using JEA](using-jea.md) section against your new endpoint to confirm it is operating as intended.</span></span>
<span data-ttu-id="d94a0-160">Asegúrese de usar el nombre nuevo del punto de conexión (JEADemo2) al proporcionar el nombre de la configuración a `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="d94a0-160">Be sure to use the new endpoint name (JEADemo2) when providing the configuration name to `Enter-PSSession`.</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## <a name="key-concepts"></a><span data-ttu-id="d94a0-161">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="d94a0-161">Key Concepts</span></span>
<span data-ttu-id="d94a0-162">**Configuración de sesión de PowerShell**: denominada también *punto de conexión de PowerShell*, es el "lugar" metafórico donde los usuarios se conectan y obtienen acceso a la funcionalidad de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d94a0-162">**PowerShell Session Configuration**: Sometimes referred to as *PowerShell Endpoint*, this is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="d94a0-163">Puede enumerar las configuraciones de sesión registradas en el sistema ejecutando `Get-PSSessionConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="d94a0-163">You can list the registered Session Configurations on your system by running `Get-PSSessionConfiguration`.</span></span>
<span data-ttu-id="d94a0-164">Cuando se configura de forma específica, la configuración de sesión de PowerShell también se puede denominar *punto de conexión de JEA*.</span><span class="sxs-lookup"><span data-stu-id="d94a0-164">When configured in a specific way, a PowerShell Session Configuration can be called a *JEA Endpoint*.</span></span>

<span data-ttu-id="d94a0-165">**Archivo de configuración de sesión de PowerShell (.pssc)**: archivo que, cuando se registra, define los valores de una configuración de sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d94a0-165">**PowerShell Session Configuration File (.pssc)**: A file that, when registered, defines settings for a PowerShell Session Configuration.</span></span>
<span data-ttu-id="d94a0-166">Contiene especificaciones para los roles de usuario que pueden conectarse al punto de conexión, la cuenta virtual de ejecución y mucho más.</span><span class="sxs-lookup"><span data-stu-id="d94a0-166">It contains specifications for user roles that can connect to the endpoint, the "run as" Virtual Account, and more.</span></span>     

<span data-ttu-id="d94a0-167">**Definiciones de rol**: campo de un archivo de configuración de sesión que define las funcionalidades de rol concedidas a los usuarios que se conectan.</span><span class="sxs-lookup"><span data-stu-id="d94a0-167">**Role Definitions**: The field in a Session Configuration File that defines the Role Capabilities granted to connecting users.</span></span>
<span data-ttu-id="d94a0-168">Define *quién* puede hacer *qué* como una cuenta con privilegios.</span><span class="sxs-lookup"><span data-stu-id="d94a0-168">It defines *who* can do *what* as a privileged account.</span></span>
<span data-ttu-id="d94a0-169">Este es el núcleo de las funcionalidades RBAC de JEA.</span><span class="sxs-lookup"><span data-stu-id="d94a0-169">This is the core of JEA's RBAC capabilities.</span></span>

<span data-ttu-id="d94a0-170">**SessionType**: campo del archivo de configuración de sesión que representa la configuración predeterminada de una configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="d94a0-170">**SessionType**: A field in a Session Configuration File that represents default settings for a Session Configuration.</span></span>
<span data-ttu-id="d94a0-171">En el caso de los puntos de conexión de JEA, debe establecerse en RestrictedRemoteServer.</span><span class="sxs-lookup"><span data-stu-id="d94a0-171">For JEA endpoints, this must be set to RestrictedRemoteServer.</span></span>

<span data-ttu-id="d94a0-172">**Transcripción de PowerShell**: archivo que contiene una vista "con consentimiento temporal" de una sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d94a0-172">**PowerShell Transcript**: A file containing an "over-the-shoulder" view of a PowerShell session.</span></span>
<span data-ttu-id="d94a0-173">Puede establecer que PowerShell genere transcripciones para sesiones de JEA mediante el campo TranscriptDirectory.</span><span class="sxs-lookup"><span data-stu-id="d94a0-173">You can set PowerShell to generate transcripts for JEA sessions using the TranscriptDirectory field.</span></span>
<span data-ttu-id="d94a0-174">Para obtener más información sobre las transcripciones, consulte esta [entrada de blog](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span><span class="sxs-lookup"><span data-stu-id="d94a0-174">For more information on transcripts, check out this [blog post](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span></span>

