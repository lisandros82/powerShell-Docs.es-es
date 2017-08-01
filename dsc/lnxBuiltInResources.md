---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Recursos de configuración de estado deseado integrados para Linux"
ms.openlocfilehash: b85f32f7559d89bda566d35462cc613d73424c50
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
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
  
