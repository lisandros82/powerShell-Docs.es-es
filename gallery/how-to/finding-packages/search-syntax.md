---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Sintaxis de búsqueda de la Galería
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003894"
---
# <a name="gallery-search-syntax"></a>Sintaxis de búsqueda de la Galería

La Galería de PowerShell ofrece un cuadro de búsqueda de texto en el que puede usar palabras, frases y expresiones de palabra clave para restringir los resultados de la búsqueda.

## <a name="search-by-keywords"></a>Buscar por palabras clave

    dsc azure sql

La búsqueda hará todo lo posible por encontrar documentos relevantes que contengan las tres palabras clave y devolver documentos coincidentes.

## <a name="search-using-phrases-and-keywords"></a>Buscar mediante palabras clave y frases

    "azure sql" deployment

Si se escribe una frase entre comillas (""), la búsqueda pasa a buscar la frase determinada en lugar de palabras clave independientes.
Los documentos coincidentes normalmente contendrán la frase exacta "azure sql", incluidas las variaciones en el uso de mayúsculas y minúsculas (por ejemplo, "Azure SQL"), y normalmente también contendrán la palabra "deployment" (implementación).

## <a name="filtering-on-fields"></a>Filtrar por campos

Puede buscar un ID de paquete específico, o "Id" o "id", u otros campos anteponiendo a los términos de la búsqueda el nombre del campo.

Actualmente, los campos que se pueden buscar son "Id", "Version", "Tags", "Author", "Owner", "Functions", "Cmdlets", "DscResources" y "PowerShellVersion".

[¿Cuál es la diferencia entre el ID y el título? El ID es el nombre que se usa en la consola. El título es lo que se muestra en la parte superior de la página del paquete en los resultados de la búsqueda].

## <a name="examples"></a>Ejemplos

    ID:"PSReadline"
    id:"AzureRM.Profile"

Busca paquetes con "PSReadline" o "AzureRM.Profile" en el campo ID, respectivamente.

    Id:"AzureRM.Profile"

Es otra manera de buscar paquetes con "AzureRM.Profile" en el campo ID.

El filtro "Id" es una coincidencia de subcadena, por lo que si busca lo siguiente:

    Id:"azure"

obtendrá resultados como "AzureRM.Profile" y "Azure.Storage".

También puede buscar varias palabras clave en un único campo, o mezclar y combinar campos.

    id:azure tags:intellisense
    id:azure id:storage

También puede buscar frases:

    id:"azure.storage"


Para buscar todos los paquetes con la etiqueta DSC.

    Tags:"DSC"

Para buscar todos los paquetes con la función especificada.

    Functions:"Update-AzureRM"

Para buscar todos los paquetes con el cmdlet especificado.

    Cmdlets:"Get-AzureRmEnvironment"

Para buscar todos los paquetes con el nombre del recurso de DSC especificado.

    DscResources:"xArchive"

Para buscar todos los paquetes con el valor de PowerShellVersion especificado.

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Por último, si usa un campo que no se admite (como "commands"), se omitirá y se buscará en todos los campos. Así pues, la consulta siguiente:

    commands:blobs storage

se interpreta exactamente igual que esta consulta:

    blobs storage
