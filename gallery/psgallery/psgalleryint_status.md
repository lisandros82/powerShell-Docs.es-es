---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="9d0b7-103">Estado de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d0b7-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="9d0b7-104">27/03/2017 - RESUELTO - No se pueden ver páginas individuales de módulo y script</span><span class="sxs-lookup"><span data-stu-id="9d0b7-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="9d0b7-105">__Resumen de impacto__: los vínculos a páginas individuales de módulo y script en https://www.powershellgallery.com estaban rotos.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="9d0b7-106">Esto se ha notificado en todas las regiones.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-106">This was being reported across all the regions.</span></span> <span data-ttu-id="9d0b7-107">Esto no afectó a los cmdlet de PowerShellGet, es decir, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module y Publish-Script continuaban funcionando.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="9d0b7-108">__Causa raíz__: los ingenieros identificaron que la causa era un problema al mostrar los botones de medios sociales, como Facebook, en la página.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="9d0b7-109">__Resolución__: los ingenieros deshabilitaron la información de la cuenta de Facebook para corregir el problema.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="9d0b7-110">__Pasos siguientes__: se ha abierto un seguimiento interno del problema para corregir el uso de la API de Facebook.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="9d0b7-111">15/12/2016: No se pueden enviar correos electrónicos a través del sitio web de PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="9d0b7-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="9d0b7-112">__Resumen del impacto__: entre el 13/12/2016 y el 15/12/2016, los administradores de la Galería de PowerShell no han recibido ningún mensaje enviado mediante las opciones Ponerse en contacto con los propietarios, Administrar propietarios, Ponerse en contacto con soporte técnico o Notificar abuso.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="9d0b7-113">__Causa principal__: los ingenieros han identificado la causa como un problema de autenticación con el servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="9d0b7-114">__Resolución__: los ingenieros han podido resolver el problema de autenticación y restaurar la conexión con el servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="9d0b7-115">__Pasos siguientes__: si ha usado los vínculos Ponerse en contacto con los propietarios, Administrar propietarios, Ponerse en contacto con soporte técnico o Notificar abuso para enviar un correo a cgadmin@microsoft.com durante este tiempo y no hemos respondido, vuelva a intentarlo.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="9d0b7-116">Disculpe las molestias.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-116">We apologize for the inconvenience.</span></span>   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="9d0b7-117">10/8/2016 - Resuelto: no se pueden enviar correos electrónicos a cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="9d0b7-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="9d0b7-118">__Resumen del impacto__: entre los días 5/8/2016 y 10/8/2016, los clientes no pudieron enviar correos electrónicos a cgadmin@microsoft.com ni usar la característica Póngase en contacto con nosotros.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="9d0b7-119">__Causa principal__: los ingenieros identificaron que la causa era un cambio de configuración de la cuenta de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="9d0b7-120">__Resolución__: los ingenieros trabajaron para resolver el problema de configuración.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="9d0b7-121">__Pasos siguientes__: si ha usado el vínculo Póngase en contacto con nosotros o ha enviado un correo a cgadmin@microsoft.com durante este tiempo y no hemos respondido, vuelva a intentarlo.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="9d0b7-122">Gracias por su paciencia.</span><span class="sxs-lookup"><span data-stu-id="9d0b7-122">Thank you for your patience.</span></span>


