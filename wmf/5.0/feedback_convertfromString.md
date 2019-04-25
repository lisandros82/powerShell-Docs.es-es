---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085361"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Extraer y analizar objetos estructurados fuera de la cadena

También presenta algunas funciones adicionales para el cmdlet `ConvertFrom-String`.

- Quita la propiedad ExtentText de forma predeterminada. Se puede incluir con el parámetro -IncludeExtent.

- Muchas correcciones de errores de algoritmo de aprendizaje de MVP y de comentarios de la comunidad.

- Un nuevo parámetro -UpdateTemplate para guardar los resultados del algoritmo de aprendizaje en un comentario en el archivo de plantilla. Esto convierte el proceso de aprendizaje (la fase más lenta) en un costo puntual. La ejecución de Convert-String con una plantilla que contenga el algoritmo de aprendizaje codificado es ahora casi instantánea.

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a>Extraer y analizar objetos estructurados fuera del contenido de la cadena

En colaboración con [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), se ha agregado un nuevo cmdlet `ConvertFrom-String`.

Este cmdlet admite dos modos: análisis delimitado básico y análisis controlado por ejemplos generados automáticamente.

De forma predeterminada, el análisis delimitado divide la entrada en el espacio en blanco y asigna los nombres de propiedad a los grupos resultantes. Puede personalizar el delimitador:

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

El cmdlet también admite el análisis controlado por ejemplos generados automáticamente basado en el trabajo de investigación de [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) en [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).

Para comenzar, considere la posibilidad de una libreta de direcciones basada en texto:

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA
```

Copie algunos ejemplos en un archivo, que se usará como plantilla:

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

Encierre los datos que quiera extraer con llaves y asígneles un nombre al hacerlo. Dado que la propiedad **Name** (y sus otras propiedades asociadas) puede aparecer varias veces, use un asterisco (\*) para indicar que se generan varios registros (en lugar de extraer un grupo de propiedades en un único registro):

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

De este conjunto de ejemplos, `ConvertFrom-String` puede ahora extraer automáticamente la salida basada en objetos de los archivos de entrada con una estructura similar.

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

Para manipular datos adicionales en el texto extraído, la propiedad **ExtentText** captura el texto sin formato del que se extrajo el registro. Para proporcionar comentarios sobre esta característica o compartir contenido que presenta dificultades para escribir ejemplos, envíe un correo electrónico a <psdmfb@microsoft.com>.