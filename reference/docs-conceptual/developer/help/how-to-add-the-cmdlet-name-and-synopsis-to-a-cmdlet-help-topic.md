---
title: Cómo agregar el nombre y la Sinopsis del cmdlet a un tema de ayuda de cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361194"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Cómo agregar el nombre del cmdlet y la sinopsis a un tema de Ayuda del cmdlet

En esta sección se describe cómo agregar el contenido que se muestra en las secciones nombre y Sinopsis de la ayuda del cmdlet. En el archivo de ayuda, este contenido se agrega al nodo comando para cada cmdlet.

> [!NOTE]
> Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll-Help. XML ubicados en el directorio de instalación de Windows PowerShell. Por ejemplo, el archivo Microsoft. PowerShell. Commands. Management. dll-Help. xml contiene contenido para algunos de los cmdlets de Windows PowerShell.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Para agregar el nombre del cmdlet y un resumen

- La ayuda del cmdlet puede mostrar dos descripciones para el cmdlet. La primera descripción es una breve descripción a la que se hace referencia como Sinopsis. La segunda Descripción es una descripción más detallada que se describe en [Agregar la descripción detallada a un tema de ayuda de cmdlet](./how-to-add-a-cmdlet-description.md). Ambas descripciones deben escribirse en un solo párrafo.

- En el Resumen, no repita el nombre del cmdlet. Informar al usuario de que el cmdlet Get-Server obtiene un servidor es breve, pero no es informativo. En su lugar, use sinónimos y agregue detalles a la descripción.

  Ejemplo: "obtiene un objeto que representa un equipo local o remoto".

- Use verbos simples como "Get", "Create" y "Change" en el resumen. Evite el uso de "SET" porque es impreciso y se decoran palabras como "Modify".

  Ejemplo: "obtiene información sobre la firma Authenticode en un archivo".

- Escriba en voz activa. Por ejemplo, "usar el objeto TimeSpan..." es mucho más claro que "el objeto TimeSpan se puede usar para..."

- Evite el verbo "Mostrar" al describir los cmdlets que obtienen objetos. Aunque Windows PowerShell muestra los datos de los cmdlets, es importante introducir a los usuarios en el concepto de que el cmdlet devuelva .NET Framework objetos cuyos datos no se puedan mostrar. Si resalta la pantalla, es posible que el usuario no tenga en cuenta que el cmdlet puede haber devuelto muchas otras propiedades y métodos útiles que no se muestran.

## <a name="see-also"></a>Véase también

 [Windows PowerShell SDK](../windows-powershell-reference.md)