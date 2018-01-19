# <a name="installing-powershell-core-on-windows"></a>Instalación de PowerShell Core en Windows

## <a name="msi"></a>MSI

Para instalar PowerShell en un cliente de Windows o Windows Server (funciona en Windows 7 SP1, Server 2008 R2 y versiones posteriores), descargue el paquete MSI desde nuestra página de [versiones][] de GitHub.

El archivo MSI tiene este aspecto: `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Una vez descargado, haga doble clic en el instalador y siga las indicaciones.

Tras la instalación, se coloca un acceso directo en el menú Inicio.

* De forma predeterminada, el paquete se instala en `$env:ProgramFiles\PowerShell\`
* Puede iniciar PowerShell mediante el menú Inicio o `$env:ProgramFiles\PowerShell\pwsh.exe`

### <a name="prerequisites"></a>Requisitos previos

Para habilitar la comunicación remota de PowerShell a través de WSMan, deben cumplirse los siguientes requisitos previos:

* Instale el [entorno de ejecución de C universal](https://www.microsoft.com/download/details.aspx?id=50410) en las versiones de Windows anteriores a Windows 10.
  Está disponible mediante descarga directa o Windows Update.
  Los sistemas admitidos a los que se hayan aplicado todas las revisiones (incluidos los paquetes opcionales) ya lo tienen instalado.
* Instale Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) o una versión más reciente ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) en Windows 7 y Windows Server 2008 R2.

## <a name="zip"></a>ZIP

Se proporcionan archivos binarios ZIP de PowerShell para permitir escenarios de implementación avanzada.
Tenga en cuenta que, cuando use el archivo ZIP, no aparecerá la comprobación de requisitos previos como en el caso del paquete MSI.
Por ello, para que la comunicación remota mediante WSMan funcione correctamente en versiones de Windows anteriores a Windows 10, debe asegurarse de que se cumplan los [requisitos previos](#prerequisites).

## <a name="deploying-on-nano-server"></a>Desarrollo en Nano Server

En estas instrucciones se da por supuesto que ya se ejecuta una versión de PowerShell en la imagen de Nano Server y que se ha generado mediante [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).
Nano Server es un sistema operativo "sin periféricos" en el que la implementación de los binarios de PowerShell Core puede producirse de dos maneras diferentes:

1. Sin conexión: monte el VHD de Nano Server y descomprima el contenido del archivo ZIP en la ubicación seleccionada de la imagen montada.
1. En línea: transfiera el archivo ZIP a través de una sesión de PowerShell y descomprímalo en la ubicación seleccionada.

En ambos casos, necesitará el paquete comercial ZIP de Windows 10 x64 y deberá ejecutar los comandos en una instancia de PowerShell de "Administrador".

### <a name="offline-deployment-of-powershell-core"></a>Implementación sin conexión de PowerShell Core

1. Use su utilidad ZIP favorita para descomprimir el paquete en un directorio de la imagen montada de Nano Server.
1. Desmonte la imagen e iníciela.
1. Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.
1. Siga las instrucciones para crear un punto de conexión de comunicación remota mediante [otra técnica de instancia](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Implementación en línea de PowerShell Core

Los pasos siguientes le guiarán a través de la implementación de PowerShell Core en una instancia en ejecución de Nano Server y la configuración de su punto de conexión remoto.

* Conéctese a la instancia de Bandeja de entrada de Windows PowerShell.

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* Copie el archivo en la instancia de Nano Server.

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* Especifique la sesión.

```powershell
Enter-PSSession $session
```

* Extraiga el archivo ZIP.

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* Si le interesa la comunicación remota basada en WSMan, siga las instrucciones para crear un punto de conexión de comunicación remota mediante [otra técnica de instancia](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instrucciones para crear un punto de conexión de comunicación remota

PowerShell Core admite el Protocolo de comunicación remota de PowerShell (PSRP) a través de WSMan y SSH. Para obtener más información, consulte:

* [Comunicación remota mediante SSH en PowerShell Core][ssh-remoting]
* [Comunicación remota mediante WSMan en PowerShell Core][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Instrucciones de instalación de artefactos

Publicamos un archivo con bits de CoreCLR en todas las compilaciones de CI con [AppVeyor][].

## <a name="coreclr-artifacts"></a>Artefactos de CoreCLR

* Descargue el paquete ZIP desde la pestaña **artefactos** de la compilación determinada.
* Desbloquee el archivo ZIP. Para ello, haga clic con el botón derecho en el Explorador de archivos -> Propiedades -> active la casilla "Desbloquear" -> aplíquelo.
* Extraiga el archivo ZIP en el directorio `bin`.
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[versiones]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
