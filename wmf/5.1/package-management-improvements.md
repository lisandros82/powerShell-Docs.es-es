---
title: "Mejoras en la administración de paquetes en WMF 5.1 (versión preliminar)"
ms.date: 2016-07-15
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: jaimeo
contributor: jianyunt, quoctruong
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 0a5dcec1089bd07b968c61b18ca4e6d59d0afd3b
ms.openlocfilehash: 615bdf1a82dc5078ee2f37eec70a64e25b42bda2

---

# Mejoras en la administración de paquetes en WMF 5.1 (versión preliminar) #

## Mejoras en la administración de paquetes ##
Estas son las correcciones realizadas en WMF 5.1: 

### Alias de versión

**Escenario**: si tiene las versiones 1.0 y 2.0 de un paquete (P1) instaladas en el sistema y quiere desinstalar la versión 1.0, ejecutaría `Uninstall-Package -Name P1 -Version 1.0` y esperaría que se desinstalara la versión 1.0 después de ejecutar el cmdlet. Sin embargo, el resultado es que se desinstala la versión 2.0.  
    
Esto se debe a que el parámetro `-Version` es un alias del parámetro `-MinimumVersion`. Cuando PackageManagement busca un paquete cualificado con la versión mínima 1.0, devuelve la versión más reciente. Este comportamiento es el esperable en los casos normales, ya que el resultado que se suele desear es que se busque la versión más reciente. En cambio, no se debe aplicar al caso `Uninstall-Package`.
    
**Solución**: el alias `-Version` se ha quitado completamente en PackageManagement (también conocido como OneGet) y PowerShellGet. 

### Varios mensajes para arrancar el proveedor de NuGet

**Escenario**: cuando ejecuta `Find-Module` o `Install-Module` u otros cmdlets de PackageManagement en un equipo por primera vez, PackageManagement intenta arrancar el proveedor de NuGet, ya que el proveedor de PowerShellGet también usa el proveedor de NuGet para descargar los módulos de PowerShell. Luego, PackageManagement pide permiso al usuario para instalar el proveedor de NuGet. Una vez que el usuario selecciona "yes" en el arranque, se instalará la versión más reciente del proveedor de NuGet. 
    
En cambio, en algunos casos, si tiene una versión anterior del proveedor de NuGet instalada en el equipo, a veces se carga primero la versión anterior de NuGet en la sesión de PowerShell (esa es la condición de carrera en PackageManagement). En cambio, PowerShellGet requiere la versión posterior del proveedor de NuGet para funcionar, por lo que PowerShellGet solicita a PackageManagement que vuelva a arrancar el proveedor de NuGet. Esto genera varios mensajes para arrancar el proveedor de NuGet.

**Solución**: en WMF 5.1, PackageManagement carga la versión más reciente del proveedor de NuGet para evitar varios mensajes de arranque del proveedor de NuGet.

Otra posible solución es la eliminación manual de la versión anterior del proveedor de NuGet (NuGet-Anycpu.exe) desde $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies


### Compatibilidad de PackageManagement en equipos con solo acceso a la intranet

**Escenario**: en el escenario empresarial, los usuarios trabajan en un entorno en el que no hay acceso a Internet, solo a la intranet. PackageManagement no admitía este caso en WMF 5.0.

**Escenario**: en WMF 5.0, PackageManagement no era compatible con equipos que solo tuvieran acceso a la intranet (pero no a Internet).

**Solución**: en WMF 5.1, puede seguir estos pasos para que los equipos de la intranet usen PackageManagement:

1. Descargue el proveedor de NuGet desde otro equipo con conexión a Internet mediante `Install-PackageProvider -Name NuGet`.

2. Busque el proveedor de NuGet en `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` o `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Copie los archivos binarios a una carpeta o ubicación de recurso compartido de red a la que pueda tener acceso el equipo de la intranet y, luego, instale el proveedor de NuGet con `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### Mejoras del registro de eventos

Al instalar paquetes, se cambia el estado del equipo. En WMF 5.1, ahora PackageManagement registra eventos en el registro de eventos de Windows para las actividades de `Install-Package`, `Uninstall-Package` y `Save-Package`. El registro de eventos es el mismo que para PowerShell; es decir, `Microsoft-Windows-PowerShell, Operational`.

### Compatibilidad con la autenticación básica

En WMF 5.1, PackageManagement admite la búsqueda e instalación de paquetes de un repositorio que requiera autenticación básica. Puede proporcionar las credenciales para los cmdlets `Find-Package` y `Install-Package`. Por ejemplo:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### Compatibilidad para usar PackageManagement detrás de un proxy

En WMF 5.1, ahora PackageManagement toma nuevos parámetros de proxy `-ProxyCredential` y `-Proxy`. Mediante estos parámetros, es posible especificar la dirección URL y las credenciales del proxy en los cmdlets de PackageManagement. De forma predeterminada, se utiliza la configuración del proxy del sistema. Por ejemplo:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```




<!--HONumber=Sep16_HO3-->


