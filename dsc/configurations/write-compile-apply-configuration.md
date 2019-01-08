---
ms.date: 12/12/2018
keywords: DSC, powershell, configuración, servicio, el programa de instalación
title: Escritura, compilación y aplicación de una configuración
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402346"
---
> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Escritura, compilación y aplicación de una configuración

Este ejercicio le guía a través de la creación y aplicación de una especificación de la configuración de estado deseado (DSC) de principio a fin.
En el ejemplo siguiente, obtendrá información sobre cómo escribir y aplicar una configuración muy sencilla. La configuración se asegurará de que un archivo de "HelloWorld.txt" existe en el equipo local. Si elimina el archivo, DSC se volverá a crear la próxima vez que actualiza.

Para obtener información general de qué es DSC y cómo funciona, consulte [Desired State Configuration de introducción para desarrolladores](../overview/overview.md).

## <a name="requirements"></a>Requisitos

Para ejecutar este ejemplo, necesitará un equipo que ejecute PowerShell 4.0 o posterior.

## <a name="write-the-configuration"></a>Escritura de la configuración

Una [configuración](configurations.md) de DSC es una función especial de PowerShell que define cómo quiere configurar uno o más equipos de destino (nodos).

En PowerShell ISE, o en otro editor de PowerShell, escriba lo siguiente:

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

Guarde el archivo como "HelloWorld.ps1".

Definir una configuración es similar a definir una función. El bloque **Node** especifica el nodo de destino que va a configurar, en este caso `localhost`.

La configuración llama a uno [recursos](../resources/resources.md), el `File` recursos. Los recursos se encargan de garantizar que el nodo de destino se encuentra en el estado definido por la configuración.

## <a name="compile-the-configuration"></a>Compilación de la configuración

Para que una configuración de DSC se aplique a un nodo, debe compilarse primero en un archivo MOF.
Ejecutar la configuración, como una función, se compilará un "MOF" archivo para cada nodo definido por el `Node` bloque.
Para ejecutar la configuración, deberá *usar el operador punto* la secuencia de comandos "HelloWorld.ps1" en el ámbito actual.
Para obtener más información, consulte [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

*Usar el operador punto* la secuencia de comandos "HelloWorld.ps1" escribiendo en la ruta de acceso donde almacenó, después de la `. ` (punto, espacio). Es posible que, a continuación, ejecute la configuración llamando al igual que una función.

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

Esto genera la siguiente salida:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Aplicación de la configuración

Ahora que ha compilado MOF, puede aplicar la configuración al nodo de destino (en este caso, el equipo local) mediante una llamada al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

El `Start-DscConfiguration` cmdlet indica la [Administrador de configuración Local (LCM)](../managing-nodes/metaConfig.md), el motor de DSC para aplicar la configuración.
El LCM se encarga de llamar a los recursos de DSC para aplicar la configuración.

Utilice el código siguiente para ejecutar el `Start-DSCConfiguration` cmdlet. Especifique la ruta de acceso del directorio donde se almacena la "localhost.mof" a la `-Path` parámetro. El `Start-DSCConfiguration` cmdlet busca en el directorio especificado para cualquiera "\<computername\>.mof" archivos. El `Start-DSCConfiguration` cmdlet intenta aplicar cada archivo de "MOF" que encuentre con el nombre del equipo especificado por el nombre de archivo ("localhost", "server01", "dc-02", etcetera.).

> [!NOTE]
> Si el `-Wait` no se especifica el parámetro, `Start-DSCConfiguration` crea un trabajo en segundo plano para llevar a cabo la operación. Especificar el `-Verbose` parámetro le permite ver el **detallado** resultado de la operación. `-Wait`, y `-Verbose` son ambos parámetros opcionales.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Probar la configuración

Una vez el `Start-DSCConfiguration` cmdlet se complete, debería ver un archivo "HelloWorld.txt" en la ubicación especificada. Puede comprobar el contenido con el [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.

También puede *probar* el estado actual, use [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

El resultado debe ser "True" si el nodo es compatible actualmente con la configuración aplicada.

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>Volver a aplicar la configuración

Para ver la configuración se aplique de nuevo, puede quitar el archivo de texto creado por la configuración. El uso del `Start-DSCConfiguration` cmdlet con el `-UseExisting` parámetro. El `-UseExisting` parámetro le indica a `Start-DSCConfiguration` para volver a aplicar el archivo "current.mof", que representa correctamente la última configuración aplicada.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Pasos siguientes

- Conozca más sobre las configuraciones de DSC en [Configuraciones DSC](configurations.md).
- Vea qué recursos de DSC están disponibles y cómo crear recursos personalizados de DSC en [recursos de DSC](../resources/resources.md).
- Encuentre las configuraciones y los recursos de DSC en la [Galería de PowerShell](https://www.powershellgallery.com/).
