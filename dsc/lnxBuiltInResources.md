---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recursos de configuración de estado deseado integrados para Linux
ms.openlocfilehash: 77617b72584f39c46fc4b9eb67235378bbfc19aa
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Recursos de configuración de estado deseado integrados para Linux

Los recursos son bloques de creación que puede usar para escribir un script de configuración de estado deseado (DSC) de PowerShell. DSC para Linux incorpora un conjunto de funcionalidades integradas para configurar recursos tales como archivos y carpetas, paquetes, variables de entorno, servicios y procesos.

## <a name="built-in-resources"></a>Recursos integrados

En la tabla siguiente se ofrece una lista con estos recursos y vínculos a temas que los describen en detalle.

* [Recurso nxArchive](lnxArchiveResource.md): ofrece un mecanismo para desempaquetar archivos de almacenamiento (.tar, .zip) en una ruta específica.
* [Recurso nxEnvironment](lnxEnvironmentResource.md): administra las variables de entorno en los nodos de destino.
* [Recurso nxFile](lnxFileResource.md): administra archivos y directorios de Linux.
* [Recurso nxFileLine](lnxFileLineResource.md): administra líneas individuales de un archivo de Linux.
* [Recurso nxGroup](lnxGroupResource.md): administra grupos locales de Linux.
* [Recurso nxPackage](lnxPackageResource.md): administra paquetes en nodos de Linux.
* [Recurso nxScript](lnxScriptResource.md): ejecuta scripts en nodos de destino.
* [Recurso nxService](lnxServiceResource.md): administra servicios (demonios) de Linux.
* [Recurso nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md): administra claves ssh públicas para un usuario de Linux.
* [Recurso nxUser](lnxUserResource.md): administra usuarios locales de Linux.