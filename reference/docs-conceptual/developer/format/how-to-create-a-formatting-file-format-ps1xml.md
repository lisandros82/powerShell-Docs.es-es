---
title: Cómo crear un archivo de formato (. Format. ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363624"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Cómo crear un archivo de formato (. format.ps1xml)

En este tema se describe cómo crear un archivo de formato (. Format. ps1xml).

> [!NOTE]
> También puede crear un archivo de formato si realiza una copia de uno de los archivos proporcionados por Windows PowerShell. Si realiza una copia de un archivo existente, elimine la firma digital existente y agregue su propia firma al nuevo archivo.

### <a name="to-create-a-formatps1xml-file"></a>Para crear un archivo. Format. ps1xml.

1. Cree un archivo de texto (. txt) mediante un editor de texto como el Bloc de notas.

2. Copie las líneas siguientes en el archivo de formato.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - Las etiquetas de configuración de \<\</Configuración > definen el nodo raíz `Configuration`. Todas las etiquetas XML adicionales se incluirán dentro de este nodo.

   - Las <ViewDefinitions></ViewDefinitions> etiquetas definen el nodo de `ViewDefinitions`. Todas las vistas se definen dentro de este nodo.

3. Guarde el archivo en la carpeta de instalación de Windows PowerShell, en la carpeta del módulo o en una subcarpeta de la carpeta del módulo. Use el siguiente formato de nombre al guardar el archivo: `MyFile.format.ps1xml`. Los archivos de formato deben utilizar la extensión `.format.ps1xml`.

   Ahora está listo para agregar vistas al archivo de formato. No hay ningún límite en el número de vistas que se pueden definir en un archivo de formato. Puede Agregar una vista única para cada objeto, varias vistas para el mismo objeto o una vista única que utilicen varios objetos.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato y tipos de Windows PowerShell](./writing-a-powershell-formatting-file.md)
