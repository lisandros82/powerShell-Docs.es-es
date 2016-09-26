Estado de la Galería de PowerShell
=========================


## 10/8/2016 - Resuelto: No se pueden enviar correos electrónicos a cgadmin@microsoft.com

__Resumen del impacto__: entre los días 5/8/2016 y 10/8/2016, los clientes no pudieron enviar correos electrónicos a cgadmin@microsoft.com ni usar la característica Póngase en contacto con nosotros.  
__Causa principal__: los ingenieros identificaron que la causa era un cambio de configuración de la cuenta de correo electrónico.  
__Resolución__: los ingenieros trabajaron para resolver el problema de configuración.  
__Pasos siguientes__: si ha usado el vínculo Póngase en contacto con nosotros o ha enviado un correo a cgadmin@microsoft.com durante este tiempo y no hemos respondido, vuelva a intentarlo. Gracias por su paciencia.



## 13/7/2016 - Error al descargar elementos

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


## 19/5/2016 - Error al descargar elementos
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


<!--HONumber=Sep16_HO2-->


