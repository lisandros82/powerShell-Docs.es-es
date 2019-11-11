---
title: Instalación de PowerShell Core en Windows
description: Información sobre cómo instalar PowerShell Core en Windows
ms.date: 08/06/2018
ms.openlocfilehash: c06eba06e376c3f795ab9c0fae9270cf6cf8f2ce
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444451"
---
# <a name="installing-powershell-core-on-windows"></a>Instalación de PowerShell Core en Windows

Hay varias formas de instalar PowerShell Core en Windows.

> [!TIP]
> Si ya tiene instalado el [SDK de .NET Core](/dotnet/core/sdk), es fácil instalar PowerShell como una [herramienta global de .NET](/dotnet/core/tools/global-tools).
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a>Requisitos previos

Para habilitar la comunicación remota de PowerShell a través de WSMan, deben cumplirse los siguientes requisitos previos:

- Instale el [entorno de ejecución de C universal](https://www.microsoft.com/download/details.aspx?id=50410) en las versiones de Windows anteriores a Windows 10. Está disponible mediante descarga directa o Windows Update. Los sistemas admitidos a los que se hayan aplicado todas las revisiones (incluidos los paquetes opcionales) ya lo tienen instalado.
- Instale Windows Management Framework (WMF) 4.0 o una versión más reciente en Windows 7 y Windows Server 2008 R2. Para más información sobre WMF, consulte la [información general sobre WMF](/powershell/wmf/overview).

## <a name="a-idmsi-installing-the-msi-package"></a><a id="msi" />Instalación del paquete MSI

Para instalar PowerShell en un cliente de Windows o Windows Server (funciona en Windows 7 SP1, Server 2008 R2 y versiones posteriores), descargue el paquete MSI desde nuestra página de [versiones][releases] de GitHub. Desplácese hacia abajo hasta la sección **Recursos** de la versión que quiere instalar. Es posible que la sección Recursos esté contraída, por lo que tendría que hacer clic para expandirla.

El archivo MSI tiene este aspecto: `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Una vez descargado, haga doble clic en el instalador y siga las indicaciones.

El instalador crea un acceso directo en el menú de inicio de Windows.

- De forma predeterminada, el paquete se instala en `$env:ProgramFiles\PowerShell\<version>`
- Puede iniciar PowerShell mediante el menú Inicio o `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="administrative-install-from-the-command-line"></a>Instalación administrativa desde la línea de comandos

Los paquetes MSI se pueden instalar desde la línea de comandos. Esto permite a los administradores implementar los paquetes sin interacción del usuario. El paquete MSI para PowerShell incluye las siguientes propiedades para controlar las opciones de instalación:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL**: esta propiedad controla la opción para agregar el elemento **Open PowerShell** al menú contextual en el Explorador de Windows.
- **ENABLE_PSREMOTING**: esta propiedad controla la opción para habilitar la comunicación remota de PowerShell durante la instalación.
- **REGISTER_MANIFEST**: esta propiedad controla la opción para registrar el manifiesto de registro de eventos de Windows.

En los ejemplos siguientes se muestra cómo instalar PowerShell Core con todas las opciones de instalación habilitadas de forma silenciosa.

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Para obtener una lista completa de opciones de línea de comandos de Msiexec.exe, consulte [Opciones de línea de comandos](/windows/desktop/Msi/command-line-options).

## <a name="a-idzip-installing-the-zip-package"></a><a id="zip" />Instalación del paquete ZIP

Se proporcionan archivos binarios ZIP de PowerShell para permitir escenarios de implementación avanzada. Tenga en cuenta que, cuando use el archivo ZIP, no aparecerá la comprobación de requisitos previos como en el caso del paquete MSI. Para que la comunicación remota en WSMan funcione correctamente, asegúrese de que se han cumplido los [requisitos previos](#prerequisites).

## <a name="deploying-on-windows-iot"></a>Implementación en Windows IoT

Windows IoT ya incluye Windows PowerShell, que se usará para implementar PowerShell Core 6.

1. Cree `PSSession` en el dispositivo de destino.

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Copie el paquete ZIP en el dispositivo.

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Conéctese al dispositivo y expanda el archivo.

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. Configure el acceso remoto a PowerShell Core 6.

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Conéctese al punto de conexión de PowerShell Core 6 en el dispositivo.

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a>Desarrollo en Nano Server

En estas instrucciones se da por supuesto que ya se ejecuta una versión de PowerShell en la imagen de Nano Server y que se ha generado mediante [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).
Nano Server es un sistema operativo "sin periféricos". Los archivos binarios principales se pueden implementar mediante dos métodos diferentes.

1. Sin conexión: monte el VHD de Nano Server y descomprima el contenido del archivo ZIP en la ubicación seleccionada de la imagen montada.
2. En línea: transfiera el archivo ZIP a través de una sesión de PowerShell y descomprímalo en la ubicación seleccionada.

En ambos casos, necesitará el paquete comercial ZIP de Windows 10 x64 y deberá ejecutar los comandos en una instancia de PowerShell de "Administrador".

### <a name="offline-deployment-of-powershell-core"></a>Implementación sin conexión de PowerShell Core

1. Use su utilidad ZIP favorita para descomprimir el paquete en un directorio de la imagen montada de Nano Server.
2. Desmonte la imagen e iníciela.
3. Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.
4. Siga las instrucciones para crear un punto de conexión de comunicación remota mediante "[otra técnica de instancia"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Implementación en línea de PowerShell Core

Los pasos siguientes le guían por la implementación de PowerShell Core en una instancia en ejecución de Nano Server y la configuración de su punto de conexión remoto.

- Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Copie el archivo en la instancia de Nano Server.

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Especifique la sesión.

  ```powershell
  Enter-PSSession $session
  ```

- Extraiga el archivo ZIP.

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Si le interesa la comunicación remota basada en WSMan, siga las instrucciones para crear un punto de conexión de comunicación remota mediante ["otra técnica de instancia"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="how-to-create-a-remoting-endpoint"></a>Procedimientos para crear un punto de conexión de comunicación remota

PowerShell Core admite el Protocolo de comunicación remota de PowerShell (PSRP) a través de WSMan y SSH. Para obtener más información, consulte:

- [Comunicación remota mediante SSH en PowerShell Core][ssh-remoting]
- [Comunicación remota mediante WSMan en PowerShell Core][wsman-remoting]

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
