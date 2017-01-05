---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psgallery_status
ms.technology: powershell
ms.openlocfilehash: 40ebfa510abe647d80a85fa15f0b777d697ffdfb
ms.sourcegitcommit: 26c3acb3dae9f7c3868a5f0d6144e9e1a0d02557
translationtype: HT
---
<a name="powershell-gallery-status"></a>Estado de la Galería de PowerShell
=========================


## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>15/12/2016: No se pueden enviar correos electrónicos a través del sitio web de PowerShellGallery

__Resumen del impacto__: entre el 13/12/2016 y el 15/12/2016, los administradores de la Galería de PowerShell no han recibido ningún mensaje enviado mediante las opciones Ponerse en contacto con los propietarios, Administrar propietarios, Ponerse en contacto con soporte técnico o Notificar abuso.  
__Causa principal__: los ingenieros han identificado la causa como un problema de autenticación con el servidor SMTP.  
__Resolución__: los ingenieros han podido resolver el problema de autenticación y restaurar la conexión con el servidor SMTP.  
__Pasos siguientes__: si ha usado los vínculos Ponerse en contacto con los propietarios, Administrar propietarios, Ponerse en contacto con soporte técnico o Notificar abuso para enviar un correo a cgadmin@microsoft.com durante este tiempo y no hemos respondido, vuelva a intentarlo. Disculpe las molestias.  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>10/8/2016 - Resuelto: no se pueden enviar correos electrónicos a cgadmin@microsoft.com

__Resumen del impacto__: entre los días 5/8/2016 y 10/8/2016, los clientes no pudieron enviar correos electrónicos a cgadmin@microsoft.com, ni usar la característica Póngase en contacto con nosotros.  
__Causa principal__: los ingenieros identificaron que la causa era un cambio de configuración de la cuenta de correo electrónico.  
__Resolución__: los ingenieros trabajaron para resolver el problema de configuración.  
__Pasos siguientes__: si ha usado el vínculo Póngase en contacto con nosotros o ha enviado un correo a cgadmin@microsoft.com durante este tiempo y no hemos respondido, vuelva a intentarlo. Gracias por su paciencia.



## <a name="7132016---download-items-failed"></a>13/7/2016 - Error al descargar elementos

__Resumen del impacto__: entre los días 11/7/2016 y 13/7/2016, un subconjunto de clientes experimentó problemas al descargar elementos de la Galería de PowerShell. Probablemente, el problema se manifestó en el siguiente mensaje de error que se ha devuelto de Install-Module/Install-Script y Save-Module/Save-Script:

```PowerShell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

__Causa principal preliminar__: los ingenieros identificaron un problema con Azure Content Deliver Network (CDN), que se implementó en la Galería de PowerShell el 11/7/2016.  
__Mitigación__: los ingenieros han deshabilitado Azure CDN en la Galería de PowerShell.  
__Pasos siguientes__: investigar la causa principal subyacente y desarrollar una solución para evitar incidencias futuras.


## <a name="5192016---download-items-failed"></a>19/5/2016 - Error al descargar elementos
__Resumen del impacto__: entre los días 17/5/2016 y 19/5/2016, un subconjunto de clientes experimentó problemas al descargar elementos de la Galería de PowerShell. Probablemente, el problema se manifestó en el siguiente mensaje de error que se ha devuelto de Install-Module/Install-Script y Save-Module/Save-Script:

```PowerShell
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

__Causa principal preliminar__: los ingenieros identificaron una interrupción en el proveedor subyacente de Azure Content Deliver Network (CDN), que se implementó en la Galería de PowerShell el 17/5/2016.  
__Mitigación__: los ingenieros han deshabilitado Azure CDN en la Galería de PowerShell.  
__Pasos siguientes__: investigar la causa principal subyacente y desarrollar una solución para evitar incidencias futuras.

