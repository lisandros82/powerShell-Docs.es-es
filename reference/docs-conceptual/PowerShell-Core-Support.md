# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="d46ba-101">Ciclo de vida de soporte técnico de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d46ba-101">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="d46ba-102">PowerShell Core es un conjunto independiente de herramientas y componentes que se entrega, se instala y se configura por separado de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d46ba-102">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="d46ba-103">Por lo tanto, PowerShell Core no se incluye en los contratos de licencias de Windows 7/8.1/10 o Windows Server.</span><span class="sxs-lookup"><span data-stu-id="d46ba-103">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="d46ba-104">Sin embargo, PowerShell Core se admite en los contratos de soporte técnico convencionales de Microsoft, incluido el soporte técnico [Premier][], los [contratos Enterprise de Microsoft][enterprise-agreement] y [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="d46ba-104">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="d46ba-105">También existe la opción de pagar para obtener [soporte técnico asistido][] para PowerShell Core. Basta con enviar una solicitud de soporte técnico para su problema.</span><span class="sxs-lookup"><span data-stu-id="d46ba-105">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="d46ba-106">También ofrecemos [soporte técnico de la comunidad][] en GitHub, donde puede registrar un problema o un error, o solicitar una característica.</span><span class="sxs-lookup"><span data-stu-id="d46ba-106">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="d46ba-107">Como alternativa, puede obtener ayuda de otros miembros de la comunidad en [Microsoft Community][] en general o en [PowerShell Tech Community][] de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d46ba-107">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="d46ba-108">No se ofrece ninguna garantía de que su problema se aborde o se resuelva oportunamente.</span><span class="sxs-lookup"><span data-stu-id="d46ba-108">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="d46ba-109">Si tiene algún problema que requiera atención inmediata, deberá usar las opciones convencionales de soporte técnico de pago.</span><span class="sxs-lookup"><span data-stu-id="d46ba-109">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="d46ba-110">Ciclo de vida de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d46ba-110">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="d46ba-111">PowerShell Core ha adoptado la [directiva moderna de ciclo de vida de Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="d46ba-111">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="d46ba-112">Este ciclo de vida de soporte técnico está diseñado para mantener a los clientes actualizados con las versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="d46ba-112">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="d46ba-113">La rama de la versión 6.x de PowerShell Core se actualizará aproximadamente una vez cada seis meses (por ejemplo, 6.0, 6.1, 6.2, etc.).</span><span class="sxs-lookup"><span data-stu-id="d46ba-113">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d46ba-114">Debe realizar la actualización en los seis meses siguientes al lanzamiento de cada nueva versión secundaria para seguir recibiendo soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="d46ba-114">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="d46ba-115">Por ejemplo, si PowerShell Core 6.1 se lanza el 1 de julio de 2018, deberá actualizar a PowerShell Core 6.1 antes del 1 de enero de 2019 para conservar el soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="d46ba-115">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![Ciclo de vida de rama de PowerShell Core][lifecycle-chart]

<span data-ttu-id="d46ba-117">La directiva moderna de ciclo de vida también requiere que Microsoft avise a los clientes con 12 meses de antelación antes de interrumpir el soporte técnico para un producto (es decir, PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="d46ba-117">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="d46ba-118">Esperamos que, a la larga, PowerShell Core adopte un enfoque de mantenimiento a largo plazo, que solo requeriría el mantenimiento y las actualizaciones de seguridad para conservar el soporte técnico de una rama o versión específica de 6.x.</span><span class="sxs-lookup"><span data-stu-id="d46ba-118">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="d46ba-119">Plataformas admitidas</span><span class="sxs-lookup"><span data-stu-id="d46ba-119">Supported platforms</span></span>

<span data-ttu-id="d46ba-120">PowerShell Core se admite oficialmente en las plataformas siguientes:</span><span class="sxs-lookup"><span data-stu-id="d46ba-120">PowerShell Core is officially supported on the following platforms:</span></span>

* <span data-ttu-id="d46ba-121">Windows 7, 8.1 y 10</span><span class="sxs-lookup"><span data-stu-id="d46ba-121">Windows 7, 8.1, and 10</span></span>
* <span data-ttu-id="d46ba-122">Windows Server 2008 R2, 2012 R2 y 2016</span><span class="sxs-lookup"><span data-stu-id="d46ba-122">Windows Server 2008 R2, 2012 R2, 2016</span></span>
* <span data-ttu-id="d46ba-123">[Canal semianual de Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="d46ba-123">[Windows Server Semi-Annual Channel][semi-annual]</span></span>
* <span data-ttu-id="d46ba-124">Ubuntu 14.04, 16.04 y 17.04</span><span class="sxs-lookup"><span data-stu-id="d46ba-124">Ubuntu 14.04, 16.04, and 17.04</span></span>
* <span data-ttu-id="d46ba-125">Debian 8.7+ y 9</span><span class="sxs-lookup"><span data-stu-id="d46ba-125">Debian 8.7+, and 9</span></span>
* <span data-ttu-id="d46ba-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d46ba-126">CentOS 7</span></span>
* <span data-ttu-id="d46ba-127">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="d46ba-127">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="d46ba-128">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="d46ba-128">OpenSUSE 42.2</span></span>
* <span data-ttu-id="d46ba-129">Fedora 25 y 26</span><span class="sxs-lookup"><span data-stu-id="d46ba-129">Fedora 25, 26</span></span>
* <span data-ttu-id="d46ba-130">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="d46ba-130">macOS 10.12+</span></span>

<span data-ttu-id="d46ba-131">Nuestra comunidad también ha aportado paquetes para las plataformas siguientes, pero no se admiten oficialmente:</span><span class="sxs-lookup"><span data-stu-id="d46ba-131">Our community has also contributed packages for the following platforms, but they are not officially suppported:</span></span>

* <span data-ttu-id="d46ba-132">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="d46ba-132">Arch Linux</span></span>
* <span data-ttu-id="d46ba-133">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="d46ba-133">Kali Linux</span></span>
* <span data-ttu-id="d46ba-134">AppImage (funciona en varias plataformas Linux)</span><span class="sxs-lookup"><span data-stu-id="d46ba-134">AppImage (works on multiple Linux platforms)</span></span>

## <a name="notes-on-licensing"></a><span data-ttu-id="d46ba-135">Notas sobre las licencias</span><span class="sxs-lookup"><span data-stu-id="d46ba-135">Notes on licensing</span></span>

<span data-ttu-id="d46ba-136">PowerShell Core se publica bajo la [licencia de MIT][].</span><span class="sxs-lookup"><span data-stu-id="d46ba-136">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="d46ba-137">De acuerdo con esta licencia, y en ausencia de un contrato de soporte técnico de pago, los usuarios están limitados al [soporte técnico de la comunidad][].</span><span class="sxs-lookup"><span data-stu-id="d46ba-137">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="d46ba-138">Con el soporte técnico de la comunidad, Microsoft no garantiza la capacidad de respuesta ni correcciones para el usuario.</span><span class="sxs-lookup"><span data-stu-id="d46ba-138">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="d46ba-139">Módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d46ba-139">Windows PowerShell Module</span></span>

<span data-ttu-id="d46ba-140">El soporte técnico para PowerShell Core no se extiende a otros módulos de producto, a menos que dichos módulos admitan explícitamente PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="d46ba-140">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="d46ba-141">Por ejemplo, el uso del módulo `ActiveDirectory` que se suministra como parte de Windows Server es un escenario que no se admite.</span><span class="sxs-lookup"><span data-stu-id="d46ba-141">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="d46ba-142">Sin embargo, los módulos que no admiten explícitamente PowerShell Core podrían ser compatibles en algunos casos.</span><span class="sxs-lookup"><span data-stu-id="d46ba-142">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="d46ba-143">Si instala el módulo [`WindowsPSModulePath`][], puede agregar `PSModulePath` de Windows PowerShell a `PSModulePath` de PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="d46ba-143">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="d46ba-144">En primer lugar, instale el módulo `WindowsPSModulePath` desde la Galería de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d46ba-144">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="d46ba-145">Después de instalar este módulo, ejecute el cmdlet `Add-WindowsPSModulePath` para agregar `PSModulePath` de Windows PowerShell a PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="d46ba-145">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[soporte técnico de la comunidad]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[soporte técnico asistido]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[licencia de MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
["WindowsPSModulePath"]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
