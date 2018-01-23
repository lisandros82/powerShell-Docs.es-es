---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell, cmdlet
ms.date: 2016-12-12
title: uninstall pswawebapplication
ms.technology: powershell
ms.openlocfilehash: cc54c94426d754ff2d3bf658e3e92083f02cd6c7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="03101-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="03101-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="03101-104">SINOPSIS</span><span class="sxs-lookup"><span data-stu-id="03101-104">SYNOPSIS</span></span>

<span data-ttu-id="03101-105">Desinstala la aplicación web de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="03101-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="03101-106">SINTAXIS</span><span class="sxs-lookup"><span data-stu-id="03101-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="03101-107">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="03101-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="03101-108">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="03101-108">DESCRIPTION</span></span>

<span data-ttu-id="03101-109">El cmdlet **Uninstall-PswaWebApplication** desinstala la aplicación web de Windows PowerShell y quita de IIS el sitio web.</span><span class="sxs-lookup"><span data-stu-id="03101-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="03101-110">El cmdlet no desinstala IIS ni ninguna otra característica instalada, ya que eran necesarias para que se ejecutara Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03101-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="03101-111">PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="03101-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="03101-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="03101-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="03101-113">Indica que se han eliminado los certificados de prueba creados por el cmdlet **Install\_PswaWebApplication** (con el parámetro **UseTestCertificate**).</span><span class="sxs-lookup"><span data-stu-id="03101-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="03101-114">Solo se quita el certificado de prueba que tiene el mismo nombre que el que ha creado el cmdlet **Install-PswaWebApplication**.</span><span class="sxs-lookup"><span data-stu-id="03101-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="03101-115">Alias</span><span class="sxs-lookup"><span data-stu-id="03101-115">Aliases</span></span>                              | <span data-ttu-id="03101-116">ninguno</span><span class="sxs-lookup"><span data-stu-id="03101-116">none</span></span>                                 |
| <span data-ttu-id="03101-117">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="03101-117">Required?</span></span>                            | <span data-ttu-id="03101-118">falso</span><span class="sxs-lookup"><span data-stu-id="03101-118">false</span></span>                                |
| <span data-ttu-id="03101-119">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="03101-119">Position?</span></span>                            | <span data-ttu-id="03101-120">llamada</span><span class="sxs-lookup"><span data-stu-id="03101-120">named</span></span>                                |
| <span data-ttu-id="03101-121">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="03101-121">Default Value</span></span>                        | <span data-ttu-id="03101-122">true</span><span class="sxs-lookup"><span data-stu-id="03101-122">true</span></span>                                 |
| <span data-ttu-id="03101-123">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="03101-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="03101-124">falso</span><span class="sxs-lookup"><span data-stu-id="03101-124">false</span></span>                                |
| <span data-ttu-id="03101-125">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="03101-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="03101-126">falso</span><span class="sxs-lookup"><span data-stu-id="03101-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="03101-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="03101-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="03101-128">Especifica el nombre de la aplicación web que se va a desinstalar.</span><span class="sxs-lookup"><span data-stu-id="03101-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="03101-129">Alias</span><span class="sxs-lookup"><span data-stu-id="03101-129">Aliases</span></span>                              | <span data-ttu-id="03101-130">ninguno</span><span class="sxs-lookup"><span data-stu-id="03101-130">none</span></span>                                 |
| <span data-ttu-id="03101-131">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="03101-131">Required?</span></span>                            | <span data-ttu-id="03101-132">falso</span><span class="sxs-lookup"><span data-stu-id="03101-132">false</span></span>                                |
| <span data-ttu-id="03101-133">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="03101-133">Position?</span></span>                            | <span data-ttu-id="03101-134">1</span><span class="sxs-lookup"><span data-stu-id="03101-134">1</span></span>                                    |
| <span data-ttu-id="03101-135">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="03101-135">Default Value</span></span>                        | <span data-ttu-id="03101-136">pswa</span><span class="sxs-lookup"><span data-stu-id="03101-136">pswa</span></span>                                 |
| <span data-ttu-id="03101-137">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="03101-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="03101-138">falso</span><span class="sxs-lookup"><span data-stu-id="03101-138">false</span></span>                                |
| <span data-ttu-id="03101-139">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="03101-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="03101-140">falso</span><span class="sxs-lookup"><span data-stu-id="03101-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="03101-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="03101-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="03101-142">Especifica el nombre del sitio web donde está instalada la aplicación web.</span><span class="sxs-lookup"><span data-stu-id="03101-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="03101-143">Alias</span><span class="sxs-lookup"><span data-stu-id="03101-143">Aliases</span></span>                              | <span data-ttu-id="03101-144">ninguno</span><span class="sxs-lookup"><span data-stu-id="03101-144">none</span></span>                                 |
| <span data-ttu-id="03101-145">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="03101-145">Required?</span></span>                            | <span data-ttu-id="03101-146">falso</span><span class="sxs-lookup"><span data-stu-id="03101-146">false</span></span>                                |
| <span data-ttu-id="03101-147">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="03101-147">Position?</span></span>                            | <span data-ttu-id="03101-148">llamada</span><span class="sxs-lookup"><span data-stu-id="03101-148">named</span></span>                                |
| <span data-ttu-id="03101-149">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="03101-149">Default Value</span></span>                        | <span data-ttu-id="03101-150">Sitio web predeterminado</span><span class="sxs-lookup"><span data-stu-id="03101-150">Default Web Site</span></span>                     |
| <span data-ttu-id="03101-151">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="03101-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="03101-152">falso</span><span class="sxs-lookup"><span data-stu-id="03101-152">false</span></span>                                |
| <span data-ttu-id="03101-153">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="03101-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="03101-154">falso</span><span class="sxs-lookup"><span data-stu-id="03101-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="03101-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="03101-155">-Confirm</span></span>

<span data-ttu-id="03101-156">Solicita confirmación antes de ejecutar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03101-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="03101-157">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="03101-157">Required?</span></span>                            | <span data-ttu-id="03101-158">falso</span><span class="sxs-lookup"><span data-stu-id="03101-158">false</span></span>                                |
| <span data-ttu-id="03101-159">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="03101-159">Position?</span></span>                            | <span data-ttu-id="03101-160">llamada</span><span class="sxs-lookup"><span data-stu-id="03101-160">named</span></span>                                |
| <span data-ttu-id="03101-161">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="03101-161">Default Value</span></span>                        | <span data-ttu-id="03101-162">falso</span><span class="sxs-lookup"><span data-stu-id="03101-162">false</span></span>                                |
| <span data-ttu-id="03101-163">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="03101-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="03101-164">falso</span><span class="sxs-lookup"><span data-stu-id="03101-164">false</span></span>                                |
| <span data-ttu-id="03101-165">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="03101-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="03101-166">falso</span><span class="sxs-lookup"><span data-stu-id="03101-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="03101-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="03101-167">-WhatIf</span></span>

<span data-ttu-id="03101-168">Muestra lo que sucedería si se ejecutara el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03101-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="03101-169">El cmdlet no se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="03101-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="03101-170">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="03101-170">Required?</span></span>                            | <span data-ttu-id="03101-171">falso</span><span class="sxs-lookup"><span data-stu-id="03101-171">false</span></span>                                |
| <span data-ttu-id="03101-172">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="03101-172">Position?</span></span>                            | <span data-ttu-id="03101-173">llamada</span><span class="sxs-lookup"><span data-stu-id="03101-173">named</span></span>                                |
| <span data-ttu-id="03101-174">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="03101-174">Default Value</span></span>                        | <span data-ttu-id="03101-175">falso</span><span class="sxs-lookup"><span data-stu-id="03101-175">false</span></span>                                |
| <span data-ttu-id="03101-176">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="03101-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="03101-177">falso</span><span class="sxs-lookup"><span data-stu-id="03101-177">false</span></span>                                |
| <span data-ttu-id="03101-178">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="03101-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="03101-179">falso</span><span class="sxs-lookup"><span data-stu-id="03101-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="03101-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="03101-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="03101-181">Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="03101-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="03101-182">Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="03101-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="03101-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="03101-183">INPUTS</span></span>

<span data-ttu-id="03101-184">Este cmdlet no toma ninguna entrada.</span><span class="sxs-lookup"><span data-stu-id="03101-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="03101-185">SALIDAS</span><span class="sxs-lookup"><span data-stu-id="03101-185">OUTPUTS</span></span>

<span data-ttu-id="03101-186">Este cmdlet no devuelve ningún resultado.</span><span class="sxs-lookup"><span data-stu-id="03101-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="03101-187">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="03101-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="03101-188">EJEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="03101-188">EXAMPLE 1</span></span>

<span data-ttu-id="03101-189">Este comando desinstala la aplicación web de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03101-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="03101-190">Puede usar este cmdlet para desinstalar la aplicación web de Windows PowerShell si la instaló con los valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="03101-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="03101-191">EJEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="03101-191">EXAMPLE 2</span></span>

<span data-ttu-id="03101-192">Este comando desinstala la aplicación web de Windows PowerShell y elimina el certificado de prueba asociado a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="03101-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="03101-193">Puede usar este cmdlet para desinstalar la aplicación web de Windows PowerShell si la instaló con los valores predeterminados y creó un certificado de prueba.</span><span class="sxs-lookup"><span data-stu-id="03101-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="03101-194">EJEMPLO 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="03101-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="03101-195">Este comando desinstala la aplicación web de Windows PowerShell si durante la instalación se especificó una aplicación y un sitio web personalizados.</span><span class="sxs-lookup"><span data-stu-id="03101-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="03101-196">El comando quita el sitio web denominado *MySite* y la aplicación denominada *TestApplication* y especifica que también se eliminan los certificados de prueba asociados a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="03101-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="03101-197">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="03101-197">Related topics</span></span>

- [<span data-ttu-id="03101-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="03101-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="03101-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="03101-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="03101-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="03101-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="03101-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="03101-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="03101-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="03101-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
