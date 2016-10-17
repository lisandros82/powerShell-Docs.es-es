---
title: "Validaciones de firmas de configuraciones y módulos de DSC"
author: jaimeo
contributor: berheabra
translationtype: Human Translation
ms.sourcegitcommit: 5c97ca6e93d31aaffc7e2207facc7658ee36dfb4
ms.openlocfilehash: 817fadb79716e41ce8cc8f4245dedc66347ac413

---

##Validaciones de firmas de configuraciones y módulos de DSC
En DSC, los módulos y los documentos de configuración se distribuyen a las máquinas administradas desde el servidor de extracción o el servicio de extracción (en el caso del servicio de extracción de Automatización de Azure). Si el servidor o el servicio de extracción están en peligro, un atacante puede modificar las configuraciones y los módulos del servidor de extracción y propagarlos a todas las máquinas administradas, con lo que todavía más máquinas del cliente estarían en peligro. 

 Esta amenaza se soluciona en WMF 5.1. DSC admite la validación de las firmas digitales en los archivos de módulos y de configuración (.MOF). Esta característica evitará que los nodos ejecuten archivos de módulos o de configuración que no están firmados por un firmante de confianza o que se han alterado después de que los haya firmado un firmante de confianza. 



###Cómo firmar un módulo y una configuración 
***
1. Archivos de configuración (. MOFS):- El cmdlet de PowerShell existente [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) se amplía para admitir la firma de archivos MOF.  
2. Módulos:- La firma de módulos se realiza mediante la firma del catálogo de módulos correspondiente mediante los siguientes pasos:- 
    * Creación de un archivo de catálogo: un archivo de catálogo contiene una colección de algoritmos hash criptográficos o huellas digitales. Cada huella digital corresponde a un archivo que se incluye en el módulo.  Se ha agregado un nuevo cmdlet, [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), para que los usuarios puedan crear un archivo de catálogo para su módulo. Consulte los [cmdlets del catálogo](catalog-cmdlets.md) para crear archivos de catálogo. 
    * Firma del archivo de catálogo: firme el archivo de catálogo mediante [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).
    * Coloque el archivo de catálogo dentro de la carpeta del módulo.
Por convención, el archivo de catálogo del módulo debe colocarse en la carpeta del módulo y debe tener el mismo nombre que el módulo.

###Configuración de LocalConfigurationManager para habilitar las validaciones de las firmas.

####PULL
En un nodo, LocalConfigurationManager realiza la validación de las firmas de módulos y las configuraciones en función de su configuración actual. De forma predeterminada, la validación de firmas está deshabilitada. La validación de firmas se puede habilitar agregando un bloque 'SignatureValidation' a la definición de metaconfiguración del nodo, tal como se muestra a continuación:

```PowerShell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'        
    } 
    
    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # By default,LCM will use default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM will use this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'            
        SignedItemType =  'Configuration','Module'         # Those are list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.       
    }
 
}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose 
 ```

El establecimiento de la metaconfiguración anterior en un nodo habilita la validación de firmas de los módulos y las configuraciones descargados. LocalConfigurationManager llevará a cabo los pasos siguientes para comprobar las firmas digitales.
* Compruebe que la firma de un archivo de configuración (. MOF) es válida. Usa el cmdlet de PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), que se amplía en la versión 5.1 para admitir la validación de la firma de MOF.
* Compruebe que la entidad de certificación que autorizó al firmante es de confianza.
* Descargue las dependencias de los módulos o recursos de la configuración en una ubicación temporal.
* Compruebe la firma del catálogo incluida dentro del módulo.
    * Busque un archivo <moduleName>.cat y compruebe su firma mediante el cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Compruebe que la entidad de certificación que autenticó al firmante es de confianza.
    * Compruebe que el contenido de los módulos no se ha alterado, para lo que debe usar el cmdlet nuevo [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).
* Módulo de instalación en $env:ProgramFiles\WindowsPowerShell\Modules\
* Configuración de proceso.

Nota: - La validación de la firma en el catálogo de módulo y la configuración solo se realizan la primera vez que se aplica la configuración al sistema o cuando el módulo se descarga e instala. Una ejecución de coherencia no valida la firma de Current.mof ni sus dependencias de módulo.
Si se ha producido un error en cualquier etapa de la comprobación, por ejemplo, si la configuración extraída del servidor de extracción no tiene firma, el procesamiento de la configuración terminará con el error que se muestra más adelante y se eliminarán todos los archivos temporales.

![Configuración de salida de error de ejemplo](../../images/PullUnsignedConfigFail.PNG)

De forma similar, la extracción de un módulo cuyo catálogo no esté firmado provocará el siguiente error:-

![Módulo de salida de error de ejemplo](../../images/PullUnisgnedCatalog.PNG)

####PUSH
Una configuración entregada mediante inserción puede alterarse en su origen antes de que se entregue al nodo. El administrador de configuración local llevará a cabo pasos de validación de firmas similares para las configuraciones insertadas o publicadas.
A continuación se muestra un ejemplo completo de validación de firma para la inserción.

* Habilite la validación de firma en el nodo.

```Powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'        
    } 
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'   
        SignedItemType =  'Configuration','Module'             
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
``` 
* Cree un archivo de configuración de ejemplo.

```Powershell
# Sample configuration
Configuration Test{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* Intente insertar el archivo de configuración sin firmar en el nodo. 

```Powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
``` 
![ErrorUnsignedMofPushed](../../images/PushUnsignedMof.PNG)

* Firme el archivo de configuración mediante el certificado de firma de código.

![SignMofFile](../../images/SignMofFile.PNG)

* Intente insertar el archivo mof firmado.

![SignMofFile](../../images/PushSignedMof.PNG)




<!--HONumber=Aug16_HO3-->


