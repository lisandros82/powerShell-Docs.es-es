---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psgalleryint_status
ms.technology: powershell
ms.openlocfilehash: 58f06ca061a4f171288e75b30698910c701f1da1
ms.sourcegitcommit: ba8ed836799ef465e507fa1b8d341ba38459d863
translationtype: HT
---
<a name="powershell-gallery-status"></a>Estado de la Galería de PowerShell
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27/03/2017 - RESUELTO - No se pueden ver páginas individuales de módulo y script

__Resumen de impacto__: los vínculos a páginas individuales de módulo y script en https://www.powershellgallery.com estaban rotos. Esto se ha notificado en todas las regiones. Esto no afectó a los cmdlet de PowerShellGet, es decir, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module y Publish-Script continuaban funcionando.

__Causa raíz__: los ingenieros identificaron que la causa era un problema al mostrar los botones de medios sociales, como Facebook, en la página.  

__Resolución__: los ingenieros deshabilitaron la información de la cuenta de Facebook para corregir el problema.

__Pasos siguientes__: se ha abierto un seguimiento interno del problema para corregir el uso de la API de Facebook.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>15/12/2016: No se pueden enviar correos electrónicos a través del sitio web de PowerShellGallery

__Resumen del impacto__: entre el 13/12/2016 y el 15/12/2016, los administradores de la Galería de PowerShell no han recibido ningún mensaje enviado mediante las opciones Ponerse en contacto con los propietarios, Administrar propietarios, Ponerse en contacto con soporte técnico o Notificar abuso.  
__Causa principal__: los ingenieros han identificado la causa como un problema de autenticación con el servidor SMTP.  
__Resolución__: los ingenieros han podido resolver el problema de autenticación y restaurar la conexión con el servidor SMTP.  
__Pasos siguientes__: si ha usado los vínculos Ponerse en contacto con los propietarios, Administrar propietarios, Ponerse en contacto con soporte técnico o Notificar abuso para enviar un correo a cgadmin@microsoft.com durante este tiempo y no hemos respondido, vuelva a intentarlo. Disculpe las molestias.   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>10/8/2016 - Resuelto: no se pueden enviar correos electrónicos a cgadmin@microsoft.com
__Resumen del impacto__: entre los días 5/8/2016 y 10/8/2016, los clientes no pudieron enviar correos electrónicos a cgadmin@microsoft.com ni usar la característica Póngase en contacto con nosotros.  
__Causa principal__: los ingenieros identificaron que la causa era un cambio de configuración de la cuenta de correo electrónico.  
__Resolución__: los ingenieros trabajaron para resolver el problema de configuración.  
__Pasos siguientes__: si ha usado el vínculo Póngase en contacto con nosotros o ha enviado un correo a cgadmin@microsoft.com durante este tiempo y no hemos respondido, vuelva a intentarlo. Gracias por su paciencia.


