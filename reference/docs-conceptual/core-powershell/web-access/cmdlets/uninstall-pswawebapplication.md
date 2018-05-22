---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Uninstall-PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="735bf-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="735bf-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="735bf-104">SINOPSIS</span><span class="sxs-lookup"><span data-stu-id="735bf-104">SYNOPSIS</span></span>

<span data-ttu-id="735bf-105">Desinstala la aplicación web de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="735bf-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="735bf-106">SINTAXIS</span><span class="sxs-lookup"><span data-stu-id="735bf-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="735bf-107">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="735bf-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="735bf-108">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="735bf-108">DESCRIPTION</span></span>

<span data-ttu-id="735bf-109">El cmdlet **Uninstall-PswaWebApplication** desinstala la aplicación web de Windows PowerShell y quita de IIS el sitio web.</span><span class="sxs-lookup"><span data-stu-id="735bf-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="735bf-110">El cmdlet no desinstala IIS ni ninguna otra característica instalada, ya que eran necesarias para que se ejecutara Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="735bf-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="735bf-111">PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="735bf-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="735bf-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="735bf-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="735bf-113">Indica que se han eliminado los certificados de prueba creados por el cmdlet **Install\_PswaWebApplication** (con el parámetro **UseTestCertificate**).</span><span class="sxs-lookup"><span data-stu-id="735bf-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="735bf-114">Solo se quita el certificado de prueba que tiene el mismo nombre que el que ha creado el cmdlet **Install-PswaWebApplication**.</span><span class="sxs-lookup"><span data-stu-id="735bf-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||
|-|-|
| <span data-ttu-id="735bf-115">Alias</span><span class="sxs-lookup"><span data-stu-id="735bf-115">Aliases</span></span>                              | <span data-ttu-id="735bf-116">ninguno</span><span class="sxs-lookup"><span data-stu-id="735bf-116">none</span></span>                                 |
| <span data-ttu-id="735bf-117">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="735bf-117">Required?</span></span>                            | <span data-ttu-id="735bf-118">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-118">false</span></span>                                |
| <span data-ttu-id="735bf-119">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="735bf-119">Position?</span></span>                            | <span data-ttu-id="735bf-120">llamada</span><span class="sxs-lookup"><span data-stu-id="735bf-120">named</span></span>                                |
| <span data-ttu-id="735bf-121">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="735bf-121">Default Value</span></span>                        | <span data-ttu-id="735bf-122">true</span><span class="sxs-lookup"><span data-stu-id="735bf-122">true</span></span>                                 |
| <span data-ttu-id="735bf-123">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="735bf-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="735bf-124">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-124">false</span></span>                                |
| <span data-ttu-id="735bf-125">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="735bf-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="735bf-126">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="735bf-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="735bf-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="735bf-128">Especifica el nombre de la aplicación web que se va a desinstalar.</span><span class="sxs-lookup"><span data-stu-id="735bf-128">Specifies the name of the web application to uninstall.</span></span>

|||
|-|-|
| <span data-ttu-id="735bf-129">Alias</span><span class="sxs-lookup"><span data-stu-id="735bf-129">Aliases</span></span>                              | <span data-ttu-id="735bf-130">ninguno</span><span class="sxs-lookup"><span data-stu-id="735bf-130">none</span></span>                                 |
| <span data-ttu-id="735bf-131">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="735bf-131">Required?</span></span>                            | <span data-ttu-id="735bf-132">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-132">false</span></span>                                |
| <span data-ttu-id="735bf-133">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="735bf-133">Position?</span></span>                            | <span data-ttu-id="735bf-134">1</span><span class="sxs-lookup"><span data-stu-id="735bf-134">1</span></span>                                    |
| <span data-ttu-id="735bf-135">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="735bf-135">Default Value</span></span>                        | <span data-ttu-id="735bf-136">pswa</span><span class="sxs-lookup"><span data-stu-id="735bf-136">pswa</span></span>                                 |
| <span data-ttu-id="735bf-137">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="735bf-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="735bf-138">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-138">false</span></span>                                |
| <span data-ttu-id="735bf-139">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="735bf-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="735bf-140">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="735bf-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="735bf-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="735bf-142">Especifica el nombre del sitio web donde está instalada la aplicación web.</span><span class="sxs-lookup"><span data-stu-id="735bf-142">Specifies the name of the web site where the web application is installed.</span></span>

|||
|-|-|
| <span data-ttu-id="735bf-143">Alias</span><span class="sxs-lookup"><span data-stu-id="735bf-143">Aliases</span></span>                              | <span data-ttu-id="735bf-144">ninguno</span><span class="sxs-lookup"><span data-stu-id="735bf-144">none</span></span>                                 |
| <span data-ttu-id="735bf-145">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="735bf-145">Required?</span></span>                            | <span data-ttu-id="735bf-146">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-146">false</span></span>                                |
| <span data-ttu-id="735bf-147">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="735bf-147">Position?</span></span>                            | <span data-ttu-id="735bf-148">llamada</span><span class="sxs-lookup"><span data-stu-id="735bf-148">named</span></span>                                |
| <span data-ttu-id="735bf-149">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="735bf-149">Default Value</span></span>                        | <span data-ttu-id="735bf-150">Sitio web predeterminado</span><span class="sxs-lookup"><span data-stu-id="735bf-150">Default Web Site</span></span>                     |
| <span data-ttu-id="735bf-151">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="735bf-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="735bf-152">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-152">false</span></span>                                |
| <span data-ttu-id="735bf-153">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="735bf-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="735bf-154">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="735bf-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="735bf-155">-Confirm</span></span>

<span data-ttu-id="735bf-156">Solicita confirmación antes de ejecutar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="735bf-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="735bf-157">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="735bf-157">Required?</span></span>                            | <span data-ttu-id="735bf-158">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-158">false</span></span>                                |
| <span data-ttu-id="735bf-159">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="735bf-159">Position?</span></span>                            | <span data-ttu-id="735bf-160">llamada</span><span class="sxs-lookup"><span data-stu-id="735bf-160">named</span></span>                                |
| <span data-ttu-id="735bf-161">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="735bf-161">Default Value</span></span>                        | <span data-ttu-id="735bf-162">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-162">false</span></span>                                |
| <span data-ttu-id="735bf-163">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="735bf-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="735bf-164">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-164">false</span></span>                                |
| <span data-ttu-id="735bf-165">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="735bf-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="735bf-166">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="735bf-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="735bf-167">-WhatIf</span></span>

<span data-ttu-id="735bf-168">Muestra lo que sucedería si se ejecutara el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="735bf-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="735bf-169">El cmdlet no se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="735bf-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="735bf-170">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="735bf-170">Required?</span></span>                            | <span data-ttu-id="735bf-171">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-171">false</span></span>                                |
| <span data-ttu-id="735bf-172">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="735bf-172">Position?</span></span>                            | <span data-ttu-id="735bf-173">llamada</span><span class="sxs-lookup"><span data-stu-id="735bf-173">named</span></span>                                |
| <span data-ttu-id="735bf-174">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="735bf-174">Default Value</span></span>                        | <span data-ttu-id="735bf-175">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-175">false</span></span>                                |
| <span data-ttu-id="735bf-176">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="735bf-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="735bf-177">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-177">false</span></span>                                |
| <span data-ttu-id="735bf-178">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="735bf-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="735bf-179">falso</span><span class="sxs-lookup"><span data-stu-id="735bf-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="735bf-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="735bf-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="735bf-181">Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="735bf-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="735bf-182">Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="735bf-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="735bf-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="735bf-183">INPUTS</span></span>

<span data-ttu-id="735bf-184">Este cmdlet no toma ninguna entrada.</span><span class="sxs-lookup"><span data-stu-id="735bf-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="735bf-185">SALIDAS</span><span class="sxs-lookup"><span data-stu-id="735bf-185">OUTPUTS</span></span>

<span data-ttu-id="735bf-186">Este cmdlet no devuelve ningún resultado.</span><span class="sxs-lookup"><span data-stu-id="735bf-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="735bf-187">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="735bf-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="735bf-188">EJEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="735bf-188">EXAMPLE 1</span></span>

<span data-ttu-id="735bf-189">Este comando desinstala la aplicación web de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="735bf-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="735bf-190">Puede usar este cmdlet para desinstalar la aplicación web de Windows PowerShell si la instaló con los valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="735bf-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="735bf-191">EJEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="735bf-191">EXAMPLE 2</span></span>

<span data-ttu-id="735bf-192">Este comando desinstala la aplicación web de Windows PowerShell y elimina el certificado de prueba asociado a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="735bf-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="735bf-193">Puede usar este cmdlet para desinstalar la aplicación web de Windows PowerShell si la instaló con los valores predeterminados y creó un certificado de prueba.</span><span class="sxs-lookup"><span data-stu-id="735bf-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="735bf-194">EJEMPLO 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="735bf-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="735bf-195">Este comando desinstala la aplicación web de Windows PowerShell si durante la instalación se especificó una aplicación y un sitio web personalizados.</span><span class="sxs-lookup"><span data-stu-id="735bf-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="735bf-196">El comando quita el sitio web denominado *MySite* y la aplicación denominada *TestApplication* y especifica que también se eliminan los certificados de prueba asociados a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="735bf-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="735bf-197">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="735bf-197">Related topics</span></span>

- [<span data-ttu-id="735bf-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="735bf-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="735bf-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="735bf-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="735bf-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="735bf-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="735bf-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="735bf-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="735bf-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="735bf-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)