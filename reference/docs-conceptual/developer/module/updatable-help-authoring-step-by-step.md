---
title: 'Creación de ayuda actualizable: paso a paso | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366994"
---
# <a name="updatable-help-authoring-step-by-step"></a>Creación de la Ayuda actualizable: paso a paso

En este documento se enumeran los pasos del proceso de creación de la ayuda actualizable.

## <a name="authoring-updatable-help-step-by-step"></a>Creación de ayuda actualizable: paso a paso

La ayuda actualizable está diseñada para los usuarios finales, pero también proporciona importantes ventajas a los autores de módulos y escritores de ayuda, incluida la capacidad de agregar contenido, corregir errores, proporcionar varias culturas de la interfaz de usuario y responder a las solicitudes y los comentarios de los usuarios, mucho después de la el módulo se ha enviado. En este tema se explica cómo empaquetar y cargar archivos de ayuda para que los usuarios puedan descargarlos e instalarlos mediante los cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

En los pasos siguientes se proporciona información general sobre el proceso de compatibilidad con la ayuda actualizable.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Paso 1: buscar un sitio de Internet para los archivos de ayuda

El primer paso para crear la ayuda actualizable es encontrar una ubicación de Internet para los archivos de ayuda del módulo. En realidad, puede usar dos ubicaciones diferentes. Puede conservar el archivo de información de ayuda (HelpInfo XML) en una ubicación de Internet y los archivos. CAB de contenido de la ayuda en otra ubicación de Internet. Todos los archivos CAB de contenido de ayuda de un módulo deben estar en la misma ubicación. Puede colocar archivos CAB de contenido de ayuda para distintos módulos en la misma ubicación.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Paso 2: agregar una clave de HelpInfoURI al manifiesto del módulo

Agregue una clave **HelpInfoURI** al manifiesto del módulo. El valor de la clave es el identificador uniforme de recursos (URI) de la ubicación del archivo de información XML HelpInfo para el módulo. Por seguridad, la dirección debe comenzar con "http" o "https". El URI debe especificar una ubicación de Internet, pero no debe incluir el nombre de archivo XML de HelpInfo.

Por ejemplo:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Paso 3: crear un archivo XML de HelpInfo

El archivo de información XML HelpInfo contiene el URI de la ubicación de Internet de los archivos de ayuda y los números de versión de los archivos de ayuda más recientes para el módulo en cada referencia cultural de interfaz de usuario admitida. Cada módulo de Windows PowerShell tiene un archivo XML HelpInfo. Al actualizar los archivos de ayuda, se edita o reemplaza el archivo XML HelpInfo; no agrega otro. Para obtener más información, vea [Cómo crear un archivo XML de HelpInfo](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Paso 4: firmar los archivos de ayuda

No se requieren firmas digitales, pero se recomiendan las prácticas recomendadas cada vez que comparta archivos.

### <a name="step-5-create-cab-files"></a>Paso 5: crear archivos. CAB

Use una herramienta que cree archivos contenedores (. cab), como MakeCab. exe, para crear un. Archivo. CAB que contiene los archivos de ayuda del módulo. Cree un archivo CAB independiente para los archivos de ayuda en cada referencia cultural de interfaz de usuario admitida. Para obtener más información, vea [Cómo preparar archivos. cab de ayuda actualizable](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Paso 6: carga de los archivos

Para publicar archivos de ayuda nuevos o actualizados, cargue los archivos. CAB en la ubicación de Internet especificada por el elemento **HelpContentUri** en el archivo XML HelpInfo. Después, cargue el archivo XML HelpInfo en la ubicación de Internet especificada por el valor de la clave **HelpInfoUri** en el manifiesto del módulo.
