---
title: Cómo establecer los números de versión XML de HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360684"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>Cómo establecer números de versión de HelpInfo XML

En este tema se explica cómo establecer y aumentar los números de versión en un archivo de información de ayuda actualizable, conocido comúnmente como "archivo XML de HelpInfo".

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>Cómo establecer números de versión de HelpInfo XML

Los números de versión de un archivo XML HelpInfo son fundamentales para el funcionamiento de la ayuda actualizable.
Los cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) descargan nuevos archivos de ayuda solo cuando el número de versión de una referencia cultural de la interfaz de usuario en el archivo XML HelpInfo remoto es mayor que el número de versión de esa referencia cultural de la interfaz de usuario en el XML de HelpInfo local o no hay ningún archivo XML HelpInfo local.

El archivo XML HelpInfo usa el número de versión de 4 partes que se define en la clase **System. version** del marco de Microsoft .net. El formato es `N1.N2.N3.N4`. Los autores de módulos pueden usar cualquier esquema de numeración de versiones permitido por la clase **System. version** . La ayuda actualizable solo requiere que el número de versión de una referencia cultural de la interfaz de usuario aumente cuando se cargue una nueva versión del archivo. CAB para esa referencia cultural de la interfaz de usuario en la ubicación especificada por el elemento **HelpContentURI** en el archivo XML de HelpInfo.

En el ejemplo siguiente se muestran los elementos del archivo XML HelpInfo para la referencia cultural de la interfaz de usuario alemana (de-DE) cuando la versión es 2.15.0.10.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

El número de versión de una referencia cultural de la interfaz de usuario refleja la versión del archivo. CAB para esa referencia cultural de la interfaz de usuario. El número de versión se aplica a todo el archivo. CAB. No se pueden establecer números de versión diferentes para los distintos archivos del archivo. CAB. El número de versión de cada referencia cultural de la interfaz de usuario se evalúa de forma independiente y no debe estar relacionado con los números de versión de otras referencias culturales de la interfaz de usuario que admite el módulo.