---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Mejoras en la administración de paquetes en WMF 5.1
ms.openlocfilehash: cb19c2d71391b5729ce9d73fc6b033270f8db307
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71325113"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Mejoras en la administración de paquetes en WMF 5.1

Estas son las correcciones realizadas en WMF 5.1:

## <a name="version-alias"></a>Alias de versión

**Escenario**: si tiene las versiones 1.0 y 2.0 de un paquete (P1) instaladas en el sistema y quiere desinstalar la versión 1.0, ejecutaría `Uninstall-Package -Name P1 -Version 1.0` y esperaría que se desinstalara la versión 1.0 después de ejecutar el cmdlet. Sin embargo, el resultado es que se desinstala la versión 2.0.

Esto se debe a que el parámetro `-Version` es un alias del parámetro `-MinimumVersion`. Cuando PackageManagement busca un paquete cualificado con la versión mínima 1.0, devuelve la versión más reciente. Este comportamiento es el esperable en los casos normales, ya que el resultado que se suele desear es que se busque la versión más reciente. En cambio, no se debe aplicar al caso `Uninstall-Package`.

**Solución**: el alias `-Version` se ha quitado completamente en PackageManagement (también conocido como OneGet) y PowerShellGet.

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Varios mensajes para arrancar el proveedor de NuGet

**Escenario**: cuando ejecuta `Find-Module` o `Install-Module` u otros cmdlets de PackageManagement en un equipo por primera vez, PackageManagement intenta arrancar el proveedor de NuGet. ya que el proveedor de PowerShellGet también usa el proveedor de NuGet para descargar los módulos de PowerShell.
Luego, PackageManagement pide permiso al usuario para instalar el proveedor de NuGet. Una vez que el usuario selecciona "yes" en el arranque, se instalará la versión más reciente del proveedor de NuGet.

En cambio, en algunos casos, si tiene una versión anterior del proveedor de NuGet instalada en el equipo, a veces se carga primero la versión anterior de NuGet en la sesión de PowerShell (esa es la condición de carrera en PackageManagement). En cambio, PowerShellGet requiere la versión posterior del proveedor de NuGet para funcionar, por lo que PowerShellGet solicita a PackageManagement que vuelva a arrancar el proveedor de NuGet.
Esto genera varios mensajes para arrancar el proveedor de NuGet.

**Solución**: en WMF 5.1, PackageManagement carga la versión más reciente del proveedor de NuGet para evitar varios mensajes de arranque del proveedor de NuGet.

Otra posible solución es la eliminación manual de la versión anterior del proveedor de NuGet (NuGet-Anycpu.exe) desde $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Compatibilidad de PackageManagement en equipos con solo acceso a la intranet

**Escenario**: en el escenario empresarial, los usuarios trabajan en un entorno en el que no hay acceso a Internet, solo a la intranet. PackageManagement no admitía este caso en WMF 5.0.

**Escenario**: en WMF 5.0, PackageManagement no era compatible con equipos que solo tuvieran acceso a la intranet (pero no a Internet).

**Solución**: en WMF 5.1, puede seguir estos pasos para que los equipos de la intranet usen PackageManagement:

1. Descargue el proveedor de NuGet desde otro equipo con conexión a Internet mediante `Install-PackageProvider -Name NuGet`.

2. Busque el proveedor de NuGet en `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` o `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Copie los archivos binarios a una carpeta o ubicación de recurso compartido de red a la que pueda tener acceso el equipo de la intranet y, luego, instale el proveedor de NuGet con `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


## <a name="event-logging-improvements"></a>Mejoras del registro de eventos

Al instalar paquetes, se cambia el estado del equipo. En WMF 5.1, ahora PackageManagement registra eventos en el registro de eventos de Windows para las actividades de `Install-Package`, `Uninstall-Package` y `Save-Package`. El registro de eventos es el mismo que para PowerShell; es decir, `Microsoft-Windows-PowerShell, Operational`.

## <a name="support-for-basic-authentication"></a>Compatibilidad con la autenticación básica

En WMF 5.1, PackageManagement admite la búsqueda e instalación de paquetes de un repositorio que requiera autenticación básica. Puede proporcionar las credenciales para los cmdlets `Find-Package` y `Install-Package`. Por ejemplo:

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Compatibilidad para usar PackageManagement detrás de un proxy

En WMF 5.1, ahora PackageManagement toma nuevos parámetros de proxy `-ProxyCredential` y `-Proxy`. Mediante estos parámetros, es posible especificar la dirección URL y las credenciales del proxy en los cmdlets de PackageManagement. De forma predeterminada, se utiliza la configuración del proxy del sistema. Por ejemplo:

```powershell
Find-Package -Source https://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
