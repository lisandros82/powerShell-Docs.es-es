---
title: Cómo agregar una sección Vea también a un tema de ayuda del proveedor | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367844"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Cómo agregar una sección Consulte también a un tema de Ayuda de proveedor

En esta sección se explica cómo rellenar la sección **vea también** de un tema de ayuda del proveedor.

La sección **vea también** contiene una lista de temas relacionados con el proveedor o puede ayudar al usuario a entender mejor y usar el proveedor. La lista de temas puede incluir la ayuda de los cmdlets, la ayuda del proveedor y los temas de ayuda conceptual ("About") en Windows PowerShell. También puede incluir referencias a los libros, el papel y los temas en línea, incluida una versión en línea del tema de ayuda del proveedor actual.

Cuando haga referencia a los temas en línea, proporcione el URI o un término de búsqueda en texto sin formato. El cmdlet `Get-Help` no vincula ni redirige a ninguno de los temas de la lista. Además, el parámetro `Online` del cmdlet `Get-Help` no funciona con la ayuda del proveedor.

La sección Vea también se crea a partir del elemento `RelatedLinks` y las etiquetas que contiene. El siguiente XML muestra cómo agregar las etiquetas.

### <a name="to-add-see-also-topics"></a>Para agregar temas "vea también"

1. En el archivo *AssemblyName*. dll-help. XML, dentro del elemento `providerHelp`, agregue un elemento `RelatedLinks`. El elemento `RelatedLinks` debe ser el último elemento del elemento `providerHelp`. Solo se permite un elemento `RelatedLinks` en el tema de ayuda de cada proveedor.

   Por ejemplo:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Para cada tema de la sección **vea también** , dentro del elemento `RelatedLinks`, agregue un elemento `navigationLink`. Después, dentro de cada elemento `navigationLink`, agregue un elemento `linkText` y un elemento `uri`. Si no está utilizando el elemento `uri`, puede agregarlo como un elemento vacío (\<URI/>).

   Por ejemplo:

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. Escriba el nombre del tema entre las etiquetas de `linkText`. Si va a proporcionar un URI, escríbalo entre las etiquetas de `uri`. Para indicar la versión en línea del tema de ayuda del proveedor actual, entre las etiquetas de `linkText`, escriba "versión en línea:" en lugar del nombre del tema. Normalmente, el vínculo "versión en línea:" es el primer tema de la lista de temas vea también.

   En el ejemplo siguiente se incluyen tres temas, vea también. El primero hace referencia a la versión en línea del tema actual. El segundo hace referencia a un tema de ayuda de cmdlet de Windows PowerShell. El tercero hace referencia a otro tema en línea.

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```