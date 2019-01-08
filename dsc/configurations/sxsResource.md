---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Importación de una versión específica de un recurso instalado
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402209"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Importación de una versión específica de un recurso instalado

> Se aplica a: Windows PowerShell 5.0

En PowerShell 5.0, versiones independientes de los recursos de DSC pueden instalarse en un equipo en paralelo. Un módulo de recursos puede almacenar versiones independientes de un recurso en carpetas denominada de versión.

## <a name="installing-separate-resource-versions-side-by-side"></a>Instalación de versiones de recursos independiente en paralelo

Puede usar los parámetros **MinimumVersion**, **MaximumVersion** y **RequiredVersion** del cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) para especificar la versión de un módulo que se va a instalar. Llamar a **Install-Module** sin especificar una versión instala la versión más reciente.

Por ejemplo, hay varias versiones del módulo **xFailOverCluster**, cada una de las cuales contiene un recurso **xCluster**. Una llamada a **Install-Module** sin especificar la versión número instala la versión más reciente del módulo.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Para instalar una versión específica de un módulo, especifique un **RequiredVersion** de 1.1.0.0. Esto instala la versión especificada en paralelo con la versión instalada.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

Ahora, puede ver tanto la versión del módulo que se enumera cuando se utiliza `Get-DSCResource`.

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Especificación de una versión de recursos en una configuración

Si tiene instaladas en un equipo de versiones de recursos independiente, debe especificar la versión de ese recurso cuando se usa en una configuración. Esto se hace mediante la especificación del parámetro **ModuleVersion** de la palabra clave **Import-DscResource**. Si tiene instaladas varias versiones de un recurso y no especifica la versión del módulo de recursos que quiere usar, la configuración generará un error.

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

>Nota: El parámetro ModuleVersion de Import-DscResource no está disponible en PowerShell 4.0. En PowerShell 4.0, puede especificar una versión de módulo pasando un objeto de especificación de módulo al parámetro ModuleName de Import-DscResource. Un objeto de especificación de módulo es una tabla hash que contiene las claves ModuleName y RequiredVersion. Por ejemplo:

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

- [Configuraciones DSC](configurations.md)
- [Recursos de DSC](../resources/resources.md)
