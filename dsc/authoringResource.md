---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Crear recursos de configuración de estado deseado de Windows PowerShell personalizados"
ms.openlocfilehash: 75b494db4ee6e381491decb11d35b60105217a0f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Crear recursos de configuración de estado deseado de Windows PowerShell personalizados

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La configuración de estado deseado (DSC) de Windows PowerShell tiene recursos integrados que puede usar para configurar el entorno. (Para más información, consulte [Recursos de configuración de estado deseado de Windows PowerShell integrados](builtInResource.md)). En este tema se ofrece información general sobre el desarrollo de recursos y vínculos a temas con información específica y ejemplos.

## <a name="dsc-resource-components"></a>Componentes de recursos de DSC

Un recurso de DSC es un módulo de Windows PowerShell. El módulo contiene el esquema (la definición de las propiedades configurables) y la implementación (el código que realiza el trabajo real especificado por una configuración) del recurso. Un esquema de recursos de DSC se puede definir en un archivo MOF y la implementación se realiza mediante un módulo de script. A partir de la compatibilidad de las clases de PowerShell de la versión 5, tanto el esquema como la implementación se pueden definir en una clase. En los temas siguientes se describe con más detalle cómo crear recursos de DSC.

* [Escribir un recurso de DSC personalizado con MOF](authoringResourceMOF.md) 
* [Implementación de un recurso de DSC en C#](authoringResourceMofCS.md) 
* [Escribir un recurso de DSC personalizado con clases de PowerShell](authoringResourceClass.md) 
* [Recursos compuestos: uso de una configuración DSC como un recurso](authoringResourceComposite.md) 
* [Uso de la herramienta Diseñador de recursos](authoringResourceMofDesigner.md) 

