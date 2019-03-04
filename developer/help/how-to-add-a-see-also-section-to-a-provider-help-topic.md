---
title: Cómo agregar una, consulte también sección a un tema de Ayuda de proveedor | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858351"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Cómo agregar una sección Consulte también a un tema de Ayuda de proveedor

Esta sección explica cómo rellenar el **Vea también** sección de un tema de Ayuda del proveedor.

El **Vea también** sección consta de una lista de temas que están relacionados con el proveedor o puede ayudar al usuario a comprender mejor y usar el proveedor. La lista de temas puede incluir la Ayuda de cmdlet de Ayuda del proveedor y conceptual ("about"), temas de Ayuda de Windows PowerShell. También puede incluir referencias a los libros en pantalla, papel y temas en línea, incluida una versión en línea del tema de Ayuda de proveedor actual.

Cuando se hace referencia a temas en línea, proporcione el identificador URI o un término de búsqueda en texto sin formato. El `Get-Help` cmdlet no vincular o redirigir a cualquiera de los temas de la lista. Además, el `Online` parámetro de la `Get-Help` cmdlet no funciona con la Ayuda del proveedor.

La sección Vea también se crea a partir del `RelatedLinks` elemento y las etiquetas que contiene. El siguiente XML muestra cómo agregar las etiquetas.

### <a name="to-add-see-also-topics"></a>Para agregar temas "Vea también"

1. En el *AssemblyName*archivo .dll help.xml dentro la `providerHelp` elemento, agregue un `RelatedLinks` elemento. El `RelatedLinks` elemento debe ser el último elemento en el `providerHelp` elemento. Solo un `RelatedLinks` elemento está permitido en cada tema de Ayuda del proveedor.

   Por ejemplo:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Para cada tema de la **Vea también** sección dentro la `RelatedLinks` elemento, agregue un `navigationLink` elemento. A continuación, dentro de cada `navigationLink` elemento, agregue uno `linkText` y un elemento `uri` elemento. Si no usa el `uri` elemento, puede agregarlo como un elemento vacío (\<uri / >).

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

3. Escriba el nombre del tema entre el `linkText` etiquetas. Si va a proporcionar un URI, escríbalo entre el `uri` etiquetas. Para indicar la versión en línea del tema de Ayuda de proveedor actual, entre el `linkText` etiquetas, escriba "versión en línea:" en lugar del nombre del tema. Normalmente, la "versión en línea:" vínculo es el primer tema de la lista de temas de Vea también.

   El ejemplo siguiente se incluyen tres temas de Vea también. La primera hacen referencia a la versión en línea del tema actual. El segundo se refiere a un tema de Ayuda de cmdlet de Windows PowerShell. La tercera hace referencia a otro tema en línea.

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