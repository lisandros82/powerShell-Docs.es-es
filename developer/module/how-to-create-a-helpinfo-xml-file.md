---
title: Cómo crear un archivo XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853271"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Cómo crear un archivo HelpInfo XML

En los temas de esta sección se explica cómo crear y rellenar un archivo de información de ayuda, normalmente se conoce como un "archivo de XML HelpInfo," para la característica de ayuda actualizable de Windows PowerShell.

## <a name="helpinfo-xml-file-overview"></a>Información general de archivo XML HelpInfo

El archivo XML HelpInfo es la fuente principal de información sobre la Ayuda actualizable para el módulo. Incluye la ubicación de los archivos de ayuda para los módulos, las referencias culturales de interfaz de usuario admitidas y los números de versión de ayuda actualizable se utiliza para determinar si el usuario tiene los archivos de ayuda más recientes.

Cada módulo tiene solo un archivo XML HelpInfo, incluso si el módulo incluye varios archivos de ayuda para varias referencias culturales de interfaz de usuario. El autor del módulo crea el archivo XML HelpInfo y lo coloca en la ubicación de Internet que se especifica mediante el **HelpInfoUri** clave en el manifiesto del módulo. Cuando se actualiza y se cargan los archivos de Ayuda del módulo, el autor del módulo actualiza el archivo XML HelpInfo y reemplaza el archivo XML HelpInfo original con la nueva versión.

Es fundamental que el archivo XML HelpInfo se mantiene con cuidado. Si carga nuevos archivos, pero se olvide de incrementar los números de versión, ayuda actualizable no descargará los nuevos archivos en sus equipos. Si agrega archivos de Ayuda de una nueva referencia cultural de interfaz de usuario, pero no actualizar el archivo XML HelpInfo o colocarlo en la ubicación correcta, ayuda actualizable no se descargarán los nuevos archivos.

## <a name="in-this-section"></a>En esta sección

Esta sección incluye los temas siguientes.

- [Esquema XML HelpInfo](./helpinfo-xml-schema.md)

- [Archivo de ejemplo de XML HelpInfo](./helpinfo-xml-sample-file.md)

- [Cómo denominar un archivo XML HelpInfo](./how-to-name-a-helpinfo-xml-file.md)

- [Cómo establecer números de versión de XML HelpInfo](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Véase también

[Compatibilidad con la Ayuda actualizable](./supporting-updatable-help.md)