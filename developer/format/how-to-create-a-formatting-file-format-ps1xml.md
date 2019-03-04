---
title: Cómo crear un archivo de formato (. format.ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862971"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Cómo crear un archivo de formato (. format.ps1xml)

Este tema describe cómo crear un archivo de formato (. format.ps1xml).

> [!NOTE]
> También puede crear un archivo de formato mediante la realización de una copia de uno de los archivos de Windows PowerShell. Si realiza una copia de un archivo existente, elimine la firma digital existente y agregar su propia firma para el nuevo archivo.

### <a name="to-create-a-formatps1xml-file"></a>Para crear una. archivo format.ps1xml.

1. Cree un archivo de texto (.txt) con un texto editor como Bloc de notas.

2. Copie las líneas siguientes en el archivo de formato.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - El \<configuración >\</Configuration > etiquetas definen la raíz `Configuration` nodo. Todas las etiquetas XML adicionales está incluidas en este nodo.

   - El <ViewDefinitions> </ViewDefinitions> etiquetas definen el `ViewDefinitions` nodo. Todas las vistas se definen dentro de este nodo.

3. Guarde el archivo a la carpeta de instalación de Windows PowerShell, la carpeta del módulo o en una subcarpeta de la carpeta del módulo. Use el siguiente formato de nombre cuando guarde el archivo: `MyFile.format.ps1xml`. Archivos de formato deben usar el `.format.ps1xml` extensión.

   Ahora está listo para agregar vistas en el archivo de formato. No hay ningún límite al número de vistas que se pueden definir en un archivo de formato. Puede agregar una vista única para cada objeto, varias vistas para el mismo objeto o una vista única que sirve para varios objetos.

## <a name="see-also"></a>Véase también

[Escribir un formato de Windows PowerShell y los tipos de archivo](./writing-a-powershell-formatting-file.md)
