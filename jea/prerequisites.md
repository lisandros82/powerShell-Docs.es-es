---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Requisitos previos de JEA
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893042"
---
# <a name="prerequisites"></a><span data-ttu-id="2b7ee-103">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="2b7ee-103">Prerequisites</span></span>

> <span data-ttu-id="2b7ee-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2b7ee-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="2b7ee-105">Just Enough Administration es una característica incluida con Windows PowerShell 5.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="2b7ee-106">En este tema, se describen los requisitos previos que se deben cumplir para empezar a usar JEA.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="2b7ee-107">Instalar JEA</span><span class="sxs-lookup"><span data-stu-id="2b7ee-107">Install JEA</span></span>

<span data-ttu-id="2b7ee-108">JEA está disponible con Windows PowerShell 5.0 y versiones posteriores, pero se recomienda que instale la versión más reciente de PowerShell disponible para su sistema para obtener la funcionalidad completa.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="2b7ee-109">En la tabla siguiente, se describe la disponibilidad de JEA en Windows Server:</span><span class="sxs-lookup"><span data-stu-id="2b7ee-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="2b7ee-110">Sistema operativo de servidor</span><span class="sxs-lookup"><span data-stu-id="2b7ee-110">Server Operating System</span></span>   | <span data-ttu-id="2b7ee-111">Disponibilidad de JEA</span><span class="sxs-lookup"><span data-stu-id="2b7ee-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="2b7ee-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="2b7ee-112">Windows Server 2016</span></span>       | <span data-ttu-id="2b7ee-113">Preinstalado</span><span class="sxs-lookup"><span data-stu-id="2b7ee-113">Preinstalled</span></span>
<span data-ttu-id="2b7ee-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="2b7ee-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="2b7ee-115">Funcionalidad completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2b7ee-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="2b7ee-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="2b7ee-116">Windows Server 2012</span></span>       | <span data-ttu-id="2b7ee-117">Funcionalidad completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2b7ee-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="2b7ee-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="2b7ee-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="2b7ee-119">Funcionalidad reducida<sup>1</sup> con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2b7ee-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="2b7ee-120">También puede usar JEA en el equipo de casa o del trabajo:</span><span class="sxs-lookup"><span data-stu-id="2b7ee-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="2b7ee-121">Sistema operativo de cliente</span><span class="sxs-lookup"><span data-stu-id="2b7ee-121">Client Operating System</span></span>   | <span data-ttu-id="2b7ee-122">Disponibilidad de JEA</span><span class="sxs-lookup"><span data-stu-id="2b7ee-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="2b7ee-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="2b7ee-123">Windows 10 1607+</span></span>          | <span data-ttu-id="2b7ee-124">Preinstalado</span><span class="sxs-lookup"><span data-stu-id="2b7ee-124">Preinstalled</span></span>
<span data-ttu-id="2b7ee-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="2b7ee-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="2b7ee-126">Preinstalado, con funcionalidad reducida<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2b7ee-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="2b7ee-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="2b7ee-127">Windows 10 1507</span></span>           | <span data-ttu-id="2b7ee-128">No disponible</span><span class="sxs-lookup"><span data-stu-id="2b7ee-128">Not available</span></span>
<span data-ttu-id="2b7ee-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="2b7ee-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="2b7ee-130">Funcionalidad completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2b7ee-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="2b7ee-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="2b7ee-131">Windows 7</span></span>                 | <span data-ttu-id="2b7ee-132">Funcionalidad reducida<sup>1</sup> con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2b7ee-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="2b7ee-133"><sup>1</sup> JEA no se puede configurar para usar cuentas de servicio administradas de grupo en Windows Server 2008 R2 o Windows 7.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="2b7ee-134">Las cuentas virtuales y otras características de JEA *sí* se admiten.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="2b7ee-135"><sup>2</sup> Las versiones 1511 y 1603 de Windows 10 no admiten las siguientes características de JEA: ejecución como una cuenta de servicio administrada de grupo, reglas de acceso condicional en configuraciones de sesión, la unidad de usuario y concesión de acceso a cuentas de usuario locales.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="2b7ee-136">Para obtener compatibilidad con estas características, actualice Windows a la versión 1607 (actualización de aniversario) o a una versión superior.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="2b7ee-137">Comprobar qué versión de PowerShell está instalada</span><span class="sxs-lookup"><span data-stu-id="2b7ee-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="2b7ee-138">Para comprobar qué versión de PowerShell está instalada en el sistema, compruebe la variable `$PSVersionTable` en un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="2b7ee-139">Está listo para usar JEA si la versión *principal* es igual o superior a **5**.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="2b7ee-140">Para obtener la mejor experiencia y tener acceso a todas las características más recientes, se recomienda que actualice a la versión de PowerShell **5.1** cuando sea posible.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="2b7ee-141">Instalar Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="2b7ee-141">Install Windows Management Framework</span></span>

<span data-ttu-id="2b7ee-142">Si ejecuta una versión anterior de PowerShell, deberá actualizar el sistema con la última actualización de Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="2b7ee-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="2b7ee-143">Los paquetes de actualización y un vínculo a las notas de la versión de WMF más recientes están disponibles en el [Centro de descarga](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).</span><span class="sxs-lookup"><span data-stu-id="2b7ee-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).</span></span>

<span data-ttu-id="2b7ee-144">Se recomienda encarecidamente que pruebe la compatibilidad de la carga de trabajo con WMF antes de actualizar todos los servidores.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="2b7ee-145">Los usuarios de Windows 10 deben instalar las actualizaciones más recientes de las características para obtener la versión actual de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="2b7ee-146">Habilitar Comunicación remota con PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b7ee-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="2b7ee-147">La comunicación remota de PowerShell proporciona la base sobre la que se compila JEA.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="2b7ee-148">Por tanto, es necesario garantizar que la comunicación remota de PowerShell está habilitada y [adecuadamente protegida](/powershell/scripting/setup/winrmsecurity) en su sistema antes de poder usar JEA.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="2b7ee-149">La comunicación remota de PowerShell está habilitada de manera predeterminada en Windows Server 2012, 2012 R2 y 2016.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="2b7ee-150">Puede habilitar la comunicación remota de PowerShell si ejecuta el siguiente comando en una ventana de PowerShell con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="2b7ee-151">Habilitar el registro de bloques de script y módulos de PowerShell (opcional)</span><span class="sxs-lookup"><span data-stu-id="2b7ee-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="2b7ee-152">En los siguientes pasos se habilita el registro para todas las acciones de PowerShell del sistema.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="2b7ee-153">El registro de módulos de PowerShell no es necesario para JEA, pero se recomienda encarecidamente que lo active para asegurarse de que los comandos que ejecutan los usuarios se registran en una ubicación central.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="2b7ee-154">Puede configurar la directiva de registro de módulos de PowerShell mediante la directiva de grupo.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="2b7ee-155">Abra el Editor de directivas de grupo local en una estación de trabajo o un objeto de directiva de grupo en la consola de administración de directivas de grupo en un controlador de dominio de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="2b7ee-156">Vaya a **Configuración del equipo\\Plantillas administrativas\\Componentes de Windows\\Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="2b7ee-157">Haga doble clic en **Activar registro de módulos**.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="2b7ee-158">Haga clic en **Habilitado**.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-158">Click **Enabled**</span></span>
5. <span data-ttu-id="2b7ee-159">En la sección Opciones, haga clic en **Mostrar** junto a Nombres de módulos.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="2b7ee-160">Escriba `\*` en la ventana emergente.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-160">Type `\*` in the pop up window.</span></span> <span data-ttu-id="2b7ee-161">Esto indica a PowerShell que registre los comandos de todos los módulos.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="2b7ee-162">Haga clic en **Aceptar** para establecer la directiva.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="2b7ee-163">Haga doble clic en **Activar el registro de bloque de script de PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="2b7ee-164">Haga clic en **Habilitado**.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-164">Click **Enabled**</span></span>
10. <span data-ttu-id="2b7ee-165">Haga clic en **Aceptar** para establecer la directiva.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="2b7ee-166">(Solo en equipos unidos a un dominio) Ejecute `gpupdate` o espere a que la directiva de grupo procese la directiva actualizada y aplique la configuración.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-166">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="2b7ee-167">También puede habilitar la transcripción de PowerShell de todo el sistema a través de la directiva de grupo.</span><span class="sxs-lookup"><span data-stu-id="2b7ee-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2b7ee-168">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="2b7ee-168">Next steps</span></span>

[<span data-ttu-id="2b7ee-169">Crear un archivo de funcionalidad de rol</span><span class="sxs-lookup"><span data-stu-id="2b7ee-169">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="2b7ee-170">Crear un archivo de configuración de sesión</span><span class="sxs-lookup"><span data-stu-id="2b7ee-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="2b7ee-171">Vea también</span><span class="sxs-lookup"><span data-stu-id="2b7ee-171">See also</span></span>

[<span data-ttu-id="2b7ee-172">Información adicional sobre la seguridad de WinRM y comunicación remota de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b7ee-172">Additional information about PowerShell Remoting and WinRM security</span></span>](/powershell/scripting/setup/winrmsecurity)

[<span data-ttu-id="2b7ee-173">Entrada de blog sobre seguridad de *PowerShell ♥ the Blue Team*</span><span class="sxs-lookup"><span data-stu-id="2b7ee-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)