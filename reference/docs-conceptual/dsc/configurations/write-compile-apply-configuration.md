---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,service,setup
title: Escritura, compilación y aplicación de una configuración
ms.openlocfilehash: 8bcd55518b0409b9a4b02ca95f027a0a77eb5300
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954002"
---
> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Escritura, compilación y aplicación de una configuración

Este ejercicio le guía a través de la creación y aplicación de una especificación de la configuración de estado deseado (DSC) de principio a fin.
En el ejemplo siguiente, obtendrá información sobre cómo escribir y aplicar una configuración muy sencilla. La configuración garantizará la existencia de un archivo "HelloWorld.txt" en el equipo local. Si elimina el archivo, DSC volverá a crearlo la próxima vez que realice una actualización.

Para obtener información general de lo que es DSC y cómo funciona, consulte [Información general sobre Desired State Configuration para desarrolladores](../overview/overview.md).

## <a name="requirements"></a>Requisitos

Para ejecutar este ejemplo, necesitará un equipo con PowerShell 4.0 o posterior.

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

> Importante: En escenarios más avanzados en los que es necesario importar varios módulos para poder trabajar con muchos recursos de DSC en la misma configuración, asegúrese de colocar cada módulo en una línea independiente mediante `Import-DscResource`.
> Es más fácil mantener esto en el control de código fuente y resulta necesario cuando se trabaja con DSC en Azure State Configuration.
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

Guarde el archivo como "HelloWorld.ps1".

Definir una configuración es parecido a definir una función. El bloque **Node** especifica el nodo de destino que va a configurar, en este caso `localhost`.

La configuración llama a uno de los [recursos](../resources/resources.md), el recurso `File`. Los recursos se encargan de garantizar que el nodo de destino se encuentra en el estado definido por la configuración.

## <a name="compile-the-configuration"></a>Compilación de la configuración

Para que una configuración de DSC se aplique a un nodo, debe compilarse primero en un archivo MOF.
Al ejecutarse la configuración, como en el caso de una función, se compilará un archivo ".mof" para cada nodo definido por el bloque `Node`.
Para ejecutar la configuración, deberá *usar el operador punto* en el script "HelloWorld.ps1" en el ámbito actual.
Para obtener más información, vea [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing) (Acerca de los scripts).

<!-- markdownlint-disable MD038 -->
*Use el operador punto* en el script "HelloWorld.ps1" escribiendo la ruta de acceso donde la almacenó, después de `. ` (punto, espacio). A continuación, puede ejecutar la configuración llamándola igual que una función.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
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

El cmdlet `Start-DscConfiguration` indica el [administrador de configuración local (LCM)](../managing-nodes/metaConfig.md), el motor de DSC, para aplicar la configuración.
El LCM se encarga de llamar a los recursos de DSC para aplicar la configuración.

Use el código siguiente para ejecutar el cmdlet `Start-DSCConfiguration`. Especifique la ruta de acceso del directorio donde se almacena "localhost.mof" en el parámetro `-Path`. El cmdlet `Start-DSCConfiguration` busca en el directorio especificado todos los archivos "\<nombrearchivo\>.mof". El cmdlet `Start-DSCConfiguration` intenta aplicar cada archivo ".mof" que encuentra con el nombre del equipo especificado por el nombre de archivo ("localhost", "servidor01", "dc-02", etc.).

> [!NOTE]
> Si no se especifica el parámetro `-Wait`, `Start-DSCConfiguration` crea un trabajo en segundo plano para llevar a cabo la operación. La especificación del parámetro `-Verbose` permite ver el resultado **detallado** de la operación. `-Wait` y `-Verbose` son parámetros opcionales, ambos.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Probar la configuración

Cuando el cmdlet `Start-DSCConfiguration` se haya completado, debe ver un archivo "HelloWorld.txt" en la ubicación especificada. Puede comprobar el contenido con el cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content).

También puede *probar* el estado actual con [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

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

## <a name="re-applying-the-configuration"></a>Nueva aplicación de la configuración

Para que la configuración se aplique de nuevo, puede quitar el archivo de texto creado por la configuración. El uso del cmdlet `Start-DSCConfiguration` con el parámetro `-UseExisting`. El parámetro `-UseExisting` indica a `Start-DSCConfiguration` que vuelva a aplicar el archivo "current.mof", que representa la última configuración aplicada correctamente.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Pasos siguientes

- Conozca más sobre las configuraciones de DSC en [Configuraciones DSC](configurations.md).
- Vea qué recursos de DSC están disponibles y cómo crear recursos personalizados de DSC en [recursos de DSC](../resources/resources.md).
- Encuentre las configuraciones y los recursos de DSC en la [Galería de PowerShell](https://www.powershellgallery.com/).
