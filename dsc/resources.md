---
title: Recursos de DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 0a27a40b995393c41f0496a5f7fa3f56fbd865dd
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="dsc-resources"></a>Recursos de DSC

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Los recursos de la configuración de estado deseado (DSC) ofrecen los bloques de creación para una configuración DSC. Un recurso expone las propiedades que se pueden configurar (el esquema) y contiene las funciones de script de PowerShell a las que el administrador de configuración local (LCM) llama para "que sea así".

Un recurso puede modelar algo tan genérico como un archivo o tan específico como una configuración de servidor IIS.  Grupos de recursos similares se combinan en un módulo de DSC, que organiza todos los archivos necesarios en una estructura portátil que incluye los metadatos para identificar cómo están diseñados para usarse los recursos.  

En los temas siguientes se describen los recursos de DSC:

- [Recursos de DSC integrados](builtInResource.md)
- [Crear recursos de DSC personalizados](authoringResource.md)
- [Recursos de DSC integrados para Linux](lnxBuiltInResources.md)

