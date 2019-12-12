---
title: Cómo crear un archivo XML de HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367324"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Cómo crear un archivo HelpInfo XML

En los temas de esta sección se explica cómo crear y rellenar un archivo de información de ayuda, conocido comúnmente como "archivo XML de HelpInfo", para la característica de ayuda actualizable de Windows PowerShell.

## <a name="helpinfo-xml-file-overview"></a>Información general sobre el archivo XML HelpInfo

El archivo XML HelpInfo es la fuente principal de información sobre la ayuda actualizable para el módulo. Incluye la ubicación de los archivos de ayuda de los módulos, las referencias culturales de la interfaz de usuario admitidas y los números de versión que la ayuda actualizable usa para determinar si el usuario tiene los archivos de ayuda más recientes.

Cada módulo tiene solo un archivo XML HelpInfo, aunque el módulo incluya varios archivos de ayuda para varias referencias culturales de la interfaz de usuario. El autor del módulo crea el archivo XML HelpInfo y lo coloca en la ubicación de Internet especificada por la clave **HelpInfoUri** en el manifiesto del módulo. Cuando se actualizan y se cargan los archivos de ayuda del módulo, el autor del módulo actualiza el archivo XML HelpInfo y reemplaza el archivo XML HelpInfo original con la nueva versión.

Es fundamental mantener cuidadosamente el archivo XML HelpInfo. Si carga nuevos archivos pero olvida incrementar los números de versión, la ayuda actualizable no descargará los nuevos archivos en los equipos de los usuarios. Si agrega archivos de ayuda para una nueva referencia cultural de la interfaz de usuario, pero no actualiza el archivo XML HelpInfo o lo coloca en la ubicación correcta, la ayuda actualizable no descargará los archivos nuevos.

## <a name="in-this-section"></a>En esta sección

Esta sección incluye los temas siguientes.

- [Esquema XML de HelpInfo](./helpinfo-xml-schema.md)

- [Archivo de ejemplo XML HelpInfo](./helpinfo-xml-sample-file.md)

- [Cómo asignar un nombre a un archivo XML HelpInfo](./how-to-name-a-helpinfo-xml-file.md)

- [Cómo establecer números de versión XML de HelpInfo](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Véase también

[Compatibilidad con la ayuda actualizable](./supporting-updatable-help.md)