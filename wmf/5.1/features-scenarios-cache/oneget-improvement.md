---
title: Mejoras de PackageManagement (esto es, OneGet)
contributor: jianyunt, quoctruong
translationtype: Human Translation
ms.sourcegitcommit: 3b5a3bb0ef9cf123c0cee4a36890ac61431c85ff
ms.openlocfilehash: bb1129e6aa20b64e94ddb6d7b7cf7b51b1df9ca3

---

>Nota: Especifique un título descriptivo propuesto y una breve descripción

## Mejoras de PackageManagement (esto es, OneGet) ##
Las siguientes son las correcciones realizadas en WMF 5.1 para solucionar algunas de las lagunas en las experiencias de los usuarios que tenía WMF 5.0. 

1 **Alias de versión**

**Escenario**: Asumiendo que las versiones 1.0 y 2.0 de un paquete, P1, están instaladas en el sistema y que desea desinstalar la versión 1.0, debe ejecutar "uninstall-package -name P1 -version 1.0". Puede esperar que la versión 1.0 se desinstale después de que se ejecutar el cmdlet. Sin embargo, el resultado es que se desinstala la versión 2.0. 
    
La causa del problema es que el parámetro "-version" es un alias del parámetro"-minimumversion". Cuando OneGet busca un paquete cualificado con la versión mínima 1.0, devuelve la versión más reciente. Este comportamiento es el esperable en los casos normales, ya que lo que desea la mayoría de los usuarios es buscar la versión más reciente. Sin embargo, no se debe aplicar al caso uninstall-package.
    
**Solución**: Se ha quitado completamente el alias - version en OneGet y PowerShellGet. 

2 **Varios mensajes para arrancar el proveedor de NuGet**

**Escenario**: La primera vez que se ejecutan Find-Module, install-module u otro cmdlet de OneGet en una máquina, OneGet intenta arrancar el proveedor de NuGet, ya que el proveedor de PowershellGet también usa el proveedor de NuGet para descargar los módulos de PowerShell. Luego, OneGet pide permiso al usuario para instalar al proveedor de NuGet. Una vez que el usuario selecciona "yes" en el arranque, se instalará la versión más reciente del proveedor de NuGet. 
    
Sin embargo, si tiene una versión anterior del proveedor de NuGet instalada en la máquina, a veces se carga primero la versión anterior de NuGet en la sesión de PowerShell (esa es la condición de carrera en OneGet). Sin embargo, PowerShellGet requiere la versión posterior del proveedor de NuGet para funcionar, por lo que PowerShellGet solicita OneGet para volver a arrancar el proveedor de NuGet. Por eso ve varios mensajes de arranque del proveedor de NuGet.

**Solución**: OneGet carga la versión más reciente del proveedor de NuGet para evitar varios mensajes de arranque del proveedor de NuGet.

También existe una solución alternativa: si existe, elimine manualmente la versión anterior del proveedor de NuGet (NuGet-Anycpu.exe) desde $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies


3 **Máquina solo con intranet**

**Escenario**: En el escenario empresarial, los usuarios trabajan en un entorno en el que no hay acceso a Internet, solo a la intranet. OneGet no admitía este caso en WMF 5.0.

**Solución**:
- El proveedor de NuGet se puede descargar en otra máquina con conexión a Internet mediante el comando "Install-PackageProvider -Name NuGet".

- Busque el proveedor de NuGet que acaba de instalar en $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget o $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget. 

- Copie los archivos binarios a una carpeta o ubicación de recurso compartido de red a la que la máquina (la que no tiene Internet) también tenga acceso e instale el proveedor de NuGet con "Install-PackageProvider NuGet -Source <Path to folder>".


4 **Registro de eventos**

Al instalar paquetes, cambia el estado de la máquina. Para los diagnósticos, OneGet registra eventos en el registro de eventos de Windows para instalar, desinstalar y guardar paquete. El canal Evento es lo mismo que PowerShell, es decir, Microsoft-Windows-PowerShell, operativo.

5 **Compatibilidad con autenticación** OneGet ahora admite la búsqueda e instalación de paquetes de un repositorio que requiera autenticación básica. Puede proporcionar sus credenciales a los cmdlets Find-Package e Install-Package. Por ejemplo:
``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
6 **Uso de OneGet detrás de un proxy**

OneGet ahora usa los parámetros de proxy: - ProxyCredential y - Proxy. Mediante estos parámetros, puede especificar la dirección url del proxy y la credencial de proxy en los cmdlets de OneGet (de forma predeterminada, se utiliza la configuración de proxy del sistema). Por ejemplo:
``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Aug16_HO3-->


