---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Uso de recursos con varias versiones
ms.openlocfilehash: c3397775a6767d74c182e15d07371e830f98e9a9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="using-resources-with-multiple-versions"></a>Uso de recursos con varias versiones

> Se aplica a: Windows PowerShell 5.0

En PowerShell 5.0, los recursos de DSC pueden tener varias versiones, y las versiones pueden instalarse en un equipo en paralelo. Esto se implementa mediante varias versiones de un módulo de recursos que están contenidas en la misma carpeta del módulo.

## <a name="installing-multiple-resource-versions-side-by-side"></a>Instalación de varias versiones de recursos en paralelo

Puede usar los parámetros **MinimumVersion**, **MaximumVersion** y **RequiredVersion** del cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) para especificar la versión de un módulo que se va a instalar. Llamar a **Install-Module** sin especificar una versión instala la versión más reciente.

Por ejemplo, hay varias versiones del módulo **xFailOverCluster**, cada una de las cuales contiene un recurso **xCluster**. El resultado de llamar a **Install-Module** sin especificar el número de versión es el siguiente:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Ahora, si se vuelve a llamar a **Install-Module**, pero se especifica una **RequiredVersion** de 1.1.0.0, se obtiene el siguiente resultado:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Especificación de una versión de recursos en una configuración

Si tiene varios recursos instalados en un equipo, debe especificar la versión de ese recurso cuando lo usa en una configuración. Esto se hace mediante la especificación del parámetro **ModuleVersion** de la palabra clave **Import-DscResource**. Si tiene instaladas varias versiones de un recurso y no especifica la versión del módulo de recursos que quiere usar, la configuración generará un error.

La configuración siguiente muestra cómo especificar la versión del recurso al que se va a llamar:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

>Nota: el parámetro ModuleVersion de Import-DscResource no está disponible en PowerShell 4.0. En PowerShell 4.0, puede especificar una versión de módulo pasando un objeto de especificación de módulo al parámetro ModuleName de Import-DscResource. Un objeto de especificación de módulo es una tabla hash que contiene las claves ModuleName y RequiredVersion. Por ejemplo:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

Esto también funcionará en PowerShell 5.0, pero se recomienda que use el parámetro **ModuleVersion**.

## <a name="see-also"></a>Vea también
* [Configuraciones DSC](configurations.md)
* [Recursos de DSC](resources.md)

