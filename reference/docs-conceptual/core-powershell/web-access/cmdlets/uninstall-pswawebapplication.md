---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: uninstall pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 5fe608b3bfbb90f842f16c1f5a8c51879589cf6d
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="2e8e1-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="2e8e1-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="2e8e1-104">SINOPSIS</span><span class="sxs-lookup"><span data-stu-id="2e8e1-104">SYNOPSIS</span></span>

<span data-ttu-id="2e8e1-105">Desinstala la aplicación web de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="2e8e1-106">SINTAXIS</span><span class="sxs-lookup"><span data-stu-id="2e8e1-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="2e8e1-107">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="2e8e1-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="2e8e1-108">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="2e8e1-108">DESCRIPTION</span></span>

<span data-ttu-id="2e8e1-109">El cmdlet **Uninstall-PswaWebApplication** desinstala la aplicación web de Windows PowerShell y quita de IIS el sitio web.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="2e8e1-110">El cmdlet no desinstala IIS ni ninguna otra característica instalada, ya que eran necesarias para que se ejecutara Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="2e8e1-111">PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="2e8e1-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="2e8e1-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="2e8e1-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="2e8e1-113">Indica que se han eliminado los certificados de prueba creados por el cmdlet **Install\_PswaWebApplication** (con el parámetro **UseTestCertificate**).</span><span class="sxs-lookup"><span data-stu-id="2e8e1-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="2e8e1-114">Solo se quita el certificado de prueba que tiene el mismo nombre que el que ha creado el cmdlet **Install-PswaWebApplication**.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="2e8e1-115">Alias</span><span class="sxs-lookup"><span data-stu-id="2e8e1-115">Aliases</span></span>                              | <span data-ttu-id="2e8e1-116">ninguno</span><span class="sxs-lookup"><span data-stu-id="2e8e1-116">none</span></span>                                 |
| <span data-ttu-id="2e8e1-117">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-117">Required?</span></span>                            | <span data-ttu-id="2e8e1-118">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-118">false</span></span>                                |
| <span data-ttu-id="2e8e1-119">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-119">Position?</span></span>                            | <span data-ttu-id="2e8e1-120">llamada</span><span class="sxs-lookup"><span data-stu-id="2e8e1-120">named</span></span>                                |
| <span data-ttu-id="2e8e1-121">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="2e8e1-121">Default Value</span></span>                        | <span data-ttu-id="2e8e1-122">true</span><span class="sxs-lookup"><span data-stu-id="2e8e1-122">true</span></span>                                 |
| <span data-ttu-id="2e8e1-123">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2e8e1-124">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-124">false</span></span>                                |
| <span data-ttu-id="2e8e1-125">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2e8e1-126">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="2e8e1-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="2e8e1-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="2e8e1-128">Especifica el nombre de la aplicación web que se va a desinstalar.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="2e8e1-129">Alias</span><span class="sxs-lookup"><span data-stu-id="2e8e1-129">Aliases</span></span>                              | <span data-ttu-id="2e8e1-130">ninguno</span><span class="sxs-lookup"><span data-stu-id="2e8e1-130">none</span></span>                                 |
| <span data-ttu-id="2e8e1-131">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-131">Required?</span></span>                            | <span data-ttu-id="2e8e1-132">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-132">false</span></span>                                |
| <span data-ttu-id="2e8e1-133">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-133">Position?</span></span>                            | <span data-ttu-id="2e8e1-134">1</span><span class="sxs-lookup"><span data-stu-id="2e8e1-134">1</span></span>                                    |
| <span data-ttu-id="2e8e1-135">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="2e8e1-135">Default Value</span></span>                        | <span data-ttu-id="2e8e1-136">pswa</span><span class="sxs-lookup"><span data-stu-id="2e8e1-136">pswa</span></span>                                 |
| <span data-ttu-id="2e8e1-137">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2e8e1-138">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-138">false</span></span>                                |
| <span data-ttu-id="2e8e1-139">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2e8e1-140">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="2e8e1-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="2e8e1-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="2e8e1-142">Especifica el nombre del sitio web donde está instalada la aplicación web.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="2e8e1-143">Alias</span><span class="sxs-lookup"><span data-stu-id="2e8e1-143">Aliases</span></span>                              | <span data-ttu-id="2e8e1-144">ninguno</span><span class="sxs-lookup"><span data-stu-id="2e8e1-144">none</span></span>                                 |
| <span data-ttu-id="2e8e1-145">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-145">Required?</span></span>                            | <span data-ttu-id="2e8e1-146">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-146">false</span></span>                                |
| <span data-ttu-id="2e8e1-147">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-147">Position?</span></span>                            | <span data-ttu-id="2e8e1-148">llamada</span><span class="sxs-lookup"><span data-stu-id="2e8e1-148">named</span></span>                                |
| <span data-ttu-id="2e8e1-149">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="2e8e1-149">Default Value</span></span>                        | <span data-ttu-id="2e8e1-150">Sitio web predeterminado</span><span class="sxs-lookup"><span data-stu-id="2e8e1-150">Default Web Site</span></span>                     |
| <span data-ttu-id="2e8e1-151">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2e8e1-152">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-152">false</span></span>                                |
| <span data-ttu-id="2e8e1-153">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2e8e1-154">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="2e8e1-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2e8e1-155">-Confirm</span></span>

<span data-ttu-id="2e8e1-156">Solicita confirmación antes de ejecutar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="2e8e1-157">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-157">Required?</span></span>                            | <span data-ttu-id="2e8e1-158">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-158">false</span></span>                                |
| <span data-ttu-id="2e8e1-159">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-159">Position?</span></span>                            | <span data-ttu-id="2e8e1-160">llamada</span><span class="sxs-lookup"><span data-stu-id="2e8e1-160">named</span></span>                                |
| <span data-ttu-id="2e8e1-161">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="2e8e1-161">Default Value</span></span>                        | <span data-ttu-id="2e8e1-162">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-162">false</span></span>                                |
| <span data-ttu-id="2e8e1-163">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2e8e1-164">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-164">false</span></span>                                |
| <span data-ttu-id="2e8e1-165">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2e8e1-166">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="2e8e1-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2e8e1-167">-WhatIf</span></span>

<span data-ttu-id="2e8e1-168">Muestra lo que sucedería si se ejecutara el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2e8e1-169">El cmdlet no se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="2e8e1-170">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-170">Required?</span></span>                            | <span data-ttu-id="2e8e1-171">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-171">false</span></span>                                |
| <span data-ttu-id="2e8e1-172">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-172">Position?</span></span>                            | <span data-ttu-id="2e8e1-173">llamada</span><span class="sxs-lookup"><span data-stu-id="2e8e1-173">named</span></span>                                |
| <span data-ttu-id="2e8e1-174">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="2e8e1-174">Default Value</span></span>                        | <span data-ttu-id="2e8e1-175">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-175">false</span></span>                                |
| <span data-ttu-id="2e8e1-176">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2e8e1-177">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-177">false</span></span>                                |
| <span data-ttu-id="2e8e1-178">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="2e8e1-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2e8e1-179">falso</span><span class="sxs-lookup"><span data-stu-id="2e8e1-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="2e8e1-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="2e8e1-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="2e8e1-181">Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="2e8e1-182">Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2e8e1-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="2e8e1-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="2e8e1-183">INPUTS</span></span>

<span data-ttu-id="2e8e1-184">Este cmdlet no toma ninguna entrada.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="2e8e1-185">SALIDAS</span><span class="sxs-lookup"><span data-stu-id="2e8e1-185">OUTPUTS</span></span>

<span data-ttu-id="2e8e1-186">Este cmdlet no devuelve ningún resultado.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="2e8e1-187">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="2e8e1-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="2e8e1-188">EJEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="2e8e1-188">EXAMPLE 1</span></span>

<span data-ttu-id="2e8e1-189">Este comando desinstala la aplicación web de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="2e8e1-190">Puede usar este cmdlet para desinstalar la aplicación web de Windows PowerShell si la instaló con los valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="2e8e1-191">EJEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="2e8e1-191">EXAMPLE 2</span></span>

<span data-ttu-id="2e8e1-192">Este comando desinstala la aplicación web de Windows PowerShell y elimina el certificado de prueba asociado a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="2e8e1-193">Puede usar este cmdlet para desinstalar la aplicación web de Windows PowerShell si la instaló con los valores predeterminados y creó un certificado de prueba.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="2e8e1-194">EJEMPLO 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="2e8e1-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="2e8e1-195">Este comando desinstala la aplicación web de Windows PowerShell si durante la instalación se especificó una aplicación y un sitio web personalizados.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="2e8e1-196">El comando quita el sitio web denominado *MySite* y la aplicación denominada *TestApplication* y especifica que también se eliminan los certificados de prueba asociados a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2e8e1-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="2e8e1-197">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="2e8e1-197">Related topics</span></span>

- [<span data-ttu-id="2e8e1-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2e8e1-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="2e8e1-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2e8e1-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="2e8e1-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="2e8e1-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="2e8e1-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2e8e1-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="2e8e1-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2e8e1-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
