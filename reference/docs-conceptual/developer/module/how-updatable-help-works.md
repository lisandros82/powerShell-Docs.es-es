---
title: Cómo funciona la ayuda actualizable | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367084"
---
# <a name="how-updatable-help-works"></a>Cómo funciona la Ayuda actualizable

En este tema se explica cómo la ayuda actualizable procesa el archivo HelpInfo XML y los archivos. CAB para cada módulo, y se instala la ayuda actualizada para los usuarios.

## <a name="the-update-help-process"></a>El proceso de Update-Help

En la lista siguiente se describen las acciones del cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cuando un usuario ejecuta un comando para actualizar los archivos de ayuda de un módulo en una referencia cultural de interfaz de usuario determinada.

1. `Update-Help` obtiene el archivo XML HelpInfo remoto de la ubicación especificada por el valor de la clave **HelpInfoURI** en el manifiesto del módulo y valida el archivo con respecto al esquema. (Para ver el esquema, vea [HELPINFO XML Schema](./helpinfo-xml-schema.md)). Después `Update-Help` busca un archivo XML HelpInfo local para el módulo en el directorio del módulo en el equipo del usuario.

2. `Update-Help` compara el número de versión de los archivos de ayuda para la referencia cultural de la interfaz de usuario especificada en los archivos XML HelpInfo remoto y local para el módulo. Si el número de versión del archivo remoto es mayor que el número de versión del archivo local, o si no hay ningún archivo XML HelpInfo local para el módulo, `Update-Help` se prepara para descargar nuevos archivos de ayuda.

3. `Update-Help` selecciona el archivo CAB para el módulo de la ubicación especificada por el elemento **HelpContentUri** en el archivo HelpInfo XML remoto. Usa el nombre del módulo, el GUID del módulo y la referencia cultural de la interfaz de usuario para identificar el archivo CAB.

4. `Update-Help` descarga el archivo CAB, lo desempaqueta, valida los archivos de contenido de ayuda y guarda los archivos de contenido de la ayuda en el subdirectorio específico del idioma del directorio del módulo en el equipo del usuario.

5. `Update-Help` crea un archivo XML HelpInfo local copiando el archivo XML HelpInfo remoto. Edita el archivo XML HelpInfo local para que incluya solo los elementos del archivo. CAB que instaló. A continuación, guarda el archivo HelpInfo XML local en el directorio de módulo y concluye la actualización.

## <a name="the-save-help-process"></a>Proceso de guardar ayuda

La lista siguiente describe las acciones de los cmdlets [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) y [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cuando un usuario ejecuta comandos para actualizar los archivos de ayuda en un recurso compartido de archivos y, a continuación, usa esos archivos para actualizar los archivos de ayuda en el equipo del usuario.

El cmdlet `Save-Help` realiza las siguientes acciones en respuesta a un comando para guardar los archivos de ayuda de un módulo en un recurso compartido de archivos especificado por el parámetro **DestinationPath** .

1. `Save-Help` obtiene el archivo XML HelpInfo remoto de la ubicación especificada por el valor de la clave **HelpInfoURI** en el manifiesto del módulo y valida el archivo con respecto al esquema. (Para ver el esquema, vea [HELPINFO XML Schema](./helpinfo-xml-schema.md)). Después `Save-Help` busca un archivo XML HelpInfo local en el directorio especificado por el parámetro **DestinationPath** en el comando `Save-Help`.

2. `Save-Help` compara el número de versión de los archivos de ayuda para la referencia cultural de la interfaz de usuario especificada en los archivos XML HelpInfo remoto y local para el módulo. Si el número de versión del archivo remoto es mayor que el número de versión del archivo local, o si no hay ningún archivo XML HelpInfo local para el módulo en el directorio **DestinationPath** , `Save-Help` se prepara para descargar nuevos archivos de ayuda.

3. `Save-Help` selecciona el archivo CAB para el módulo de la ubicación especificada por el elemento **HelpContentUri** en el archivo HelpInfo XML remoto. Usa el nombre del módulo, el GUID del módulo y la referencia cultural de la interfaz de usuario para identificar el archivo CAB.

4. `Save-Help` descarga el archivo CAB y lo guarda en el directorio **DestinationPath** (No crea ningún subdirectorio específico del lenguaje).

5. `Save-Help` crea un archivo XML HelpInfo local copiando el archivo XML HelpInfo remoto. Edita el archivo XML HelpInfo local para que incluya solo los elementos del archivo. CAB que ha guardado. A continuación, guarda el archivo HelpInfo XML local en el directorio **DestinationPath** y concluye la actualización.

   El cmdlet `Update-Help` realiza las siguientes acciones en respuesta a un comando para actualizar los archivos de ayuda en el equipo de un usuario desde los archivos de un recurso compartido de archivos especificado por el parámetro **SourcePath** .

1. `Update-Help` obtiene el archivo XML HelpInfo remoto desde el directorio **SourcePath** . A continuación, busca un archivo XML HelpInfo local en el directorio del módulo en el equipo del usuario.

2. `Update-Help` compara el número de versión de los archivos de ayuda para la referencia cultural de la interfaz de usuario especificada en los archivos XML HelpInfo remoto y local para el módulo. Si el número de versión del archivo remoto es mayor que el número de versión del archivo local, o si no hay ningún archivo XML HelpInfo local, `Update-Help` se prepara para instalar nuevos archivos de ayuda.

3. `Update-Help` selecciona el archivo CAB para el módulo del directorio **SourcePath** . Usa el nombre del módulo, el GUID del módulo y la referencia cultural de la interfaz de usuario para identificar el archivo CAB.

4. `Update-Help` Desempaqueta el archivo. CAB, valida los archivos de contenido de ayuda y guarda los archivos de contenido de la ayuda en el subdirectorio específico del idioma del directorio del módulo en el equipo del usuario.

5. `Update-Help` crea un archivo XML HelpInfo local copiando el archivo XML HelpInfo remoto. Edita el archivo XML HelpInfo local para que incluya solo los elementos del archivo. CAB que instaló. A continuación, guarda el archivo HelpInfo XML local en el directorio de módulo y concluye la actualización.