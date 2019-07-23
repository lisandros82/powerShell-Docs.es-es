---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Requisitos previos de JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734281"
---
# <a name="prerequisites"></a><span data-ttu-id="f7c59-103">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="f7c59-103">Prerequisites</span></span>

<span data-ttu-id="f7c59-104">Just Enough Administration es una característica incluida en PowerShell 5.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="f7c59-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="f7c59-105">En este artículo se describen los requisitos previos que se deben cumplir para empezar a usar JEA.</span><span class="sxs-lookup"><span data-stu-id="f7c59-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="f7c59-106">Comprobar qué versión de PowerShell está instalada</span><span class="sxs-lookup"><span data-stu-id="f7c59-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="f7c59-107">Para comprobar qué versión de PowerShell está instalada en el sistema, compruebe la variable `$PSVersionTable` en un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7c59-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="f7c59-108">JEA está disponible con PowerShell 5.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="f7c59-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="f7c59-109">Para obtener la funcionalidad completa, se recomienda instalar la versión más reciente de PowerShell disponible para el sistema.</span><span class="sxs-lookup"><span data-stu-id="f7c59-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="f7c59-110">En la tabla siguiente, se describe la disponibilidad de JEA en Windows Server:</span><span class="sxs-lookup"><span data-stu-id="f7c59-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="f7c59-111">Sistema operativo de servidor</span><span class="sxs-lookup"><span data-stu-id="f7c59-111">Server Operating System</span></span> |                <span data-ttu-id="f7c59-112">Disponibilidad de JEA</span><span class="sxs-lookup"><span data-stu-id="f7c59-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="f7c59-113">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="f7c59-113">Windows Server 2016+</span></span>    | <span data-ttu-id="f7c59-114">Preinstalado</span><span class="sxs-lookup"><span data-stu-id="f7c59-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="f7c59-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f7c59-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="f7c59-116">Funcionalidad completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f7c59-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="f7c59-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="f7c59-117">Windows Server 2012</span></span>     | <span data-ttu-id="f7c59-118">Funcionalidad completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f7c59-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="f7c59-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="f7c59-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="f7c59-120">Funcionalidad reducida<sup>1</sup> con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f7c59-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="f7c59-121">También puede usar JEA en el equipo de casa o del trabajo:</span><span class="sxs-lookup"><span data-stu-id="f7c59-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="f7c59-122">Sistema operativo de cliente</span><span class="sxs-lookup"><span data-stu-id="f7c59-122">Client Operating System</span></span> |                   <span data-ttu-id="f7c59-123">Disponibilidad de JEA</span><span class="sxs-lookup"><span data-stu-id="f7c59-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="f7c59-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="f7c59-124">Windows 10 1607+</span></span>        | <span data-ttu-id="f7c59-125">Preinstalado</span><span class="sxs-lookup"><span data-stu-id="f7c59-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="f7c59-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="f7c59-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="f7c59-127">Preinstalado, con funcionalidad reducida<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="f7c59-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="f7c59-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="f7c59-128">Windows 10 1507</span></span>         | <span data-ttu-id="f7c59-129">No disponible</span><span class="sxs-lookup"><span data-stu-id="f7c59-129">Not available</span></span>                                        |
| <span data-ttu-id="f7c59-130">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="f7c59-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="f7c59-131">Funcionalidad completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f7c59-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="f7c59-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="f7c59-132">Windows 7</span></span>               | <span data-ttu-id="f7c59-133">Funcionalidad reducida<sup>1</sup> con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f7c59-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="f7c59-134"><sup>1</sup> JEA no se puede configurar para usar cuentas de servicio administradas de grupo en Windows Server 2008 R2 o Windows 7.</span><span class="sxs-lookup"><span data-stu-id="f7c59-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="f7c59-135">Las cuentas virtuales y otras características de JEA *sí* se admiten.</span><span class="sxs-lookup"><span data-stu-id="f7c59-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="f7c59-136"><sup>2</sup> Las características de JEA siguientes no se admiten en las versiones 1511 y 1603 de Windows 10:</span><span class="sxs-lookup"><span data-stu-id="f7c59-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="f7c59-137">Ejecución como una cuenta de servicio administrada de grupo</span><span class="sxs-lookup"><span data-stu-id="f7c59-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="f7c59-138">Reglas de acceso condicional en configuraciones de sesión</span><span class="sxs-lookup"><span data-stu-id="f7c59-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="f7c59-139">Unidad de usuario</span><span class="sxs-lookup"><span data-stu-id="f7c59-139">The user drive</span></span>
  - <span data-ttu-id="f7c59-140">Concesión de acceso a cuentas de usuario locales</span><span class="sxs-lookup"><span data-stu-id="f7c59-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="f7c59-141">Para obtener compatibilidad con estas características, actualice Windows a la versión 1607 (actualización de aniversario) o a una versión superior.</span><span class="sxs-lookup"><span data-stu-id="f7c59-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="f7c59-142">Instalar Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="f7c59-142">Install Windows Management Framework</span></span>

<span data-ttu-id="f7c59-143">Si ejecuta una versión anterior de PowerShell, es posible que tenga que actualizar el sistema con la actualización más reciente de Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="f7c59-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="f7c59-144">Para obtener más información, vea la documentación de [WMF](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="f7c59-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="f7c59-145">Se recomienda probar la compatibilidad de la carga de trabajo con WMF antes de actualizar todos los servidores.</span><span class="sxs-lookup"><span data-stu-id="f7c59-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="f7c59-146">Los usuarios de Windows 10 deben instalar las actualizaciones más recientes de las características para obtener la versión actual de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7c59-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="f7c59-147">Habilitar Comunicación remota con PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7c59-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="f7c59-148">La comunicación remota de PowerShell proporciona la base sobre la que se compila JEA.</span><span class="sxs-lookup"><span data-stu-id="f7c59-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="f7c59-149">Es necesario garantizar que la comunicación remota de PowerShell está habilitada y protegida de forma adecuada antes de poder usar JEA.</span><span class="sxs-lookup"><span data-stu-id="f7c59-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="f7c59-150">Para obtener más información, vea [Seguridad de WinRM](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="f7c59-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="f7c59-151">La comunicación remota de PowerShell está habilitada de manera predeterminada en Windows Server 2012, 2012 R2 y 2016.</span><span class="sxs-lookup"><span data-stu-id="f7c59-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="f7c59-152">Puede habilitar la comunicación remota de PowerShell si ejecuta el siguiente comando en una ventana de PowerShell con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="f7c59-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="f7c59-153">Habilitar el registro de bloques de script y módulos de PowerShell (opcional)</span><span class="sxs-lookup"><span data-stu-id="f7c59-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="f7c59-154">En los siguientes pasos se habilita el registro para todas las acciones de PowerShell del sistema.</span><span class="sxs-lookup"><span data-stu-id="f7c59-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="f7c59-155">El registro de módulos de PowerShell no es necesario para JEA, pero se recomienda activarlo para asegurarse de que los comandos que ejecutan los usuarios se registran en una ubicación central.</span><span class="sxs-lookup"><span data-stu-id="f7c59-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="f7c59-156">Puede configurar la directiva de registro de módulos de PowerShell mediante la directiva de grupo.</span><span class="sxs-lookup"><span data-stu-id="f7c59-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="f7c59-157">Abra el Editor de directivas de grupo local en una estación de trabajo o un objeto de directiva de grupo en la consola de administración de directivas de grupo en un controlador de dominio de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="f7c59-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="f7c59-158">Vaya a **Configuración del equipo\\Plantillas administrativas\\Componentes de Windows\\Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f7c59-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="f7c59-159">Haga doble clic en **Activar registro de módulos**.</span><span class="sxs-lookup"><span data-stu-id="f7c59-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="f7c59-160">Haga clic en **Habilitado**.</span><span class="sxs-lookup"><span data-stu-id="f7c59-160">Click **Enabled**</span></span>
5. <span data-ttu-id="f7c59-161">En la sección Opciones, haga clic en **Mostrar** junto a Nombres de módulos.</span><span class="sxs-lookup"><span data-stu-id="f7c59-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="f7c59-162">Escriba `*` en la ventana emergente para registrar comandos de todos los módulos.</span><span class="sxs-lookup"><span data-stu-id="f7c59-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="f7c59-163">Haga clic en **Aceptar** para establecer la directiva.</span><span class="sxs-lookup"><span data-stu-id="f7c59-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="f7c59-164">Haga doble clic en **Activar el registro de bloque de script de PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f7c59-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="f7c59-165">Haga clic en **Habilitado**.</span><span class="sxs-lookup"><span data-stu-id="f7c59-165">Click **Enabled**</span></span>
10. <span data-ttu-id="f7c59-166">Haga clic en **Aceptar** para establecer la directiva.</span><span class="sxs-lookup"><span data-stu-id="f7c59-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="f7c59-167">(Solo en equipos unidos a un dominio) Ejecute `gpupdate` o espere a que la directiva de grupo procese la directiva actualizada y aplique la configuración.</span><span class="sxs-lookup"><span data-stu-id="f7c59-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="f7c59-168">También puede habilitar la transcripción de PowerShell de todo el sistema a través de la directiva de grupo.</span><span class="sxs-lookup"><span data-stu-id="f7c59-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f7c59-169">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="f7c59-169">Next steps</span></span>

[<span data-ttu-id="f7c59-170">Crear un archivo de funcionalidad de rol</span><span class="sxs-lookup"><span data-stu-id="f7c59-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="f7c59-171">Crear un archivo de configuración de sesión</span><span class="sxs-lookup"><span data-stu-id="f7c59-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="f7c59-172">Vea también</span><span class="sxs-lookup"><span data-stu-id="f7c59-172">See also</span></span>

[<span data-ttu-id="f7c59-173">Seguridad de WinRM</span><span class="sxs-lookup"><span data-stu-id="f7c59-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="f7c59-174">PowerShell ♥ the Blue Team</span><span class="sxs-lookup"><span data-stu-id="f7c59-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
