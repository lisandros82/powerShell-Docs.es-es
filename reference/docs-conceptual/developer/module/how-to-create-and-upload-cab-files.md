---
title: Cómo crear y cargar archivos. CAB | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367334"
---
# <a name="how-to-create-and-upload-cab-files"></a>Cómo crear y cargar archivos CAB

En este tema se explica cómo crear archivos CAB de ayuda actualizable y cómo cargarlos en la ubicación donde los cmdlets de ayuda actualizables pueden encontrarlos.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Cómo crear y cargar archivos CAB de ayuda actualizable

Puede usar la característica de ayuda actualizable para ofrecer archivos de ayuda nuevos o actualizados para un módulo en varios idiomas y referencias culturales. Un paquete de ayuda actualizable de un módulo consta de un archivo XML HelpInfo y uno o varios contenedores (. Archivos. CAB). Cada archivo. CAB contiene archivos de ayuda para el módulo en una referencia cultural de la interfaz de usuario. Utilice el procedimiento siguiente para crear archivos. CAB para obtener ayuda actualizable.

1. Organice los archivos de ayuda del módulo por referencia cultural de la interfaz de usuario. Cada archivo. CAB de ayuda actualizable contiene los archivos de ayuda de un módulo en una referencia cultural de la interfaz de usuario. Puede proporcionar varios archivos CAB de ayuda para el módulo, cada uno para una referencia cultural de interfaz de usuario diferente.

2. Compruebe que los archivos de ayuda incluyen solo los tipos de archivo permitidos para la ayuda actualizable y los validan con respecto a un esquema de archivo de ayuda. Si el cmdlet `Update-Help` encuentra un archivo que no es válido o que no es un tipo permitido, no instala el archivo no válido y deja de instalar archivos del archivo CAB. Para obtener una lista de los tipos de archivo permitidos, consulte [tipos de archivo permitidos en un archivo CAB de ayuda actualizable](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. Firmar digitalmente los archivos de ayuda. No se requieren firmas digitales, pero es un procedimiento recomendado.

4. Incluya todos los archivos de ayuda del módulo en la referencia cultural de la interfaz de usuario, no solo los archivos que son nuevos o han cambiado. Si el archivo CAB está incompleto, los usuarios que descarguen los archivos de ayuda por primera vez o no descarguen todas las actualizaciones, no tendrán todos los archivos de ayuda del módulo.

5. Use una utilidad que cree archivos. cab, como MakeCab. exe. Windows PowerShell no incluye cmdlets que crean archivos. CAB.

6. Asigne un nombre a los archivos. CAB. Para obtener más información, consulte [asignar un nombre a un archivo. cab de ayuda actualizable](./how-to-name-an-updatable-help-cab-file.md).

7. Cargue los archivos. CAB para el módulo en la ubicación especificada por el elemento **HelpContentUri** en el archivo XML HelpInfo para el módulo. Después, cargue el archivo XML HelpInfo en la ubicación especificada por la clave **HelpInfoUri** del manifiesto del módulo. **HelpContentUri** y **HelpInfoUri** pueden apuntar a la misma ubicación.

> [!CAUTION]
> El valor de la clave **HelpInfoUri** y el elemento **HelpContentUri** debe empezar por "http" o "https". El valor debe indicar una ubicación de Internet y no debe incluir un nombre de archivo.