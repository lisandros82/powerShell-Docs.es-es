---
title: Ciclo de vida de soporte técnico de PowerShell Core
description: Directivas que rigen la compatibilidad para PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: b8dd4891ecf245b87c3fe2fa61cd241a12209b57
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854375"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="820be-103">Ciclo de vida de soporte técnico de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="820be-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="820be-104">PowerShell Core es un conjunto independiente de herramientas y componentes que se entrega, se instala y se configura por separado de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="820be-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="820be-105">Por lo tanto, PowerShell Core no se incluye en los contratos de licencias de Windows 7/8.1/10 o Windows Server.</span><span class="sxs-lookup"><span data-stu-id="820be-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="820be-106">Sin embargo, PowerShell Core se admite en los contratos de soporte técnico convencionales de Microsoft, incluido el soporte técnico [Premier][], los [contratos Enterprise de Microsoft][enterprise-agreement] y [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="820be-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="820be-107">También existe la opción de pagar para obtener [soporte técnico asistido][] para PowerShell Core. Basta con enviar una solicitud de soporte técnico para su problema.</span><span class="sxs-lookup"><span data-stu-id="820be-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="820be-108">Soporte técnico de la comunidad</span><span class="sxs-lookup"><span data-stu-id="820be-108">Community Support</span></span>

<span data-ttu-id="820be-109">También ofrecemos [soporte técnico de la comunidad][] en GitHub, donde puede registrar un problema o un error, o solicitar una característica.</span><span class="sxs-lookup"><span data-stu-id="820be-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="820be-110">Además puede obtener ayuda de otros miembros de la comunidad en [Microsoft Community][] en general o en [PowerShell Tech Community][] de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="820be-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="820be-111">No se ofrece ninguna garantía de que la comunidad abordará o resolverá oportunamente su problema.</span><span class="sxs-lookup"><span data-stu-id="820be-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="820be-112">Si tiene algún problema que requiera atención inmediata, deberá usar las opciones convencionales de soporte técnico de pago.</span><span class="sxs-lookup"><span data-stu-id="820be-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="820be-113">Ciclo de vida de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="820be-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="820be-114">PowerShell Core ha adoptado la [directiva moderna de ciclo de vida de Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="820be-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="820be-115">Este ciclo de vida de soporte técnico está diseñado para mantener a los clientes actualizados con las versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="820be-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="820be-116">La rama de la versión 6.x de PowerShell Core se actualizará aproximadamente una vez cada seis meses (por ejemplo, 6.0, 6.1, 6.2, etc.)</span><span class="sxs-lookup"><span data-stu-id="820be-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="820be-117">Debe realizar la actualización en los seis meses siguientes al lanzamiento de cada nueva versión secundaria para seguir recibiendo soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="820be-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="820be-118">Por ejemplo, si PowerShell Core 6.1 se lanza el 1 de julio de 1, 2018, deberá actualizar a PowerShell Core 6.1 antes del 1 de enero de 1, 2019 para conservar el soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="820be-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="820be-119">Debe realizar la actualización en los 30 días siguientes al lanzamiento de cada nueva versión de revisión para seguir recibiendo soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="820be-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="820be-120">Por ejemplo, si ejecuta PowerShell Core 6.1 y la versión 6.1.3 se lanzó el 19 de febrero de 2019, se esperaría que actualice a PowerShell Core 6.1.3 antes del 21 de marzo de 2019, es decir, 30 días después del lanzamiento para conservar el soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="820be-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="820be-121">Si se considera necesaria alguna corrección, se lanzará en la siguiente actualización acumulativa.</span><span class="sxs-lookup"><span data-stu-id="820be-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

<span data-ttu-id="820be-122">La directiva moderna de ciclo de vida también requiere que Microsoft avise a los clientes con 12 meses de antelación antes de interrumpir el soporte técnico para un producto (es decir, PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="820be-122">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="820be-123">Por último, se espera que PowerShell Core adoptará el enfoque de "mantenimiento a largo plazo".</span><span class="sxs-lookup"><span data-stu-id="820be-123">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="820be-124">En este enfoque de mantenimiento, solo se requerirían actualizaciones de seguridad y mantenimiento para conservar el soporte técnico en una rama/versión específica de 6.x.</span><span class="sxs-lookup"><span data-stu-id="820be-124">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="820be-125">Plataformas admitidas</span><span class="sxs-lookup"><span data-stu-id="820be-125">Supported platforms</span></span>

<span data-ttu-id="820be-126">En la tabla siguiente podrá ver la plataforma en la que la versión de PowerShell Core que está utilizando es compatible oficialmente.</span><span class="sxs-lookup"><span data-stu-id="820be-126">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="820be-127">Nuestra comunidad también ha aportado paquetes para algunas plataformas, pero no se admiten oficialmente.</span><span class="sxs-lookup"><span data-stu-id="820be-127">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="820be-128">Estos paquetes se marcan como `Community` en la tabla.</span><span class="sxs-lookup"><span data-stu-id="820be-128">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="820be-129">Las plataformas mencionadas como `Experimental` no se admiten oficialmente, pero están disponibles para experimentación y comentarios.</span><span class="sxs-lookup"><span data-stu-id="820be-129">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="820be-130">6.1</span><span class="sxs-lookup"><span data-stu-id="820be-130">6.1</span></span>         | <span data-ttu-id="820be-131">6.2</span><span class="sxs-lookup"><span data-stu-id="820be-131">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="820be-132">Windows 7, 8.1 y 10</span><span class="sxs-lookup"><span data-stu-id="820be-132">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="820be-133">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-133">Supported</span></span>   | <span data-ttu-id="820be-134">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-134">Supported</span></span>   |
| <span data-ttu-id="820be-135">Windows Server 2008 R2, 2012 R2 y 2016</span><span class="sxs-lookup"><span data-stu-id="820be-135">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="820be-136">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-136">Supported</span></span>   | <span data-ttu-id="820be-137">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-137">Supported</span></span>   |
| <span data-ttu-id="820be-138">[Canal semianual de Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="820be-138">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="820be-139">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-139">Supported</span></span>   | <span data-ttu-id="820be-140">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-140">Supported</span></span>   |
| <span data-ttu-id="820be-141">Ubuntu 16.04 y 18.04</span><span class="sxs-lookup"><span data-stu-id="820be-141">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="820be-142">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-142">Supported</span></span>   | <span data-ttu-id="820be-143">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-143">Supported</span></span>   |
| <span data-ttu-id="820be-144">Ubuntu 18.10 (mediante un paquete Snap)</span><span class="sxs-lookup"><span data-stu-id="820be-144">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="820be-145">Comunidad</span><span class="sxs-lookup"><span data-stu-id="820be-145">Community</span></span>   | <span data-ttu-id="820be-146">Comunidad</span><span class="sxs-lookup"><span data-stu-id="820be-146">Community</span></span>   |
| <span data-ttu-id="820be-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="820be-147">Debian 9</span></span>                                          | <span data-ttu-id="820be-148">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-148">Supported</span></span>   | <span data-ttu-id="820be-149">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-149">Supported</span></span>   |
| <span data-ttu-id="820be-150">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="820be-150">CentOS 7</span></span>                                          | <span data-ttu-id="820be-151">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-151">Supported</span></span>   | <span data-ttu-id="820be-152">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-152">Supported</span></span>   |
| <span data-ttu-id="820be-153">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="820be-153">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="820be-154">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-154">Supported</span></span>   | <span data-ttu-id="820be-155">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-155">Supported</span></span>   |
| <span data-ttu-id="820be-156">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="820be-156">openSUSE 42.3</span></span>                                     | <span data-ttu-id="820be-157">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-157">Supported</span></span>   | <span data-ttu-id="820be-158">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-158">Supported</span></span>   |
| <span data-ttu-id="820be-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="820be-159">Fedora 28</span></span>                                         | <span data-ttu-id="820be-160">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-160">Supported</span></span>   | <span data-ttu-id="820be-161">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-161">Supported</span></span>   |
| <span data-ttu-id="820be-162">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="820be-162">macOS 10.12+</span></span>                                      | <span data-ttu-id="820be-163">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-163">Supported</span></span>   | <span data-ttu-id="820be-164">Compatible</span><span class="sxs-lookup"><span data-stu-id="820be-164">Supported</span></span>   |
| <span data-ttu-id="820be-165">Arch</span><span class="sxs-lookup"><span data-stu-id="820be-165">Arch</span></span>                                              | <span data-ttu-id="820be-166">Comunidad</span><span class="sxs-lookup"><span data-stu-id="820be-166">Community</span></span>   | <span data-ttu-id="820be-167">Comunidad</span><span class="sxs-lookup"><span data-stu-id="820be-167">Community</span></span>   |
| <span data-ttu-id="820be-168">Raspbian</span><span class="sxs-lookup"><span data-stu-id="820be-168">Raspbian</span></span>                                          | <span data-ttu-id="820be-169">Comunidad</span><span class="sxs-lookup"><span data-stu-id="820be-169">Community</span></span>   | <span data-ttu-id="820be-170">Comunidad</span><span class="sxs-lookup"><span data-stu-id="820be-170">Community</span></span>   |
| <span data-ttu-id="820be-171">Kali</span><span class="sxs-lookup"><span data-stu-id="820be-171">Kali</span></span>                                              | <span data-ttu-id="820be-172">Comunidad</span><span class="sxs-lookup"><span data-stu-id="820be-172">Community</span></span>   | <span data-ttu-id="820be-173">Comunidad</span><span class="sxs-lookup"><span data-stu-id="820be-173">Community</span></span>   |
| <span data-ttu-id="820be-174">AppImage (funciona en varias plataformas Linux)</span><span class="sxs-lookup"><span data-stu-id="820be-174">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="820be-175">Comunidad</span><span class="sxs-lookup"><span data-stu-id="820be-175">Community</span></span>   | <span data-ttu-id="820be-176">Comunidad</span><span class="sxs-lookup"><span data-stu-id="820be-176">Community</span></span>   |
| [<span data-ttu-id="820be-177">Paquete Snap</span><span class="sxs-lookup"><span data-stu-id="820be-177">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="820be-178">Ver nota</span><span class="sxs-lookup"><span data-stu-id="820be-178">See note</span></span>    | <span data-ttu-id="820be-179">Ver nota</span><span class="sxs-lookup"><span data-stu-id="820be-179">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="820be-180">Los paquetes Snap se admiten del mismo modo que la distribución en la que se ejecuta el paquete.</span><span class="sxs-lookup"><span data-stu-id="820be-180">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="820be-181">Fin del ciclo de vida de PowerShell</span><span class="sxs-lookup"><span data-stu-id="820be-181">PowerShell release end of life</span></span>

<span data-ttu-id="820be-182">Según la sección [Ciclo de vida de PowerShell Core](#lifecycle-of-powershell-core), en la tabla siguiente se muestran las fechas en las que diversas versiones dejarán de tener soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="820be-182">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="820be-183">Version</span><span class="sxs-lookup"><span data-stu-id="820be-183">Version</span></span> | <span data-ttu-id="820be-184">Fin de la vida útil</span><span class="sxs-lookup"><span data-stu-id="820be-184">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="820be-185">6.0</span><span class="sxs-lookup"><span data-stu-id="820be-185">6.0</span></span>     | <span data-ttu-id="820be-186">13 de febrero de 2019</span><span class="sxs-lookup"><span data-stu-id="820be-186">February 13, 2019</span></span>             |
| <span data-ttu-id="820be-187">6.1</span><span class="sxs-lookup"><span data-stu-id="820be-187">6.1</span></span>     | <span data-ttu-id="820be-188">28 de septiembre de 2019</span><span class="sxs-lookup"><span data-stu-id="820be-188">September 28, 2019</span></span>            |
| <span data-ttu-id="820be-189">6.2</span><span class="sxs-lookup"><span data-stu-id="820be-189">6.2</span></span>     | <span data-ttu-id="820be-190">6 meses después de las versiones 7</span><span class="sxs-lookup"><span data-stu-id="820be-190">6 months after 7 releases</span></span>     |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="820be-191">Plataformas que están fuera de soporte técnico</span><span class="sxs-lookup"><span data-stu-id="820be-191">Platforms, which are out of support</span></span>

<span data-ttu-id="820be-192">Cuando una versión de la plataforma llega al final de su vida útil definida por el propietario de la plataforma, PowerShell Core también dejará de ofrecer soporte técnico a esa versión de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="820be-192">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="820be-193">Los paquetes previamente publicados seguirán estando disponibles para los clientes que necesiten acceso, pero ya no se proporcionará soporte técnico formal ni actualizaciones de ningún tipo.</span><span class="sxs-lookup"><span data-stu-id="820be-193">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="820be-194">Por lo tanto, los propietarios de distribución finalizaron el soporte técnico para las versiones siguientes y ya no se admiten.</span><span class="sxs-lookup"><span data-stu-id="820be-194">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="820be-195">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="820be-195">OS</span></span>       | <span data-ttu-id="820be-196">Version</span><span class="sxs-lookup"><span data-stu-id="820be-196">Version</span></span> | <span data-ttu-id="820be-197">Fin de la vida útil</span><span class="sxs-lookup"><span data-stu-id="820be-197">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="820be-198">Fedora</span><span class="sxs-lookup"><span data-stu-id="820be-198">Fedora</span></span>   | <span data-ttu-id="820be-199">24</span><span class="sxs-lookup"><span data-stu-id="820be-199">24</span></span>      | [<span data-ttu-id="820be-200">Agosto de 2017</span><span class="sxs-lookup"><span data-stu-id="820be-200">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="820be-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="820be-201">Fedora</span></span>   | <span data-ttu-id="820be-202">25</span><span class="sxs-lookup"><span data-stu-id="820be-202">25</span></span>      | [<span data-ttu-id="820be-203">Diciembre de 2017</span><span class="sxs-lookup"><span data-stu-id="820be-203">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="820be-204">Fedora</span><span class="sxs-lookup"><span data-stu-id="820be-204">Fedora</span></span>   | <span data-ttu-id="820be-205">26</span><span class="sxs-lookup"><span data-stu-id="820be-205">26</span></span>      | [<span data-ttu-id="820be-206">Mayo de 2018</span><span class="sxs-lookup"><span data-stu-id="820be-206">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="820be-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="820be-207">openSUSE</span></span> | <span data-ttu-id="820be-208">42.1</span><span class="sxs-lookup"><span data-stu-id="820be-208">42.1</span></span>    | [<span data-ttu-id="820be-209">Mayo de 2017</span><span class="sxs-lookup"><span data-stu-id="820be-209">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="820be-210">openSUSE</span><span class="sxs-lookup"><span data-stu-id="820be-210">openSUSE</span></span> | <span data-ttu-id="820be-211">42.2</span><span class="sxs-lookup"><span data-stu-id="820be-211">42.2</span></span>    | [<span data-ttu-id="820be-212">Enero de 2018</span><span class="sxs-lookup"><span data-stu-id="820be-212">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="820be-213">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="820be-213">Ubuntu</span></span>   | <span data-ttu-id="820be-214">16.10</span><span class="sxs-lookup"><span data-stu-id="820be-214">16.10</span></span>   | [<span data-ttu-id="820be-215">Julio de 2017</span><span class="sxs-lookup"><span data-stu-id="820be-215">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="820be-216">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="820be-216">Ubuntu</span></span>   | <span data-ttu-id="820be-217">17.04</span><span class="sxs-lookup"><span data-stu-id="820be-217">17.04</span></span>   | [<span data-ttu-id="820be-218">Enero de 2018</span><span class="sxs-lookup"><span data-stu-id="820be-218">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="820be-219">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="820be-219">Ubuntu</span></span>   | <span data-ttu-id="820be-220">17.10</span><span class="sxs-lookup"><span data-stu-id="820be-220">17.10</span></span>   | [<span data-ttu-id="820be-221">Julio de 2018</span><span class="sxs-lookup"><span data-stu-id="820be-221">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="820be-222">Debian</span><span class="sxs-lookup"><span data-stu-id="820be-222">Debian</span></span>   | <span data-ttu-id="820be-223">8</span><span class="sxs-lookup"><span data-stu-id="820be-223">8</span></span>       | [<span data-ttu-id="820be-224">Junio de 2018</span><span class="sxs-lookup"><span data-stu-id="820be-224">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="820be-225">Fedora</span><span class="sxs-lookup"><span data-stu-id="820be-225">Fedora</span></span>   | <span data-ttu-id="820be-226">27</span><span class="sxs-lookup"><span data-stu-id="820be-226">27</span></span>      | [<span data-ttu-id="820be-227">Noviembre de 2018</span><span class="sxs-lookup"><span data-stu-id="820be-227">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="820be-228">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="820be-228">Ubuntu</span></span>   | <span data-ttu-id="820be-229">14.04</span><span class="sxs-lookup"><span data-stu-id="820be-229">14.04</span></span>   | [<span data-ttu-id="820be-230">Abril de 2019</span><span class="sxs-lookup"><span data-stu-id="820be-230">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="820be-231">Notas sobre las licencias</span><span class="sxs-lookup"><span data-stu-id="820be-231">Notes on licensing</span></span>

<span data-ttu-id="820be-232">PowerShell Core se publica bajo la [licencia de MIT][].</span><span class="sxs-lookup"><span data-stu-id="820be-232">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="820be-233">De acuerdo con esta licencia y sin un contrato de soporte técnico de pago, los usuarios están limitados al [soporte técnico de la comunidad][].</span><span class="sxs-lookup"><span data-stu-id="820be-233">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="820be-234">Con el soporte técnico de la comunidad, Microsoft no garantiza la capacidad de respuesta ni correcciones para el usuario.</span><span class="sxs-lookup"><span data-stu-id="820be-234">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="820be-235">Módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="820be-235">Windows PowerShell Module</span></span>

<span data-ttu-id="820be-236">El soporte técnico para PowerShell Core no incluye módulos de producto, a menos que dichos módulos admitan explícitamente PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="820be-236">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="820be-237">Por ejemplo, el uso del módulo `ActiveDirectory` que se suministra como parte de Windows Server es un escenario que no se admite.</span><span class="sxs-lookup"><span data-stu-id="820be-237">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="820be-238">Sin embargo, los módulos que no admiten explícitamente PowerShell Core podrían ser compatibles en algunos casos.</span><span class="sxs-lookup"><span data-stu-id="820be-238">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="820be-239">Si instala el módulo [`WindowsPSModulePath`][] puede agregar `PSModulePath` de Windows PowerShell a `PSModulePath` de PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="820be-239">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="820be-240">En primer lugar, instale el módulo `WindowsPSModulePath` desde la Galería de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="820be-240">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="820be-241">Después de instalar este módulo, ejecute el cmdlet `Add-WindowsPSModulePath` para agregar `PSModulePath` de Windows PowerShell a PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="820be-241">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="820be-242">Características experimentales</span><span class="sxs-lookup"><span data-stu-id="820be-242">Experimental features</span></span>

<span data-ttu-id="820be-243">Las [características experimentales][] están limitadas al [soporte técnico de la comunidad](#community-support).</span><span class="sxs-lookup"><span data-stu-id="820be-243">[Experimental features][] are limited to [community support](#community-support).</span></span>

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Soporte técnico de la comunidad]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[Soporte técnico asistido]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Licencia de MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
["WindowsPSModulePath"]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Características experimentales]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
