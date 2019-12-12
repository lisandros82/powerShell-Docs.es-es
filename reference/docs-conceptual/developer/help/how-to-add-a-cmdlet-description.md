---
title: Cómo agregar una descripción de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361284"
---
# <a name="how-to-add-a-cmdlet-description"></a>Cómo agregar una descripción del cmdlet

En esta sección se describe cómo agregar el contenido que se muestra en la sección Descripción de la ayuda del cmdlet. En el archivo de ayuda, este contenido se agrega al nodo comando para cada cmdlet.

> [!NOTE]
> Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll-Help. XML ubicados en el directorio de instalación de Windows PowerShell. Por ejemplo, el archivo Microsoft. PowerShell. Commands. Management. dll-Help. xml contiene contenido para algunos de los cmdlets de Windows PowerShell.

### <a name="to-add-a-description"></a>Para agregar una descripción

- Empiece por explicar con más detalle las características básicas del cmdlet. En muchos casos, puede explicar los términos que se usan en el nombre del cmdlet y ilustrar los conceptos desconocidos con un ejemplo. Por ejemplo, si el cmdlet anexa datos a un archivo, explique que agrega datos al final de un archivo existente.

- Para buscar todas las características del cmdlet, revise la lista de parámetros. Describa la función principal del cmdlet y, a continuación, incluya otras funciones y características. Por ejemplo, si la función principal del cmdlet es cambiar una propiedad, pero el cmdlet puede cambiar todas las propiedades, por ejemplo, en la descripción detallada. Si los parámetros del cmdlet permiten a los usuarios solicitar información de distintas maneras, explíquelo.

- Incluya información sobre las formas en que los usuarios pueden usar el cmdlet, además de los usos obvios. Por ejemplo, puede usar el objeto que el cmdlet `Get-Host` recupera para cambiar el color del texto en la ventana de comandos de Windows PowerShell.

  Ejemplo: "el cmdlet `Get-Acl` obtiene objetos que representan el descriptor de seguridad de un archivo o recurso. El descriptor de seguridad contiene las listas de control de acceso (ACL) del recurso. La ACL especifica los permisos que los usuarios y grupos de usuarios tienen para tener acceso al recurso. "

- La descripción detallada debe describir el cmdlet, pero no debe describir los conceptos que usa el cmdlet. Coloque las definiciones de concepto en notas adicionales.

## <a name="see-also"></a>Véase también

[Windows PowerShell SDK](../windows-powershell-reference.md)
