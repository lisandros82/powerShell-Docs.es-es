---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Inicio rápido de la configuración de estado deseado
ms.openlocfilehash: eb7572f39f7a2710c82f132f42c3502b15c48d0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219052"
---
> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="desired-state-configuration-quick-start"></a>Inicio rápido de la configuración de estado deseado

Este ejercicio le guía a través de la creación y aplicación de una especificación de la configuración de estado deseado (DSC) de principio a fin.
En el ejemplo, nos aseguraremos de que un servidor tiene habilitada la característica `Web-Server` (IIS) y de que el contenido de un sitio web "Hello World" simple está presente en el directorio `intepub\wwwroot` de ese servidor.

Para información general de lo que es DSC y cómo funciona, consulte [Información general sobre la configuración de estado deseado para responsables de toma de decisiones](decisionMaker.md).

## <a name="requirements"></a>Requisitos

Para ejecutar este ejemplo, necesitará un equipo con Windows Server 2012 o posterior y PowerShell 4.0 o posterior.

## <a name="write-and-place-the-indexhtm-file"></a>Escritura y colocación del archivo index.htm

En primer lugar, vamos a crear el archivo HTML que se utilizará como el contenido del sitio web.

En la carpeta raíz, cree una carpeta denominada `test`.

En un editor de texto, escriba el texto siguiente:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Guárdelo como `index.htm` en la carpeta `test` que creó anteriormente.

## <a name="write-the-configuration"></a>Escritura de la configuración

Una [configuración DSC](configurations.md) es una función especial de PowerShell que define cómo desea configurar uno o más equipos de destino (nodos).

En PowerShell ISE, escriba lo siguiente:

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

Guarde el archivo como `WebsiteTest.ps1`.

Puede ver que se parece a una función de PowerShell, con la incorporación de la palabra clave **Configuration** utilizada antes del nombre de la función.

El bloque **Node** especifica el nodo de destino que va a configurar, en este caso `localhost`.

La configuración llama a dos [recursos](resources.md): [WindowsFeature](windowsFeatureResource.md) y [File](fileResource.md).
Los recursos se encargan de garantizar que el nodo de destino se encuentra en el estado definido por la configuración.

## <a name="compile-the-configuration"></a>Compilación de la configuración

Para que una configuración de DSC se aplique a un nodo, debe compilarse primero en un archivo MOF.
Para ello, ejecute la configuración como una función.
En una consola de PowerShell, vaya a la misma carpeta donde guardó la configuración y ejecute los siguientes comandos para compilar la configuración en un archivo MOF:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Esto genera la siguiente salida:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

La primera línea hace que la función de configuración esté disponible en la consola.
La segunda línea ejecuta la configuración.
El resultado es que se crea una carpeta nueva llamada `WebsiteTest` como una subcarpeta de la carpeta actual.
La carpeta `WebsiteTest` contiene un archivo denominado `localhost.mof`.
Este es el archivo que se puede aplicar al nodo de destino.

## <a name="apply-the-configuration"></a>Aplicación de la configuración

Ahora que ha compilado MOF, puede aplicar la configuración al nodo de destino (en este caso, el equipo local) mediante una llamada al cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration).

El cmdlet `Start-DscConfiguration` indica el [administrador de configuración local (LCM)](metaConfig.md), que es el motor de DSC, para aplicar la configuración.
El LCM se encarga de llamar a los recursos de DSC para aplicar la configuración.

En una consola de PowerShell, vaya a la misma carpeta donde guardó la configuración y ejecute el siguiente comando:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Probar la configuración

Puede llamar al cmdlet [DscConfigurationStatus Get](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) para ver si la configuración se realizó correctamente.

También puede probar los resultados directamente, en este caso examinando `http://localhost/` en un explorador web.
Debería ver la página HTML "Hello World" que creó como el primer paso en este ejemplo.

## <a name="next-steps"></a>Pasos siguientes

- Conozca más sobre las configuraciones de DSC en [Configuraciones DSC](configurations.md).
- Vea qué recursos de DSC están disponibles y cómo crear recursos personalizados de DSC en [recursos de DSC](resources.md).
- Encuentre las configuraciones y los recursos de DSC en la [Galería de PowerShell](https://www.powershellgallery.com/).