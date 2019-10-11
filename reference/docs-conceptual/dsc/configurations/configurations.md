---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configuraciones DSC
ms.openlocfilehash: d7749ec88f9cca3e29c6b38d61fb73776af7ceb4
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954502"
---
# <a name="dsc-configurations"></a>Configuraciones DSC

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Las configuraciones DSC son scripts de PowerShell que definen un tipo especial de función.
Para definir una configuración, se utiliza la palabra clave de PowerShell **Configuration**.

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

Guarde el script como un archivo `.ps1`.

## <a name="configuration-syntax"></a>Sintaxis de la configuración

Un script de configuración consta de las partes siguientes:

- El bloque **Configuration**. Este es el bloque del script más externo. Para definirlo, se usa la palabra clave **Configuration** y se facilita un nombre. En este caso, el nombre de la configuración es "MyDscConfiguration".
- Uno o varios bloques **Node**. Estos definen los nodos (equipos o máquinas virtuales) que se están configurando. En la configuración anterior, hay un bloque **Node** cuyo destino es un equipo denominado "TEST-PC1". El bloque Node puede aceptar varios nombres de equipo.
- Uno o varios bloques de recursos. Es aquí donde la configuración establece las propiedades de los recursos que se están configurando. En este caso, hay dos bloques de recursos, cada uno de los cuales llama al recurso "WindowsFeature".

Dentro de un bloque **Configuration**, puede hacer todo lo que se puede realizar normalmente en una función de PowerShell. Por ejemplo, en el ejemplo anterior, si no quisiera codificar de forma rígida el nombre del equipo de destino en la configuración, podría agregar un parámetro para el nombre del nodo:

En este ejemplo, especifique el nombre del nodo, pasando como parámetro **ComputerName** cuando compile la configuración. El nombre se establece como el valor predeterminado "localhost".

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

El bloque **Node** también puede aceptar varios nombres de equipo. En el ejemplo anterior, puede usar el parámetro `-ComputerName` o pasar una lista de equipos separados por comas directamente al bloque **Node**.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

Al especificar una lista de equipos para el bloque **Node** desde una configuración, debe utilizar la notación de matriz.

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>Compilación de la configuración

Antes de que se pueda establecer una configuración, debe compilarla en un documento MOF.
Para ello, llame a la configuración, como lo haría con una función de PowerShell.
La última línea del ejemplo que contiene sólo el nombre de la configuración llama a la configuración.

> [!NOTE]
> Para llamar a una configuración, la función debe estar en el ámbito global (como ocurre con cualquier otra función de PowerShell).
> Puede conseguirlo si precede el script con el operador punto ".", o si ejecuta el script de configuración presionando F5 o haciendo clic en el botón **Ejecutar Script** del ISE.
> Para anteponer el operador punto al script, ejecute el comando `. .\myConfig.ps1`, donde `myConfig.ps1` es el nombre del archivo de script que contiene la configuración.

Cuando llama a la configuración:

- Resuelve todas las variables
- Crea una carpeta en el directorio actual con el mismo nombre que la configuración.
- Crea un archivo denominado _NodeName_.mof en el directorio nuevo, donde _NodeName_ es el nombre del nodo de destino de la configuración.
  Si hay más de un nodo, se creará un archivo MOF para cada nodo.

> [!NOTE]
> El archivo MOF contiene toda la información de configuración del nodo de destino. Por este motivo, es importante protegerlo adecuadamente.
> Para obtener más información, consulte [Proteger el archivo MOF](../pull-server/secureMOF.md).

Cuando se compila la primera configuración anterior, el resultado es la estructura de carpetas siguiente:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

Si la configuración toma un parámetro, como en el segundo ejemplo, se debe proporcionar en tiempo de compilación. Este sería su aspecto:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>Uso de nuevos recursos en la configuración

Si ha ejecutado los ejemplos anteriores, habrá observado que se le mostró una advertencia respecto a que se estaba utilizando un recurso sin importarlo explícitamente.
En la actualidad, DSC incluye 12 recursos como parte del módulo PSDesiredStateConfiguration.

El cmdlet ([Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)) puede utilizarse para determinar qué recursos están instalados en el sistema y disponibles para que el LCM los use.
Cuando estos módulos se hayan colocado en `$env:PSModulePath` y [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) los reconozca correctamente, es necesario que se carguen en la configuración.

**Import-DscResource** es una palabra clave dinámica que solo puede reconocerse dentro de un bloque **Configuration**, no es un cmdlet.
**Import-DscResource** admite dos parámetros:

- **ModuleName** es la manera recomendada de usar **Import-DscResource**. Acepta el nombre del módulo que contiene los recursos que se importarán (así como una matriz de cadenas de nombres de módulo).
- **Name** es el nombre del recurso que se importará. Este no es el nombre descriptivo que [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) devuelve como "Name", sino el nombre de clase que se usa al definir el esquema del recurso (que [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) devuelve como **ResourceType**).

Para obtener más información sobre el uso de `Import-DSCResource`, consulte [Uso de Import-DSCResource](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>Diferencias de PowerShell v4 y v5

Hay diferencias en cuanto a dónde se deben almacenar los recursos de DSC en PowerShell 4.0. Para obtener más información, consulte [Ubicación de los recursos](import-dscresource.md#resource-location).

## <a name="see-also"></a>Véase también

- [Información general sobre la configuración de estado deseado de Windows PowerShell](../overview/overview.md)
- [Recursos de DSC](../resources/resources.md)
- [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md)
