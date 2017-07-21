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
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="b0fc4-103">Recursos de configuración de estado deseado integrados para Linux</span><span class="sxs-lookup"><span data-stu-id="b0fc4-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="b0fc4-104">Los recursos son bloques de creación que puede usar para escribir un script de configuración de estado deseado (DSC) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="b0fc4-105">DSC para Linux incorpora un conjunto de funcionalidades integradas para configurar recursos tales como archivos y carpetas, paquetes, variables de entorno, servicios y procesos.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="b0fc4-106">Recursos integrados</span><span class="sxs-lookup"><span data-stu-id="b0fc4-106">Built-in resources</span></span> 

<span data-ttu-id="b0fc4-107">En la tabla siguiente se ofrece una lista con estos recursos y vínculos a temas que los describen en detalle.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="b0fc4-108">[Recurso nxArchive](lnxArchiveResource.md): ofrece un mecanismo para desempaquetar archivos de almacenamiento (.tar, .zip) en una ruta específica.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="b0fc4-109">[Recurso nxEnvironment](lnxEnvironmentResource.md): administra las variables de entorno en los nodos de destino.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span> 
* <span data-ttu-id="b0fc4-110">[Recurso nxFile](lnxFileResource.md): administra archivos y directorios de Linux.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span> 
* <span data-ttu-id="b0fc4-111">[Recurso nxFileLine](lnxFileLineResource.md): administra líneas individuales de un archivo de Linux.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span> 
* <span data-ttu-id="b0fc4-112">[Recurso nxGroup](lnxGroupResource.md): administra grupos locales de Linux.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span> 
* <span data-ttu-id="b0fc4-113">[Recurso nxPackage](lnxPackageResource.md): administra paquetes en nodos de Linux.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="b0fc4-114">[Recurso nxScript](lnxScriptResource.md): ejecuta scripts en nodos de destino.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="b0fc4-115">[Recurso nxService](lnxServiceResource.md): administra servicios (demonios) de Linux.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="b0fc4-116">[Recurso nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md): administra claves ssh públicas para un usuario de Linux.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span> 
* <span data-ttu-id="b0fc4-117">[Recurso nxUser](lnxUserResource.md): administra usuarios locales de Linux.</span><span class="sxs-lookup"><span data-stu-id="b0fc4-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span> 
  
