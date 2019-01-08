---
title: Instalación de PowerShell Core en macOS
description: Información sobre cómo instalar PowerShell Core en macOS
ms.date: 12/12/2018
ms.openlocfilehash: 91e64cace7d4ed988da56109dde9bf2a80528eb4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402561"
---
# <a name="installing-powershell-core-on-macos"></a>Instalación de PowerShell Core en macOS

PowerShell Core admite macOS 10.12 y superior.
Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.
Después de instalar el paquete, ejecute `pwsh` desde el terminal.

## <a name="about-brew"></a>Acerca de Brew

[Homebrew][brew] es el administrador de paquetes preferido de macOS.
Si no se encuentra el comando `brew`, debe instalar Homebrew según [sus instrucciones][brew].

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Instalación de la versión estable más reciente a través de Homebrew en macOS 10.12 o superior

Consulte [Acerca de Brew](#about-brew) para obtener información sobre Brew.

Ahora puede instalar PowerShell:

```sh
brew cask install powershell
```

Por último, compruebe que la instalación funciona correctamente:

```sh
pwsh
```

Cuando se publiquen nuevas versiones de PowerShell, actualice las fórmulas de Homebrew y actualizar PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Los comandos anteriores pueden llamarse desde dentro de un host de PowerShell (pwsh) pero, a continuación, se debe saldrá y reiniciar para completar la actualización y actualizar los valores mostrados en el shell de PowerShell `$PSVersionTable`.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Instalación de la versión preliminar más reciente a través de Homebrew en macOS 10.12 o superior

Consulte [Acerca de Brew](#about-brew) para obtener información sobre Brew.

Una vez instalado Homebrew, puede instalar PowerShell.
En primer lugar, instale el [Cask versiones] [ cask-versions] paquete que le permita instalar versiones alternativas de los paquetes de cask:

```sh
brew tap homebrew/cask-versions
```

Ahora puede instalar PowerShell:

```sh
brew cask install powershell-preview
```

Por último, compruebe que la instalación funciona correctamente:

```sh
pwsh-preview
```

Cuando se publiquen nuevas versiones de PowerShell, actualice las fórmulas de Homebrew y actualizar PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Los comandos anteriores pueden llamarse desde dentro de un host de PowerShell (pwsh), pero, en este caso, es necesario salir y reiniciar el shell de PowerShell para completar la actualización.
> y actualice los valores mostrados en `$PSVersionTable`.

## <a name="installation-via-direct-download"></a>Instalación mediante descarga directa

Descargue el paquete PKG `powershell-6.1.0-osx-x64.pkg`
desde la página de [versiones][] en la máquina macOS.

Puede hacer doble clic en el archivo y seguir las indicaciones, o bien instalarlo desde el terminal:

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

Instale [OpenSSL](#install-openssl). OpenSSL se necesita para la comunicación remota de PowerShell y las operaciones de CIM.

## <a name="binary-archives"></a>Archivos binarios

Se proporcionan archivos binarios `tar.gz` de PowerShell para la plataforma macOS, a fin de permitir escenarios de implementación avanzados.

### <a name="installing-binary-archives-on-macos"></a>Instalación de archivos binarios en macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

Instale [OpenSSL](#install-openssl). OpenSSL se necesita para la comunicación remota de PowerShell y las operaciones de CIM.

## <a name="installing-dependencies"></a>Instalación de dependencias

### <a name="install-xcode-command-line-tools"></a>Instalación de las herramientas de línea de comandos de XCode

```sh
xcode-select --install
```

### <a name="install-openssl"></a>Instalación de OpenSSL

OpenSSL se necesita para la comunicación remota de PowerShell y las operaciones de CIM. Puede realizar la instalación mediante MacPorts o Brew.

#### <a name="install-openssl-via-brew"></a>Instalación de OpenSSL mediante Brew

Consulte [Acerca de Brew](#about-brew) para obtener información sobre Brew.

Para instalar OpenSSL, ejecute `brew install openssl`.

#### <a name="install-openssl-via-macports"></a>Instalación de OpenSSL mediante MacPorts

1. Instalar el [las herramientas de línea de comandos de XCode](#install-xcode-command-line-tools).
1. Instale MacPorts.
   Si necesita instrucciones, consulte el [Guía de instalación](https://guide.macports.org/chunked/installing.macports.html).
1. Actualice MacPorts mediante la ejecución de `sudo port selfupdate`.
1. Actualice los paquetes de MacPorts mediante la ejecución de `sudo port upgrade outdated`.
1. Instale OpenSSL ejecutando `sudo port install openssl`.
1. Vincule las bibliotecas para que estén disponibles para PowerShell:

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>Desinstalación de PowerShell Core

Si ha instalado PowerShell con Homebrew, use el siguiente comando para desinstalar:

```sh
brew cask uninstall powershell
```

Si ha instalado PowerShell mediante descarga directa, deberá quitar PowerShell manualmente:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Para quitar las rutas de acceso de PowerShell adicionales, consulte el [rutas](#paths) sección en este documento y quitar las rutas de acceso mediante `sudo rm`.

> [!NOTE]
> Este paso no es necesario si ha realizado la instalación con Homebrew.

## <a name="paths"></a>Paths

* `$PSHOME` es `/usr/local/microsoft/powershell/6.1.0/`.
* Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.
* Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.
* Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.
* Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.
* Los módulos predeterminados se leerán de `$PSHOME/Modules`.
* El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.

Los perfiles respetan la configuración por host de PowerShell.
Por lo que existe el perfil de host específico predeterminado en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.

PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en macOS.

Dado que macOS es una derivación de BSD, se usa el prefijo `/usr/local` en lugar de `/opt`.
Por lo tanto, `$PSHOME` es `/usr/local/microsoft/powershell/6.1.0/`, y el vínculo simbólico se coloca en `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Recursos adicionales

* [Homebrew Web][brew]
* [Repositorio GitHub de Homebrew][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
