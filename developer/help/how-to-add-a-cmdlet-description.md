---
title: Cómo agregar una descripción del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862601"
---
# <a name="how-to-add-a-cmdlet-description"></a>Cómo agregar una descripción del cmdlet

En esta sección se describe cómo agregar contenido que se muestra en la sección de descripción de la Ayuda del cmdlet. En el archivo de ayuda, este contenido se agrega al nodo de comando para cada cmdlet.

> [!NOTE]
> Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll Help.xml ubicado en el directorio de instalación de Windows PowerShell. Por ejemplo, el archivo Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenido para varios de los cmdlets de Windows PowerShell.

### <a name="to-add-a-description"></a>Para agregar una descripción

- Empiece por explicar las características básicas del cmdlet en más detalle. En muchos casos, puede explicar los términos usados en el nombre del cmdlet e ilustrar conceptos familiarizados con un ejemplo. Por ejemplo, si el cmdlet anexa datos a un archivo, explique que agrega datos al final de un archivo existente.

- Para buscar todas las características del cmdlet, revise la lista de parámetros. Describir la función principal del cmdlet y, a continuación, incluir otras funciones y características. Por ejemplo, si es la función principal del cmdlet cambiar una propiedad, pero el cmdlet puede cambiar todas las propiedades, indicarlo en la descripción detallada. Si los parámetros de cmdlet permiten a los usuarios solicitan información de maneras diferentes, se explica.

- Incluir información sobre la forma que los usuarios pueden usar el cmdlet, además de los usos obvios. Por ejemplo, puede utilizar el objeto que el `Get-Host` cmdlet recupera para cambiar el color del texto en la ventana de comandos de Windows PowerShell.

  Ejemplo:  "El `Get-Acl` Obtiene objetos que representan el descriptor de seguridad de un archivo o recurso. El descriptor de seguridad contiene las listas de control de acceso (ACL) del recurso. La ACL especifica los permisos que los usuarios y grupos de usuarios tienen acceso al recurso."

- La descripción detallada debe describir el cmdlet, pero deben describir conceptos que usa el cmdlet. Coloque las definiciones de concepto en notas adicionales.

## <a name="see-also"></a>Véase también

[Windows PowerShell SDK](../windows-powershell-reference.md)
