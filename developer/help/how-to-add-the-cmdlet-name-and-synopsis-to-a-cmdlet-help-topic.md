---
title: Cómo agregar el nombre de Cmdlet y Sinopsis a un tema de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861831"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Cómo agregar el nombre del cmdlet y la sinopsis a un tema de Ayuda del cmdlet

En esta sección se describe cómo agregar contenido que se muestra en las secciones de nombre y una sinopsis de la Ayuda del cmdlet. En el archivo de ayuda, este contenido se agrega al nodo de comando para cada cmdlet.

> [!NOTE]
> Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll Help.xml ubicado en el directorio de instalación de Windows PowerShell. Por ejemplo, el archivo Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenido para varios de los cmdlets de Windows PowerShell.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Para agregar el nombre del Cmdlet y una sinopsis

- La Ayuda del cmdlet puede mostrar dos descripciones del cmdlet. La descripción de la primera es una breve descripción que se conoce como la sinopsis. La descripción de la segunda es una descripción más detallada que se describe en [agregar la descripción detallada para un tema de Ayuda de Cmdlet](./how-to-add-a-cmdlet-description.md). Estas descripciones se deben escribir como un único párrafo.

- En la sinopsis no repetir el nombre del cmdlet. Para informar al usuario que el cmdlet Get-Server obtiene un servidor es breve, pero no informativo. En su lugar, utilizar sinónimos y agregar detalles a la descripción.

  Ejemplo: "Obtiene un objeto que representa un equipo local o remoto."

- Usar los verbos simple como "get", "crear" y "cambiar" en la sinopsis. Evite el uso de "set" porque es imprecisa y elegantes palabras como "modificación".

  Ejemplo: "Obtiene información sobre la firma Authenticode en un archivo".

- Escribir en voz activa. Por ejemplo, "usar el objeto TimeSpan..." es mucho más claro que "el objeto TimeSpan se puede usar para..."

- Evite el verbo "display" al describir los cmdlets que se obtienen los objetos. Aunque Windows PowerShell muestra los datos de cmdlet, es importante presentar el concepto de que el cmdlet devuelve objetos de .NET Framework cuyos datos no pueden mostrarse a los usuarios. Si hacer hincapié en la pantalla, el usuario podría no darse cuenta que el cmdlet devuelto muchas otras propiedades y métodos útiles que no se muestran.

## <a name="see-also"></a>Véase también

 [Windows PowerShell SDK](../windows-powershell-reference.md)