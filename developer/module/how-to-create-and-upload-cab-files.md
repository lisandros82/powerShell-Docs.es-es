---
title: Cómo crear y cargar archivos CAB | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858651"
---
# <a name="how-to-create-and-upload-cab-files"></a>Cómo crear y cargar archivos CAB

En este tema se explica cómo crear archivos CAB de ayuda actualizable y cargarlos en la ubicación donde puede encontrar los cmdlets de ayuda actualizable.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Cómo crear y cargar los archivos CAB de ayuda actualizable

Puede usar la característica de ayuda actualizable para entregar archivos de ayuda nuevos o actualizados para un módulo en varios idiomas y referencias culturales. Un paquete de ayuda actualizable de un módulo consta de un archivo XML HelpInfo y uno o varios del gabinete (. Archivos CAB). Cada archivo .cab contiene los archivos de ayuda para el módulo en una referencia cultural de interfaz de usuario. Use el procedimiento siguiente para crear archivos CAB de ayuda actualizable.

1. Organizar los archivos de ayuda para el módulo mediante la referencia cultural de interfaz de usuario. Cada archivo .cab de ayuda actualizable contiene los archivos de ayuda para un módulo en una referencia cultural de interfaz de usuario. Puede ofrecer ayuda varios archivos .cab para el módulo, cada uno para una referencia cultural de interfaz de usuario diferente.

2. Compruebe que los archivos de ayuda incluye solo los tipos de archivo permitidos para Ayuda actualizable y validarlas en un esquema de archivo de ayuda. Si el `Update-Help` cmdlet encuentra un archivo que no es válido o no es un tipo permitido, no se instala el archivo no válido y se detiene la instalación de archivos desde el archivo CAB. Para obtener una lista de tipos de archivo permitidos, consulte [permiten tipos de archivo en un archivo CAB de ayuda actualizable](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. Firmar digitalmente los archivos de ayuda. Las firmas digitales no son necesarias, pero son una práctica recomendada.

4. Incluir todos los archivos del módulo en la interfaz de usuario de la referencia cultural, no sólo los archivos que son nuevos o han cambiado de ayuda. Si el archivo .cab está incompleto, los usuarios descargar archivos de ayuda por primera vez o descargar todas las actualizaciones, no tendrá todos los archivos de Ayuda del módulo.

5. Usar una utilidad que crea archivos contenedores, como MakeCab.exe. Windows PowerShell no incluye los cmdlets que crean archivos CAB.

6. Nombre de los archivos CAB. Para obtener más información, consulte [cómo denominar un archivo CAB de ayuda actualizable](./how-to-name-an-updatable-help-cab-file.md).

7. Cargue los archivos .cab para el módulo en la ubicación especificada por el **HelpContentUri** elemento en el archivo XML HelpInfo para el módulo. A continuación, cargue el archivo XML HelpInfo a la ubicación especificada por el **HelpInfoUri** clave del manifiesto del módulo. El **HelpContentUri** y **HelpInfoUri** puede apuntar a la misma ubicación.

> [!CAUTION]
> El valor de la **HelpInfoUri** clave y el **HelpContentUri** elemento debe empezar por "http" o "https". El valor debe indicar una ubicación de Internet y no debe incluir un nombre de archivo.