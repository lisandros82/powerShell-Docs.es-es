---
title: "Mejoras de OneGet en WMF 5.1 (versión preliminar)"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 1d0bd545b52ef56045f2ec740b05c4e0fd93bb67

---

# Mejoras de OneGet
WMF 5.1 incluye varias correcciones y mejoras para solucionar algunos problemas con que se topaban los usuarios en la versión 5.0 de WMF. 

##Alias version quitado

**Escenario**: si tiene las versiones 1.0 y 2.0 de un paquete, P1, instaladas en el sistema y desea desinstalar la versión 1.0, ejecutaría "uninstall-package -name P1 -version 1.0" y esperaría que se desinstalara la versión 1.0 después de ejecutar el cmdlet. Sin embargo, el resultado es que se desinstala la versión 2.0. 
    
Esto se debe a que el parámetro "-version" es un alias del parámetro"-minimumversion". Cuando OneGet busca un paquete cualificado con la versión mínima 1.0, devuelve la versión más reciente. Este comportamiento es el esperable en los casos normales, ya que el resultado que se suele desear es que se busque la versión más reciente. Sin embargo, no se debe aplicar al caso uninstall-package.
    
**Solución**: en WMF 5.1, se quita completamente el alias - version en OneGet y PowerShellGet. 

##Varios mensajes para arrancar el proveedor de NuGet

**Escenario**: la primera vez que se ejecutan Find-Module, Install-module u otro cmdlet de OneGet en un equipo, OneGet intenta arrancar el proveedor de NuGet, ya que el proveedor de PowerShellGet también usa el proveedor de NuGet para descargar los módulos de PowerShell. Luego, OneGet pide permiso al usuario para instalar al proveedor de NuGet. Una vez que el usuario selecciona "yes" en el arranque, se instalará la versión más reciente del proveedor de NuGet. 
    
Sin embargo, en algunos casos, si tiene una versión anterior del proveedor de NuGet instalada en el equipo, a veces se carga primero la versión anterior de NuGet en la sesión de PowerShell (esa es la condición de carrera en OneGet). Sin embargo, PowerShellGet requiere la versión posterior del proveedor de NuGet para funcionar, por lo que PowerShellGet solicita OneGet para volver a arrancar el proveedor de NuGet. Esto genera varios mensajes para arrancar el proveedor de NuGet.

**Solución**: en WMF 5.1, OneGet carga la versión más reciente del proveedor de NuGet para evitar varios mensajes de arranque del proveedor de NuGet.

Otra posible solución es la eliminación manual de la versión anterior del proveedor de NuGet (NuGet-Anycpu.exe) desde $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies


##Compatibilidad con OneGet en equipos con acceso solo a la intranet

**Escenario**: en WMF 5.0, OneGet no era compatible con equipos que solo tuvieran acceso a la intranet (pero no a Internet).

**Solución**: en WMF 5.1, puede seguir estos pasos para que los equipos de la intranet usen OneGet:

1. Descargue el proveedor de NuGet desde otro equipo con conexión a Internet mediante Install-PackageProvider NuGet.

2. Busque el proveedor de NuGet en $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget o $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget. 

3. Copie los archivos binarios a una carpeta o ubicación de recurso compartido de red a la que pueda acceder el equipo de la intranet y luego instale el proveedor de NuGet con "Install-PackageProvider NuGet -Source <Path to folder>".


##Mejoras del registro de eventos

Al instalar paquetes, se cambia el estado del equipo. En WMF 5.1, OneGet registra eventos en el registro de eventos de Windows para las actividades de instalar, desinstalar y guardar paquete. El canal Evento es lo mismo que para PowerShell, es decir, Microsoft-Windows-PowerShell, operativo.

##Compatibilidad con la autenticación básica

En WMF 5.1, OneGet admite la búsqueda e instalación de paquetes de un repositorio que requiera autenticación básica. Puede proporcionar sus credenciales a los cmdlets Find-Package e Install-Package. Por ejemplo:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
##Compatibilidad para usar OneGet detrás de un proxy

En WMF 5.1, OneGet usa nuevos parámetros de proxy: - ProxyCredential y - Proxy. Mediante estos parámetros, es posible especificar la dirección URL y las credenciales del proxy en los cmdlets de OneGet. De forma predeterminada, se utiliza la configuración del proxy del sistema. Por ejemplo:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO3-->


