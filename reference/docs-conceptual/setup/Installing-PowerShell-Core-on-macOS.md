---
title: Instalación de PowerShell Core en macOS
description: Información sobre cómo instalar PowerShell Core en macOS
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998510"
---
# <a name="installing-powershell-core-on-macos"></a>Instalación de PowerShell Core en macOS

PowerShell Core admite macOS 10.12 y superior.
Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.
Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.

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

Cuando se publiquen nuevas versiones de PowerShell, bastará con actualizar las fórmulas de Homebrew y PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Los comandos anteriores pueden llamarse desde un host de PowerShell (pwsh), pero, acto seguido, el shell de PowerShell se debe cerrar y volver a iniciar para finalizar la actualización y actualizar los valores que aparecen en $PSVersionTable.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Instalación de la versión preliminar más reciente a través de Homebrew en macOS 10.12 o superior

Consulte [Acerca de Brew](#about-brew) para obtener información sobre Brew.

Una vez que haya instalado Homebrew, le resultará muy fácil instalar PowerShell.
En primer lugar, instale [Cask-Versions][cask-versions] que le permite instalar versiones alternativas de los paquetes de cask:

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

Cuando se publiquen nuevas versiones de PowerShell, bastará con actualizar las fórmulas de Homebrew y PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Los comandos anteriores pueden llamarse desde dentro de un host de PowerShell (pwsh), pero, en este caso, es necesario salir y reiniciar el shell de PowerShell para completar la actualización.
> y actualizar los valores mostrados en $PSVersionTable.

## <a name="installation-via-direct-download"></a>Instalación mediante descarga directa

Descargue el paquete PKG `powershell-6.1.0-osx-x64.pkg`
desde la página de [versiones][] en la máquina macOS.

Puede hacer doble clic en el archivo y seguir las indicaciones, o bien instalarlo desde el terminal:

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

Instale [OpenSSL](#install-openssl), ya que es necesario para operaciones de CIM y comunicaciones remotas de PowerShell.

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

Instale [OpenSSL](#install-openssl), ya que es necesario para las operaciones de CIM y las comunicaciones remotas de PowerShell.

## <a name="installing-dependencies"></a>Instalación de dependencias

### <a name="install-xcode-command-line-tools"></a>Instalación de las herramientas de la línea de comandos de XCode

```shell
xcode-select -install
```

### <a name="install-openssl"></a>Instalación de OpenSSL

OpenSSL se necesita para la comunicación remota de PowerShell y las operaciones de CIM.  Puede realizar la instalación mediante MacPorts o Brew.

#### <a name="install-openssl-via-brew"></a>Instalación de OpenSSL mediante Brew

Consulte [Acerca de Brew](#about-brew) para obtener información sobre Brew.

Ejecute `brew install openssl` para instalar OpenSSL.

#### <a name="install-openssl-via-macports"></a>Instalación de OpenSSL mediante MacPorts

1. Instalación de las [herramientas de la línea de comandos de XCode](#install-xcode-command-line-tools)
1. Instale MacPorts.
   Consulte la [guía de instalación](https://guide.macports.org/chunked/installing.macports.html) si necesita instrucciones.
1. Actualice MacPorts mediante la ejecución de `sudo port selfupdate`.
1. Actualice los paquetes de MacPorts mediante la ejecución de `sudo port upgrade outdated`.
1. Instale OpenSSL mediante la ejecución de `sudo port instal openssl`.
1. Vincule las bibliotecas para que PowerShell pueda usarlas.

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>Desinstalación de PowerShell Core

Si ha instalado PowerShell con Homebrew, la desinstalación es fácil:

```sh
brew cask uninstall powershell
```

Si ha instalado PowerShell mediante descarga directa, deberá quitar PowerShell manualmente:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Para quitar las rutas de acceso de PowerShell adicionales, consulte la sección [Rutas de acceso](#paths) de este documento y elimine las rutas de acceso deseadas mediante `sudo rm`.

> [!NOTE]
> Este paso no es necesario si ha realizado la instalación con Homebrew.

## <a name="paths"></a>Rutas de acceso

* `$PSHOME` es `/usr/local/microsoft/powershell/6.1.0/`.
* Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.
* Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.
* Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.
* Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.
* Los módulos predeterminados se leerán de `$PSHOME/Modules`.
* El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.

Los perfiles respetan la configuración por host de PowerShell.
Así que los perfiles predeterminados específicos del host están en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.

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
