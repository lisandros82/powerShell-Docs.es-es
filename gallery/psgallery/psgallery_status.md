---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_status
ms.openlocfilehash: 08d09ce83b5133598152186e12fc8ced90c36a88
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a><span data-ttu-id="dc14f-103">Estado de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="dc14f-103">PowerShell Gallery Status</span></span>
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a><span data-ttu-id="dc14f-104">10-10-2017: La Galería de PowerShell no estuvo disponible durante dos horas 10-10-2017</span><span class="sxs-lookup"><span data-stu-id="dc14f-104">10/10/2017 - PowerShell Gallery unavailable for 2 hours 10/10/17</span></span>

<span data-ttu-id="dc14f-105">__Resumen del impacto__: la Galería de PowerShell experimentó un período de latencia muy alta, lo que generó problemas de conexión intermitente, los que comenzaron aproximadamente a las 5:00 p.m. (PDT) del 10-10-2017.</span><span class="sxs-lookup"><span data-stu-id="dc14f-105">__Summary of Impact__: The PowerShell Gallery experienced a period of very high latency, resulting in intermittent connection issues, beginning approximately 5pm (PDT) 10/10/17.</span></span> <span data-ttu-id="dc14f-106">Durante la resolución del problema, el sitio estuvo sin conexión por dos horas, desde aproximadamente las 10:00 p.m. (PDT).</span><span class="sxs-lookup"><span data-stu-id="dc14f-106">While resolving the issue, the site was taken offline for 2 hours starting approximately 10pm (PDT).</span></span> <span data-ttu-id="dc14f-107">El sitio se restauró poco antes de la medianoche del 10-10-2017.</span><span class="sxs-lookup"><span data-stu-id="dc14f-107">The site was restored shortly before midnight 10/10/2017.</span></span>

<span data-ttu-id="dc14f-108">__Causa principal__: se sigue investigando la causa principal de la latencia alta.</span><span class="sxs-lookup"><span data-stu-id="dc14f-108">__Root Cause__: The root cause of the high latency is still being investigated.</span></span>

<span data-ttu-id="dc14f-109">__Resolución__: hubo que desconectar los servicios web y restaurarlos para poder solucionar el problema principal.</span><span class="sxs-lookup"><span data-stu-id="dc14f-109">__Resolution__: The web services had to be taken offline and restored in order to address the primary issue.</span></span>

<span data-ttu-id="dc14f-110">__Pasos siguientes__: se investiga la causa principal del problema original.</span><span class="sxs-lookup"><span data-stu-id="dc14f-110">__Next Steps__: The root cause for the original issue is being investigated.</span></span>

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="dc14f-111">01-06-2017: Implementar en Azure Automation actualmente no disponible</span><span class="sxs-lookup"><span data-stu-id="dc14f-111">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="dc14f-112">__Resumen del impacto__: la implementación de elementos con dependencias de Azure Automation desde la Galería de PowerShell actualmente no está disponible.</span><span class="sxs-lookup"><span data-stu-id="dc14f-112">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="dc14f-113">La importación de elementos de la Galería de PowerShell desde Azure Automation sigue disponible.</span><span class="sxs-lookup"><span data-stu-id="dc14f-113">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>

<span data-ttu-id="dc14f-114">__Causa raíz__: los elementos que tienen dependencias de otros y que se implementaron anteriormente en Azure Automation no se implementarán en Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="dc14f-114">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="dc14f-115">Los ingenieros identificaron un problema con la forma en que se generan las plantillas de ARM para elementos con dependencias para la funcionalidad Implementar en Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="dc14f-115">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="dc14f-116">__Resolución__: los ingenieros están trabajando para solucionar el problema.</span><span class="sxs-lookup"><span data-stu-id="dc14f-116">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="dc14f-117">La solución alternativa actual para los usuarios es importar el elemento de la Galería de PowerShell desde Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="dc14f-117">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span>

<span data-ttu-id="dc14f-118">__Pasos siguientes__: los ingenieros publicarán próximamente la corrección.</span><span class="sxs-lookup"><span data-stu-id="dc14f-118">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="dc14f-119">Mientras tanto, use la solución alternativa recomendada.</span><span class="sxs-lookup"><span data-stu-id="dc14f-119">In the meantime, please use the recommended workaround.</span></span>


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="dc14f-120">11/04/2017: los usuarios no pueden iniciar sesión con cuentas de Azure Active Directory (AAD)</span><span class="sxs-lookup"><span data-stu-id="dc14f-120">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="dc14f-121">__Resumen de impacto__: algunos usuarios no podían iniciar sesión en Galería de PowerShell con sus cuentas de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="dc14f-121">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span>

<span data-ttu-id="dc14f-122">__Causa principal__: durante una actualización para interactuar de forma más segura con AAD, se perdió un cambio de configuración.</span><span class="sxs-lookup"><span data-stu-id="dc14f-122">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span>
<span data-ttu-id="dc14f-123">Las pruebas realizadas para validar el cambio no incluían ciertos tipos de cuentas de AAD, por lo que la implementación siguió adelante.</span><span class="sxs-lookup"><span data-stu-id="dc14f-123">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="dc14f-124">__Resolución__: los ingenieros han identificado el valor de configuración que faltaba y han corregido el problema.</span><span class="sxs-lookup"><span data-stu-id="dc14f-124">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span>

<span data-ttu-id="dc14f-125">__Pasos siguientes__: modificaremos nuestras pruebas para incluir un conjunto más amplio de tipos de cuentas de AAD.</span><span class="sxs-lookup"><span data-stu-id="dc14f-125">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="dc14f-126">27/03/2017 - RESUELTO - No se pueden ver páginas individuales de módulo y script</span><span class="sxs-lookup"><span data-stu-id="dc14f-126">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="dc14f-127">__Resumen de impacto__: los vínculos directos a páginas individuales de módulo y script en https://www.powershellgallery.com estaban rotos.</span><span class="sxs-lookup"><span data-stu-id="dc14f-127">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="dc14f-128">Esto se ha notificado en todas las regiones.</span><span class="sxs-lookup"><span data-stu-id="dc14f-128">This was being reported across all the regions.</span></span> <span data-ttu-id="dc14f-129">Esto no afectó a los cmdlet de PowerShellGet, es decir, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module y Publish-Script continuaban funcionando.</span><span class="sxs-lookup"><span data-stu-id="dc14f-129">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="dc14f-130">__Causa raíz__: los ingenieros identificaron que la causa era un problema al mostrar los botones de medios sociales, como Facebook, en la página.</span><span class="sxs-lookup"><span data-stu-id="dc14f-130">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>

<span data-ttu-id="dc14f-131">__Resolución__: los ingenieros deshabilitaron la información de la cuenta de Facebook para corregir el problema.</span><span class="sxs-lookup"><span data-stu-id="dc14f-131">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="dc14f-132">__Pasos siguientes__: se ha abierto un seguimiento interno del problema para corregir el uso de la API de Facebook.</span><span class="sxs-lookup"><span data-stu-id="dc14f-132">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="dc14f-133">15/12/2016: No se pueden enviar correos electrónicos a través del sitio web de PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="dc14f-133">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="dc14f-134">__Resumen del impacto__: entre el 13/12/2016 y el 15/12/2016, los administradores de la Galería de PowerShell no han recibido ningún mensaje enviado mediante las opciones Ponerse en contacto con los propietarios, Administrar propietarios, Ponerse en contacto con soporte técnico o Notificar abuso.</span><span class="sxs-lookup"><span data-stu-id="dc14f-134">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="dc14f-135">__Causa principal__: los ingenieros han identificado la causa como un problema de autenticación con el servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="dc14f-135">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>
<span data-ttu-id="dc14f-136">__Resolución__: los ingenieros han podido resolver el problema de autenticación y restaurar la conexión con el servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="dc14f-136">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>
<span data-ttu-id="dc14f-137">__Pasos siguientes__: si ha usado los vínculos Ponerse en contacto con los propietarios, Administrar propietarios, Ponerse en contacto con soporte técnico o Notificar abuso para enviar un correo a cgadmin@microsoft.com durante este tiempo y no hemos respondido, vuelva a intentarlo.</span><span class="sxs-lookup"><span data-stu-id="dc14f-137">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="dc14f-138">Disculpe las molestias.</span><span class="sxs-lookup"><span data-stu-id="dc14f-138">We apologize for the inconvenience.</span></span>



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="dc14f-139">10/8/2016 - Resuelto: no se pueden enviar correos electrónicos a cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="dc14f-139">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="dc14f-140">__Resumen del impacto__: entre los días 5/8/2016 y 10/8/2016, los clientes no pudieron enviar correos electrónicos a cgadmin@microsoft.com ni usar la característica Póngase en contacto con nosotros.</span><span class="sxs-lookup"><span data-stu-id="dc14f-140">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>
<span data-ttu-id="dc14f-141">__Causa principal__: los ingenieros identificaron que la causa era un cambio de configuración de la cuenta de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="dc14f-141">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>
<span data-ttu-id="dc14f-142">__Resolución__: los ingenieros trabajaron para resolver el problema de configuración.</span><span class="sxs-lookup"><span data-stu-id="dc14f-142">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>
<span data-ttu-id="dc14f-143">__Pasos siguientes__: si ha usado el vínculo Póngase en contacto con nosotros o ha enviado un correo a cgadmin@microsoft.com durante este tiempo y no hemos respondido, vuelva a intentarlo.</span><span class="sxs-lookup"><span data-stu-id="dc14f-143">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="dc14f-144">Gracias por su paciencia.</span><span class="sxs-lookup"><span data-stu-id="dc14f-144">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="dc14f-145">13/7/2016 - Error al descargar elementos</span><span class="sxs-lookup"><span data-stu-id="dc14f-145">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="dc14f-146">__Resumen del impacto__: entre los días 11/7/2016 y 13/7/2016, un subconjunto de clientes experimentó problemas al descargar elementos de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc14f-146">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="dc14f-147">Probablemente, el problema se manifestó en el siguiente mensaje de error que se ha devuelto de Install-Module/Install-Script y Save-Module/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="dc14f-147">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
PS C:\> Install-Module xStorage
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because:
End of Central Directory record could not be found. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ...
$null = PackageManagement\Install-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult:
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}'
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

<span data-ttu-id="dc14f-148">__Causa principal preliminar__: los ingenieros identificaron un problema con Azure Content Deliver Network (CDN), que se implementó en la Galería de PowerShell el 11/7/2016.</span><span class="sxs-lookup"><span data-stu-id="dc14f-148">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>
<span data-ttu-id="dc14f-149">__Mitigación__: los ingenieros han deshabilitado Azure CDN en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc14f-149">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="dc14f-150">__Pasos siguientes__: investigar la causa principal subyacente y desarrollar una solución para evitar incidencias futuras.</span><span class="sxs-lookup"><span data-stu-id="dc14f-150">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="dc14f-151">19/5/2016 - Error al descargar elementos</span><span class="sxs-lookup"><span data-stu-id="dc14f-151">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="dc14f-152">__Resumen del impacto__: entre los días 17/5/2016 y 19/5/2016, un subconjunto de clientes experimentó problemas al descargar elementos de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc14f-152">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="dc14f-153">Probablemente, el problema se manifestó en el siguiente mensaje de error que se ha devuelto de Install-Module/Install-Script y Save-Module/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="dc14f-153">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because:
End of Central Directory record could not be found.
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install.
WARNING: Package 'AzureRM' failed to install.
VERBOSE: Module 'AzureRM.Network' was saved successfully.
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the
module 'AzureRM'.
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully.
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 +
$null = PackageManagement\Save-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ +
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage)
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage
```

<span data-ttu-id="dc14f-154">__Causa principal preliminar__: los ingenieros identificaron una interrupción en el proveedor subyacente de Azure Content Deliver Network (CDN), que se implementó en la Galería de PowerShell el 17/5/2016.</span><span class="sxs-lookup"><span data-stu-id="dc14f-154">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>
<span data-ttu-id="dc14f-155">__Mitigación__: los ingenieros han deshabilitado Azure CDN en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc14f-155">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="dc14f-156">__Pasos siguientes__: investigar la causa principal subyacente y desarrollar una solución para evitar incidencias futuras.</span><span class="sxs-lookup"><span data-stu-id="dc14f-156">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>