---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Introducción a la configuración de estado deseado (DSC) para Linux
ms.openlocfilehash: b1bc9b9fafd89a1af0f967de38a817bff1f3ffe3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "73933846"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Introducción a la configuración de estado deseado (DSC) para Linux

En este tema se ofrece una introducción al uso de la configuración de estado deseado (DSC) de PowerShell para Linux. Para obtener información general sobre DSC, consulte [Introducción a la configuración de estado deseado de Windows PowerShell](../overview/overview.md).

## <a name="supported-linux-operation-system-versions"></a>Versiones de sistemas operativos Linux compatibles

Se admiten las siguientes versiones de sistemas operativos Linux para DSC para Linux.

- CentOS 5, 6 y 7 (x86/x64)
- Debian GNU/Linux 6, 7 y 8 (x86/x64)
- Oracle Linux 5, 6 y 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 y 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 y 12 (x86/x64)
- Ubuntu Server 12.04 LTS, 14.04 LTS y 16.04 LTS (x86/x64)

En la tabla siguiente se describen las dependencias de paquetes necesarios para DSC para Linux.

|  Paquete necesario |  Descripción |  Versión mínima |
|---|---|---|
| glibc| Biblioteca de GNU| 2…4 – 31.30|
| python| Python| 2.4 – 3.4|
| omiserver| Infraestructura de administración abierta| 1.0.8.1|
| openssl| Bibliotecas de OpenSSL| 0.9.8 o 1.0|
| ctypes| Biblioteca de Python CTypes| Debe coincidir con la versión de Python|
| libcurl| Biblioteca de cliente http cURL| 7.15.1|

## <a name="installing-dsc-for-linux"></a>Instalación de DSC para Linux

Debe instalar la [infraestructura de administración abierta (OMI)](https://github.com/Microsoft/omi) antes de instalar DSC para Linux.

### <a name="installing-omi"></a>Instalación de la OMI

La configuración de estado deseado para Linux requiere el servidor CIM de infraestructura de administración abierta (OMI), versión 1.0.8.1 o posterior. OMI se puede descargar en The Open Group: [Infraestructura de administración abierta (OMI)](https://github.com/Microsoft/omi)

Para instalar OMI, instale el paquete que sea adecuado para su sistema Linux (.rpm o .deb) y versión de OpenSSL (ssl_098 o ssl_100), y la arquitectura (x64/x86). Los paquetes RPM son adecuados para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server y Oracle Linux. Los paquetes DEB son adecuados para Debian GNU/Linux y Ubuntu Server. Los paquetes ssl_098 son adecuados para equipos con OpenSSL 0.9.8 instalado, mientras que los paquetes ssl_100 son adecuados para equipos con OpenSSL 1.0 instalado.

> [!NOTE]
> Para determinar la versión de OpenSSL instalada, ejecute el comando `openssl version`.

Ejecute el siguiente comando para instalar OMI en un sistema con CentOS 7 x64.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>Instalación de DSC

DSC para Linux está disponible para su descarga [aquí](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).

Para instalar DSC, instale el paquete que sea adecuado para su sistema Linux (.rpm o .deb) y versión de OpenSSL (ssl_098 o ssl_100), y la arquitectura (x64/x86). Los paquetes RPM son adecuados para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server y Oracle Linux. Los paquetes DEB son adecuados para Debian GNU/Linux y Ubuntu Server. Los paquetes ssl_098 son adecuados para equipos con OpenSSL 0.9.8 instalado, mientras que los paquetes ssl_100 son adecuados para equipos con OpenSSL 1.0 instalado.

> [!NOTE]
> Para determinar la versión instalada de OpenSSL, ejecute el comando openssl version.

Ejecute el siguiente comando para instalar DSC en un sistema con CentOS 7 x64.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>Uso de DSC para Linux

En las siguientes secciones se explica cómo crear y ejecutar configuraciones DSC en equipos Linux.

### <a name="creating-a-configuration-mof-document"></a>Creación de un documento MOF de configuración

Se utiliza la palabra clave de Windows PowerShell Configuration a fin de crear una configuración para los equipos Linux, de la misma forma que para los equipos Windows. En los pasos siguientes se describe la creación de un documento de configuración para un equipo Linux con Windows PowerShell.

1. Importe el módulo nx. El módulo de Windows PowerShell nx contiene el esquema para los recursos integrados de DSC para Linux y debe instalarse en el equipo local e importarse en la configuración.

   - Para instalar el módulo nx, copie el directorio del módulo nx en `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` o `$PSHOME\Modules`. El módulo nx se incluye en la DSC para paquetes de instalación de Linux. Para importar el módulo nx en la configuración, utilice el comando `Import-DSCResource`:

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. Defina una configuración y genere el documento de configuración:

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a>Insertar la configuración en el equipo Linux

Los documentos de configuración (archivos MOF) se pueden insertar en el equipo Linux mediante el cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration). Para usar este cmdlet, junto con los cmdlets [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) o [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), de forma remota en un equipo Linux, debe usar un elemento CIMSession. El cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) se usa para crear un elemento CIMSession para el equipo Linux.

En el código siguiente se muestra cómo crear un elemento CIMSession de DSC para Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> En el modo "Push", la credencial de usuario debe ser un usuario raíz del equipo Linux.
> Solo se admiten conexiones SSL/TLS de DSC para Linux, el cmdlet `New-CimSession` debe utilizarse con el parámetro -UseSSL establecido en $true.
> El certificado SSL que utiliza OMI (para DSC) se especifica en el archivo `/etc/opt/omi/conf/omiserver.conf` con las propiedades pemfile y keyfile.
> Si este certificado no es de confianza para el equipo de Windows en el que se está ejecutando el cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession), puede elegir omitir la validación de certificados con las opciones de CIMSession `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`

Ejecute el comando siguiente para insertar la configuración DSC en el nodo de Linux.

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Distribuir la configuración con un servidor de extracción

Las configuraciones se pueden distribuir a un equipo Linux con un servidor de extracción, igual que con equipos Windows. Para obtener instrucciones sobre el uso de un servidor de extracción, consulte [Servidores de extracción de la configuración de estado deseado de Windows PowerShell](../pull-server/pullServer.md). Para obtener información adicional y conocer las limitaciones relativas al uso de equipos Linux con un servidor de extracción, consulte las notas de la versión de la configuración de estado deseado para Linux.

### <a name="working-with-configurations-locally"></a>Trabajar con configuraciones de forma local

DSC para Linux incluye scripts para trabajar con la configuración del equipo Linux local. Estos scripts se encuentran en `/opt/microsoft/dsc/Scripts` e incluyen lo siguiente:

- GetDscConfiguration.py

Devuelve la configuración actual que se aplica al equipo. Es similar al cmdlet de Windows PowerShell `Get-DscConfiguration`.

`# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

Devuelve la metaconfiguración actual que se aplica al equipo. Es similar al cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

`# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

Instala un módulo de recursos de DSC personalizado. Requiere la ruta de acceso a un archivo .zip que contenga la biblioteca de objetos compartidos del módulo y los archivos MOF del esquema.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

Quita un módulo de recursos de DSC personalizado. Requiere el nombre del módulo que se va a quitar.

`# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

Aplica un archivo MOF de configuración en el equipo. Es similar al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration). Requiere la ruta de acceso al MOF de configuración que se va a aplicar.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

Aplica a un archivo MOF de metaconfiguración en el equipo. Es similar al cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager). Requiere la ruta de acceso al MOF de metaconfiguración que se va a aplicar.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>Archivos de registro de la configuración de estado deseado para Linux de PowerShell

Los siguientes archivos de registro son mensajes generados para DSC para Linux.

|Archivo de registro|Directory|Descripción|
|---|---|---|
|**omiserver.log**|`/var/opt/omi/log`|Mensajes relacionados con la operación del servidor CIM OMI.|
|**dsc.log**|`/var/opt/omi/log`|Mensajes relacionados con el funcionamiento del administrador de configuración local (LCM) y las operaciones de recursos de DSC.|
