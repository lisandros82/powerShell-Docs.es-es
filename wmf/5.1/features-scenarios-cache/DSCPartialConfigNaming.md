---
title: "Convención de nomenclatura de configuración parcial de extracción"
author: jaimeo
contributor: berheabrha
translationtype: Human Translation
ms.sourcegitcommit: dfa487a11528e26faf5b0e8637b75983abe0b1c8
ms.openlocfilehash: 368c26766961e760fd2de8c99057121bea076158

---

##Convención de nomenclatura de configuración parcial de extracción
En las versiones anteriores, la convención de nomenclatura de una configuración parcial era que el nombre de archivo mof en el servidor o servicio de extracción debía coincidir con el nombre de configuración parcial especificado en la configuración del administrador de configuración local, que a su vez debe coincidir con el nombre de configuración insertado en el archivo MOF. Vea las instantáneas siguientes:-• Opciones de configuración local que definen una configuración parcial que puede recibir un nodo.

![Metaconfiguración de ejemplo](../../images/MetaConfigPartialOne.png)

• Definición de configuración parcial de ejemplo. 

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

• ‘ConfigurationName’ insertado en el archivo MOF generado.

![Archivo MOF de ejemplo generado](../../images/PartialGeneratedMof.png)

• FileName en el repositorio de configuración de extracción 

![FileName en el repositorio de configuración](../../images/PartialInConfigRepository.png)

El nombre del servicio Automatización de Azure generó archivos MOF como ``<ConfigurationName>.<NodeName>.mof``. Por tanto, la configuración siguiente se compilará como PartialOne.Localhost.mof.  
Esto hizo imposible extraer una configuración parcial del servicio Automatización de Azure.

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

En WMF 5.1, la configuración parcial del servidor o servicio de extracción se puede denominar ``<ConfigurationName>.<NodeName>.mof``. Además, si una máquina extrae una sola configuración del servidor o servicio de extracción, el documento de configuración del repositorio de configuración del servidor de extracción puede tener cualquier nombre. Esta flexibilidad de nomenclatura permite administrar la configuración parcial de un nodo a través del servicio de extracción local y de Automatización de Azure. Por ejemplo, puede tener una configuración parcial "base" que se inserta de forma local y otra configuración parcial que se extrae del servicio Automatización de Azure.

La metaconfiguración siguiente configurará un nodo que se debe administrar tanto localmente como mediante el servicio Automatización de Azure.

```Powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30;
            RefreshMode = "PULL";            
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation Service.
        PartialConfiguration PartialCOnfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"   
        }
    
        # This partial configuration is managed locally.
        PartialConfiguration OnPremConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   slcm -Path .\RegistrationMetaConfig -Verbose
 ```





<!--HONumber=Aug16_HO3-->


