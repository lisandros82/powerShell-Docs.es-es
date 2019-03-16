---
title: Cómo establecer números de versión XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054142"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>Cómo establecer números de versión de HelpInfo XML

En este tema se explica cómo establecer y aumentar los números de versión en un archivo de información de ayuda actualizable, conocido comúnmente como "archivo XML HelpInfo".

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>Cómo establecer números de versión de HelpInfo XML

Los números de versión en un archivo XML HelpInfo son fundamentales para el funcionamiento de la Ayuda actualizable.
El [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets descargar nuevos archivos de ayuda solo cuando el número de versión para una referencia cultural de interfaz de usuario en el archivo XML HelpInfo remoto es mayor que el número de versión para esa referencia cultural de interfaz de usuario en el XML HelpInfo local, o no hay ningún archivo XML HelpInfo local.

El archivo XML HelpInfo utiliza el número de versión de 4 partes que se define en el **System.Version** clase de Microsoft .NET Framework. El formato es `N1.N2.N3.N4`. Los autores del módulo pueden usar cualquier versión de esquema que está permitido por la numeración del **System.Version** clase. La Ayuda actualizable requiere solo que el número de versión para un aumento de la referencia cultural de interfaz de usuario cuando se cargue una nueva versión del archivo CAB para esa referencia cultural de interfaz de usuario en la ubicación especificada por el **HelpContentURI** elemento en el archivo XML HelpInfo.

El ejemplo siguiente muestra los elementos del archivo XML HelpInfo para el alemán (de-DE) la interfaz de usuario de la referencia cultural cuando la versión es 2.15.0.10.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

El número de versión para una referencia cultural de interfaz de usuario refleja la versión del archivo CAB para esa referencia cultural de interfaz de usuario. El número de versión se aplica a todo el archivo CAB. No se puede establecer números de versión diferentes para distintos archivos en el archivo CAB. El número de versión para cada referencia cultural de interfaz de usuario se evalúa de forma independiente y no necesita estar relacionado con los números de versión para otras referencias culturales de interfaz de usuario que admite el módulo.