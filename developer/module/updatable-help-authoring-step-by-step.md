---
title: 'Creación de la Ayuda actualizable: Paso a paso | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082131"
---
# <a name="updatable-help-authoring-step-by-step"></a>Creación de la Ayuda actualizable: paso a paso

En este documentos se enumeran los pasos del proceso de creación de ayuda actualizable.

## <a name="authoring-updatable-help-step-by-step"></a>La Ayuda actualizable de creación: paso a paso

La Ayuda actualizable está diseñada para usuarios finales, pero también proporciona ventajas importantes a los autores de módulos y escritores de ayuda, incluida la capacidad para agregar contenido, corregirán los errores, entregar en varias referencias culturales de interfaz de usuario y responden a solicitudes y los comentarios del usuario después de la módulo se ha enviado. En este tema se explica cómo empaqueta y ayuda de la carga de archivos para que los usuarios pueden descargarlas e instalarlas mediante el uso de la [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.

Los pasos siguientes proporcionan una visión general del proceso de compatibilidad con la Ayuda actualizable.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Paso 1: Buscar un sitio de Internet para los archivos de ayuda

El primer paso en la creación de la Ayuda actualizable es buscar una ubicación de Internet para los archivos de Ayuda de su módulo. En realidad, puede usar dos ubicaciones diferentes. Puede mantener el archivo de información de su módulo ayuda (HelpInfo XML: se describe a continuación) en una ubicación de Internet y los archivos CAB contenidos de ayuda en otra ubicación de Internet. Todos los archivos de CAB contenido ayuda para un módulo deben estar en la misma ubicación. Puede colocar archivos CAB contenidos de ayuda para los distintos módulos en la misma ubicación.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Paso 2: Agregar una clave HelpInfoURI al manifiesto de módulo

Agregar un **HelpInfoURI** clave al manifiesto de módulo. El valor de la clave es el identificador uniforme de recursos (URI) de la ubicación del archivo de información XML HelpInfo para el módulo. Para la seguridad, la dirección debe comenzar con "http" o "https". El URI debe especificar una ubicación de Internet, pero no debe incluir el nombre del archivo XML HelpInfo.

Por ejemplo:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Paso 3: Cree un archivo XML HelpInfo

El archivo de información XML HelpInfo contiene el URI de la ubicación de Internet de los archivos de ayuda y los números de versión de los archivos de ayuda más recientes para el módulo en cada referencia cultural de interfaz de usuario admitida. Cada módulo de Windows PowerShell tiene un archivo XML HelpInfo. Al actualizar los archivos de ayuda, editar o reemplazar el archivo XML HelpInfo; No agregue otro. Para obtener más información, consulte [cómo crear un archivo de XML HelpInfo](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Paso 4: Firme los archivos de ayuda

Las firmas digitales no son necesarias, pero son una práctica recomendada cuando el uso compartido de archivos.

### <a name="step-5-create-cab-files"></a>Paso 5: Crear archivos CAB

Usar una herramienta que crea archivos de contenedor (.cab), como MakeCab.exe para crear una. Archivo CAB que contiene los archivos de ayuda para el módulo. Cree un archivo .cab independiente para los archivos de ayuda en cada referencia cultural de interfaz de usuario admitida. Para obtener más información, consulte [cómo preparar actualizable ayudan a los archivos CAB](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Paso 6: Cargar los archivos

Para publicar los archivos de ayuda nuevos o actualizados, cargar los archivos .cab a la ubicación de Internet que se especifica mediante el **HelpContentUri** elemento en el archivo XML HelpInfo. A continuación, cargue el archivo XML HelpInfo para la ubicación de Internet que se especifica mediante el valor de la **HelpInfoUri** clave en el manifiesto del módulo.
