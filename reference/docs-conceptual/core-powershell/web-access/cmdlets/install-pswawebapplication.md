---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 68455d9490f7d5c33c1a928ac262a76a78ad7128
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="b7a63-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="b7a63-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="b7a63-104">SINOPSIS</span><span class="sxs-lookup"><span data-stu-id="b7a63-104">SYNOPSIS</span></span>

<span data-ttu-id="b7a63-105">Configura en IIS la aplicación web de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="b7a63-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7a63-106">SINTAXIS</span><span class="sxs-lookup"><span data-stu-id="b7a63-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="b7a63-107">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b7a63-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="b7a63-108">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="b7a63-108">DESCRIPTION</span></span>

<span data-ttu-id="b7a63-109">El cmdlet **Install-PswaWebApplication** configura la aplicación web de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="b7a63-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="b7a63-110">Este cmdlet instala la aplicación web, la asocia a un sitio web y, de forma opcional, crea un certificado SSL de prueba mediante el parámetro **useTestCertificate**.</span><span class="sxs-lookup"><span data-stu-id="b7a63-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="b7a63-111">Por motivos de seguridad, los administradores web no deben usar ningún certificado de prueba para los entornos de producción.</span><span class="sxs-lookup"><span data-stu-id="b7a63-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="b7a63-112">PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="b7a63-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="b7a63-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="b7a63-113">-UseTestCertificate</span></span>

<span data-ttu-id="b7a63-114">Especifica que se crea un certificado de prueba.</span><span class="sxs-lookup"><span data-stu-id="b7a63-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="b7a63-115">Si este parámetro se establece en true, este cmdlet crea un certificado de prueba y configura la aplicación web de Windows PowerShell Web Access para usar el certificado para las solicitudes HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b7a63-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="b7a63-116">Si este parámetro se establece en false, no se creará ningún certificado o enlace.</span><span class="sxs-lookup"><span data-stu-id="b7a63-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="b7a63-117">Establezca este valor en false si se usa otro certificado para Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="b7a63-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="b7a63-118">Alias</span><span class="sxs-lookup"><span data-stu-id="b7a63-118">Aliases</span></span>                              | <span data-ttu-id="b7a63-119">ninguno</span><span class="sxs-lookup"><span data-stu-id="b7a63-119">none</span></span>                                 |
| <span data-ttu-id="b7a63-120">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b7a63-120">Required?</span></span>                            | <span data-ttu-id="b7a63-121">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-121">false</span></span>                                |
| <span data-ttu-id="b7a63-122">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b7a63-122">Position?</span></span>                            | <span data-ttu-id="b7a63-123">llamada</span><span class="sxs-lookup"><span data-stu-id="b7a63-123">named</span></span>                                |
| <span data-ttu-id="b7a63-124">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b7a63-124">Default Value</span></span>                        | <span data-ttu-id="b7a63-125">true</span><span class="sxs-lookup"><span data-stu-id="b7a63-125">true</span></span>                                 |
| <span data-ttu-id="b7a63-126">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b7a63-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b7a63-127">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-127">false</span></span>                                |
| <span data-ttu-id="b7a63-128">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b7a63-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b7a63-129">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="b7a63-130">-WebApplicationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="b7a63-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="b7a63-131">Especifica el nombre de la aplicación web.</span><span class="sxs-lookup"><span data-stu-id="b7a63-131">Specifies the name for your web application.</span></span> <span data-ttu-id="b7a63-132">Aparece como la última parte de la dirección URL de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="b7a63-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="b7a63-133">Alias</span><span class="sxs-lookup"><span data-stu-id="b7a63-133">Aliases</span></span>                              | <span data-ttu-id="b7a63-134">ninguno</span><span class="sxs-lookup"><span data-stu-id="b7a63-134">none</span></span>                                 |
| <span data-ttu-id="b7a63-135">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b7a63-135">Required?</span></span>                            | <span data-ttu-id="b7a63-136">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-136">false</span></span>                                |
| <span data-ttu-id="b7a63-137">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b7a63-137">Position?</span></span>                            | <span data-ttu-id="b7a63-138">1</span><span class="sxs-lookup"><span data-stu-id="b7a63-138">1</span></span>                                    |
| <span data-ttu-id="b7a63-139">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b7a63-139">Default Value</span></span>                        | <span data-ttu-id="b7a63-140">pswa</span><span class="sxs-lookup"><span data-stu-id="b7a63-140">pswa</span></span>                                 |
| <span data-ttu-id="b7a63-141">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b7a63-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b7a63-142">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-142">false</span></span>                                |
| <span data-ttu-id="b7a63-143">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b7a63-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b7a63-144">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="b7a63-145">-WebSiteName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="b7a63-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="b7a63-146">Especifica el nombre del sitio web del Servidor web (IIS) en el que se va a instalar esta aplicación web de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="b7a63-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="b7a63-147">Alias</span><span class="sxs-lookup"><span data-stu-id="b7a63-147">Aliases</span></span>                              | <span data-ttu-id="b7a63-148">ninguno</span><span class="sxs-lookup"><span data-stu-id="b7a63-148">none</span></span>                                 |
| <span data-ttu-id="b7a63-149">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b7a63-149">Required?</span></span>                            | <span data-ttu-id="b7a63-150">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-150">false</span></span>                                |
| <span data-ttu-id="b7a63-151">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b7a63-151">Position?</span></span>                            | <span data-ttu-id="b7a63-152">llamada</span><span class="sxs-lookup"><span data-stu-id="b7a63-152">named</span></span>                                |
| <span data-ttu-id="b7a63-153">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b7a63-153">Default Value</span></span>                        | <span data-ttu-id="b7a63-154">Sitio web predeterminado</span><span class="sxs-lookup"><span data-stu-id="b7a63-154">Default Web Site</span></span>                     |
| <span data-ttu-id="b7a63-155">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b7a63-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b7a63-156">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-156">false</span></span>                                |
| <span data-ttu-id="b7a63-157">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b7a63-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b7a63-158">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="b7a63-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b7a63-159">-Confirm</span></span>

<span data-ttu-id="b7a63-160">Solicita confirmación antes de ejecutar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7a63-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="b7a63-161">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b7a63-161">Required?</span></span>                            | <span data-ttu-id="b7a63-162">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-162">false</span></span>                                |
| <span data-ttu-id="b7a63-163">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b7a63-163">Position?</span></span>                            | <span data-ttu-id="b7a63-164">llamada</span><span class="sxs-lookup"><span data-stu-id="b7a63-164">named</span></span>                                |
| <span data-ttu-id="b7a63-165">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b7a63-165">Default Value</span></span>                        | <span data-ttu-id="b7a63-166">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-166">false</span></span>                                |
| <span data-ttu-id="b7a63-167">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b7a63-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b7a63-168">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-168">false</span></span>                                |
| <span data-ttu-id="b7a63-169">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b7a63-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b7a63-170">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="b7a63-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b7a63-171">-WhatIf</span></span>

<span data-ttu-id="b7a63-172">Muestra lo que sucedería si se ejecutara el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7a63-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b7a63-173">El cmdlet no se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="b7a63-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="b7a63-174">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b7a63-174">Required?</span></span>                            | <span data-ttu-id="b7a63-175">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-175">false</span></span>                                |
| <span data-ttu-id="b7a63-176">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b7a63-176">Position?</span></span>                            | <span data-ttu-id="b7a63-177">llamada</span><span class="sxs-lookup"><span data-stu-id="b7a63-177">named</span></span>                                |
| <span data-ttu-id="b7a63-178">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b7a63-178">Default Value</span></span>                        | <span data-ttu-id="b7a63-179">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-179">false</span></span>                                |
| <span data-ttu-id="b7a63-180">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b7a63-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b7a63-181">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-181">false</span></span>                                |
| <span data-ttu-id="b7a63-182">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b7a63-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b7a63-183">falso</span><span class="sxs-lookup"><span data-stu-id="b7a63-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="b7a63-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="b7a63-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="b7a63-185">Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="b7a63-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="b7a63-186">Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b7a63-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="b7a63-187">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="b7a63-187">INPUTS</span></span>

<span data-ttu-id="b7a63-188">Este cmdlet no toma ninguna entrada.</span><span class="sxs-lookup"><span data-stu-id="b7a63-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="b7a63-189">SALIDAS</span><span class="sxs-lookup"><span data-stu-id="b7a63-189">OUTPUTS</span></span>

<span data-ttu-id="b7a63-190">Este cmdlet no genera ninguna salida.</span><span class="sxs-lookup"><span data-stu-id="b7a63-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="b7a63-191">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="b7a63-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="b7a63-192">EJEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="b7a63-192">EXAMPLE 1</span></span>

<span data-ttu-id="b7a63-193">Este ejemplo instala la aplicación web PSWA con los valores predeterminados de los parámetros **WebApplicationName** (*pswa*) y **WebSiteName** (*sitio web predeterminado*).</span><span class="sxs-lookup"><span data-stu-id="b7a63-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="b7a63-194">EJEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="b7a63-194">EXAMPLE 2</span></span>

<span data-ttu-id="b7a63-195">Este ejemplo instala la aplicación web PSWA con un certificado de prueba y usando los valores predeterminados de los parámetros **WebApplicationName** y **WebSiteName**.</span><span class="sxs-lookup"><span data-stu-id="b7a63-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="b7a63-196">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="b7a63-196">Related topics</span></span>

- [<span data-ttu-id="b7a63-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b7a63-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="b7a63-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b7a63-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="b7a63-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b7a63-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="b7a63-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b7a63-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)