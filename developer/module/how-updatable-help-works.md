---
title: Cómo Updatable Help funciona | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082267"
---
# <a name="how-updatable-help-works"></a>Cómo funciona la Ayuda actualizable

En este tema se explica cómo los procesos de ayuda actualizable el archivo XML HelpInfo CAB archivos para cada módulo y se instala actualizan la ayuda para los usuarios.

## <a name="the-update-help-process"></a>El proceso de Update-Help

En la lista siguiente se describe las acciones de la [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet cuando un usuario ejecuta un comando para actualizar los archivos de Ayuda de un módulo en una determinada referencia cultural de interfaz de usuario.

1. `Update-Help` Obtiene el archivo XML HelpInfo remoto desde la ubicación especificada por el valor de la **HelpInfoURI** clave en el manifiesto del módulo y valida el archivo con el esquema. (Para ver el esquema, consulte [HelpInfo XML Schema](./helpinfo-xml-schema.md).) A continuación, `Update-Help` busca un archivo XML HelpInfo local para el módulo en el directorio del módulo en el equipo del usuario.

2. `Update-Help` Compara el número de versión de los archivos de ayuda para la referencia cultural de interfaz de usuario especificada en los archivos XML HelpInfo locales y remotos para el módulo. Si el número de versión en el archivo remoto es mayor que el número de versión en el archivo local, o si no existe ningún archivo XML HelpInfo local para el módulo, `Update-Help` se prepara para descargar nuevos archivos de ayuda.

3. `Update-Help` selecciona el archivo CAB para el módulo de la ubicación especificada por el **HelpContentUri** elemento en el archivo XML HelpInfo remoto. El nombre del módulo, el GUID del módulo y la referencia cultural de interfaz de usuario usa para identificar el archivo CAB.

4. `Update-Help` descarga el archivo CAB, se desempaqueta, valida los archivos de contenido de ayuda y guarda los archivos de contenido de la Ayuda en el subdirectorio específico del lenguaje del directorio de módulo en el equipo del usuario.

5. `Update-Help` crea un archivo XML HelpInfo local copiando el archivo XML HelpInfo remoto. Edita el archivo XML HelpInfo local para que incluya elementos solo para el archivo CAB que instala. A continuación, guarda el archivo XML HelpInfo local en el directorio del módulo y finaliza la actualización.

## <a name="the-save-help-process"></a>El proceso de Save-Help

En la lista siguiente se describe las acciones de la [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) y [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets cuando un usuario ejecuta los comandos para actualizar los archivos de ayuda en un recurso compartido de archivos y, a continuación, usar esos archivos para actualizar los archivos de ayuda en el equipo del usuario.

El `Save-Help` cmdlet realiza las siguientes acciones en respuesta a un comando para guardar los archivos de ayuda para un módulo en un recurso compartido de archivos especificado por el **DestinationPath** parámetro.

1. `Save-Help` Obtiene el archivo XML HelpInfo remoto desde la ubicación especificada por el valor de la **HelpInfoURI** clave en el manifiesto del módulo y valida el archivo con el esquema. (Para ver el esquema, consulte [HelpInfo XML Schema](./helpinfo-xml-schema.md).) A continuación, `Save-Help` busca un archivo XML HelpInfo local en el directorio especificado por el **DestinationPath** parámetro en el `Save-Help` comando.

2. `Save-Help` Compara el número de versión de los archivos de ayuda para la referencia cultural de interfaz de usuario especificada en los archivos XML HelpInfo locales y remotos para el módulo. Si el número de versión en el archivo remoto es mayor que el número de versión en el archivo local, o si no existe ningún archivo XML HelpInfo local para el módulo en el **DestinationPath** directorio, `Save-Help` se prepara para descargar nuevos archivos de ayuda.

3. `Save-Help` selecciona el archivo CAB para el módulo de la ubicación especificada por el **HelpContentUri** elemento en el archivo XML HelpInfo remoto. El nombre del módulo, el GUID del módulo y la referencia cultural de interfaz de usuario usa para identificar el archivo CAB.

4. `Save-Help` descarga el archivo .cab y lo guarda en el **DestinationPath** directory. (No crea los subdirectorios específicos del lenguaje).

5. `Save-Help` crea un archivo XML HelpInfo local copiando el archivo XML HelpInfo remoto. Edita el archivo XML HelpInfo local para que incluya elementos solo para el archivo CAB que guardó. Después, guarda el archivo XML HelpInfo local en el **DestinationPath** directorio y finaliza la actualización.

   El `Update-Help` cmdlet realiza las siguientes acciones en respuesta a un comando para actualizar los archivos de ayuda en el equipo del usuario de los archivos en un recurso compartido de archivos especificado por el **SourcePath** parámetro.

1. `Update-Help` Obtiene el archivo XML HelpInfo remoto desde el **SourcePath** directory. A continuación, busca un archivo XML HelpInfo local en el directorio del módulo en el equipo del usuario.

2. `Update-Help` Compara el número de versión de los archivos de ayuda para la referencia cultural de interfaz de usuario especificada en los archivos XML HelpInfo locales y remotos para el módulo. Si el número de versión en el archivo remoto es mayor que el número de versión en el archivo local, o si no existe ningún archivo XML HelpInfo local, `Update-Help` se prepara para instalar nuevos archivos de ayuda.

3. `Update-Help` selecciona el archivo CAB para el módulo de **SourcePath** directory. El nombre del módulo, el GUID del módulo y la referencia cultural de interfaz de usuario usa para identificar el archivo CAB.

4. `Update-Help` Desempaquete el archivo CAB, valida los archivos de contenido de ayuda y guarda los archivos de contenido de la Ayuda en el subdirectorio específico del lenguaje del directorio de módulo en el equipo del usuario.

5. `Update-Help` crea un archivo XML HelpInfo local copiando el archivo XML HelpInfo remoto. Edita el archivo XML HelpInfo local para que incluya elementos solo para el archivo CAB que instala. A continuación, guarda el archivo XML HelpInfo local en el directorio del módulo y finaliza la actualización.