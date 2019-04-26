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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082321"
---
# <a name="how-to-update-help-files"></a>Cómo actualizar los archivos de Ayuda

En este tema se explica cómo actualizar los archivos de ayuda para un módulo que admite la Ayuda actualizable.

## <a name="updating-help-files"></a>Actualizar los archivos de ayuda

Hay muchas razones para actualizar los archivos de ayuda, como la corrección de errores, aclarar un concepto, responder una pregunta más frecuentes, agregar nuevos archivos o agregar nuevos y mejores ejemplos.

Para actualizar un archivo de ayuda:

1. Cambiar los archivos.

2. Los archivos se traducen en otras referencias culturales de interfaz de usuario.

3. Recopilar todos los archivos de ayuda (nuevas, cambiados y sin cambios) para el módulo en cada referencia cultural de interfaz de usuario.

4. Valide los archivos con respecto al esquema XML.

5. Vuelva a generar los archivos .cab para cada referencia cultural de interfaz de usuario.

6. En el archivo XML HelpInfo, incrementar los números de versión del archivo .cab para cada referencia cultural de interfaz de usuario.

7. Cargue los archivos CAB de nuevo en la ubicación especificada por el valor de la **HelpContentUri** elemento en el archivo XML HelpInfo. Reemplazar los antiguos archivos CAB con los nuevos archivos CAB.

8. Cargue el archivo XML HelpInfo actualizado en la ubicación especificada por el **HelpInfoUri** clave en el manifiesto del módulo. Reemplace el archivo XML HelpInfo anterior con el nuevo archivo.