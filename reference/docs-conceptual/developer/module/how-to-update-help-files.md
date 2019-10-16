---
title: Cómo actualizar los archivos de ayuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367144"
---
# <a name="how-to-update-help-files"></a>Cómo actualizar los archivos de Ayuda

En este tema se explica cómo actualizar los archivos de ayuda de un módulo que admite la ayuda actualizable.

## <a name="updating-help-files"></a>Actualizar archivos de ayuda

Hay muchas razones para actualizar los archivos de ayuda, como corregir errores, aclarar un concepto, responder a preguntas frecuentes, agregar nuevos archivos o agregar nuevos y mejores ejemplos.

Para actualizar un archivo de ayuda:

1. Cambie los archivos.

2. Traduzca los archivos a otras referencias culturales de la interfaz de usuario.

3. Recopilar todos los archivos de ayuda (nuevos, modificados y sin cambios) para el módulo en cada referencia cultural de la interfaz de usuario.

4. Valide los archivos con el esquema XML.

5. Recompile los archivos. CAB para cada referencia cultural de la interfaz de usuario.

6. En el archivo XML HelpInfo, incremente los números de versión del archivo. CAB para cada referencia cultural de la interfaz de usuario.

7. Cargue los nuevos archivos. CAB en la ubicación especificada por el valor del elemento **HelpContentUri** en el archivo XML de HelpInfo. Reemplace los archivos CAB antiguos por los nuevos archivos. CAB.

8. Cargue el archivo XML HelpInfo actualizado en la ubicación especificada por la clave **HelpInfoUri** en el manifiesto del módulo. Reemplace el archivo XML HelpInfo anterior por el nuevo archivo.