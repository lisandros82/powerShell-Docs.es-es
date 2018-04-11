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
<a name="powershell-gallery-status"></a>Estado de la Galería de PowerShell
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a>10-10-2017: La Galería de PowerShell no estuvo disponible durante dos horas 10-10-2017

__Resumen del impacto__: la Galería de PowerShell experimentó un período de latencia muy alta, lo que generó problemas de conexión intermitente, los que comenzaron aproximadamente a las 5:00 p.m. (PDT) del 10-10-2017. Durante la resolución del problema, el sitio estuvo sin conexión por dos horas, desde aproximadamente las 10:00 p.m. (PDT). El sitio se restauró poco antes de la medianoche del 10-10-2017.

__Causa principal__: se sigue investigando la causa principal de la latencia alta.

__Resolución__: hubo que desconectar los servicios web y restaurarlos para poder solucionar el problema principal.

__Pasos siguientes__: se investiga la causa principal del problema original.

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a>01-06-2017: Implementar en Azure Automation actualmente no disponible

__Resumen del impacto__: la implementación de elementos con dependencias de Azure Automation desde la Galería de PowerShell actualmente no está disponible.  La importación de elementos de la Galería de PowerShell desde Azure Automation sigue disponible.

__Causa raíz__: los elementos que tienen dependencias de otros y que se implementaron anteriormente en Azure Automation no se implementarán en Azure Automation. Los ingenieros identificaron un problema con la forma en que se generan las plantillas de ARM para elementos con dependencias para la funcionalidad Implementar en Azure Automation.

__Resolución__: los ingenieros están trabajando para solucionar el problema.  La solución alternativa actual para los usuarios es importar el elemento de la Galería de PowerShell desde Azure Automation.

__Pasos siguientes__: los ingenieros publicarán próximamente la corrección.  Mientras tanto, use la solución alternativa recomendada.


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>11/04/2017: los usuarios no pueden iniciar sesión con cuentas de Azure Active Directory (AAD)

__Resumen de impacto__: algunos usuarios no podían iniciar sesión en Galería de PowerShell con sus cuentas de Azure AD.

__Causa principal__: durante una actualización para interactuar de forma más segura con AAD, se perdió un cambio de configuración.
Las pruebas realizadas para validar el cambio no incluían ciertos tipos de cuentas de AAD, por lo que la implementación siguió adelante.

__Resolución__: los ingenieros han identificado el valor de configuración que faltaba y han corregido el problema.

__Pasos siguientes__: modificaremos nuestras pruebas para incluir un conjunto más amplio de tipos de cuentas de AAD.

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27/03/2017 - RESUELTO - No se pueden ver páginas individuales de módulo y script

__Resumen de impacto__: los vínculos directos a páginas individuales de módulo y script en https://www.powershellgallery.com estaban rotos. Esto se ha notificado en todas las regiones. Esto no afectó a los cmdlet de PowerShellGet, es decir, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module y Publish-Script continuaban funcionando.

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



## <a name="7132016---download-items-failed"></a>13/7/2016 - Error al descargar elementos

__Resumen del impacto__: entre los días 11/7/2016 y 13/7/2016, un subconjunto de clientes experimentó problemas al descargar elementos de la Galería de PowerShell. Probablemente, el problema se manifestó en el siguiente mensaje de error que se ha devuelto de Install-Module/Install-Script y Save-Module/Save-Script:

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

__Causa principal preliminar__: los ingenieros identificaron un problema con Azure Content Deliver Network (CDN), que se implementó en la Galería de PowerShell el 11/7/2016.
__Mitigación__: los ingenieros han deshabilitado Azure CDN en la Galería de PowerShell.
__Pasos siguientes__: investigar la causa principal subyacente y desarrollar una solución para evitar incidencias futuras.


## <a name="5192016---download-items-failed"></a>19/5/2016 - Error al descargar elementos
__Resumen del impacto__: entre los días 17/5/2016 y 19/5/2016, un subconjunto de clientes experimentó problemas al descargar elementos de la Galería de PowerShell. Probablemente, el problema se manifestó en el siguiente mensaje de error que se ha devuelto de Install-Module/Install-Script y Save-Module/Save-Script:

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

__Causa principal preliminar__: los ingenieros identificaron una interrupción en el proveedor subyacente de Azure Content Deliver Network (CDN), que se implementó en la Galería de PowerShell el 17/5/2016.
__Mitigación__: los ingenieros han deshabilitado Azure CDN en la Galería de PowerShell.
__Pasos siguientes__: investigar la causa principal subyacente y desarrollar una solución para evitar incidencias futuras.