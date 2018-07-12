---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892370"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="5021b-102">Extraer y analizar objetos estructurados fuera de la cadena</span><span class="sxs-lookup"><span data-stu-id="5021b-102">Extract and Parse Structured Objects out of String</span></span>

<span data-ttu-id="5021b-103">También presenta algunas funciones adicionales para el cmdlet `ConvertFrom-String`.</span><span class="sxs-lookup"><span data-stu-id="5021b-103">This also introduces some additional functionality for the `ConvertFrom-String` cmdlet:</span></span>

- <span data-ttu-id="5021b-104">Quita la propiedad ExtentText de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="5021b-104">Removes the extent text property by default.</span></span> <span data-ttu-id="5021b-105">Se puede incluir con el parámetro -IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="5021b-105">You can include it with the -IncludeExtent parameter.</span></span>

- <span data-ttu-id="5021b-106">Muchas correcciones de errores de algoritmo de aprendizaje de MVP y de comentarios de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="5021b-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

- <span data-ttu-id="5021b-107">Un nuevo parámetro -UpdateTemplate para guardar los resultados del algoritmo de aprendizaje en un comentario en el archivo de plantilla.</span><span class="sxs-lookup"><span data-stu-id="5021b-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="5021b-108">Esto convierte el proceso de aprendizaje (la fase más lenta) en un costo puntual.</span><span class="sxs-lookup"><span data-stu-id="5021b-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="5021b-109">La ejecución de Convert-String con una plantilla que contenga el algoritmo de aprendizaje codificado es ahora casi instantánea.</span><span class="sxs-lookup"><span data-stu-id="5021b-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="5021b-110">Extraer y analizar objetos estructurados fuera del contenido de la cadena</span><span class="sxs-lookup"><span data-stu-id="5021b-110">Extract and parse structured objects out of string content</span></span>

<span data-ttu-id="5021b-111">En colaboración con [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), se ha agregado un nuevo cmdlet `ConvertFrom-String`.</span><span class="sxs-lookup"><span data-stu-id="5021b-111">In collaboration with [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), a new `ConvertFrom-String` cmdlet has been added.</span></span>

<span data-ttu-id="5021b-112">Este cmdlet admite dos modos: análisis delimitado básico y análisis controlado por ejemplos generados automáticamente.</span><span class="sxs-lookup"><span data-stu-id="5021b-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="5021b-113">De forma predeterminada, el análisis delimitado divide la entrada en el espacio en blanco y asigna los nombres de propiedad a los grupos resultantes.</span><span class="sxs-lookup"><span data-stu-id="5021b-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="5021b-114">Puede personalizar el delimitador:</span><span class="sxs-lookup"><span data-stu-id="5021b-114">You can customize the delimiter:</span></span>

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

<span data-ttu-id="5021b-115">El cmdlet también admite el análisis controlado por ejemplos generados automáticamente basado en el trabajo de investigación de [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) en [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span><span class="sxs-lookup"><span data-stu-id="5021b-115">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) research work in [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span></span>

<span data-ttu-id="5021b-116">Para comenzar, considere la posibilidad de una libreta de direcciones basada en texto:</span><span class="sxs-lookup"><span data-stu-id="5021b-116">To get started, consider a text-based address book:</span></span>

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

<span data-ttu-id="5021b-117">Copie algunos ejemplos en un archivo, que se usará como plantilla:</span><span class="sxs-lookup"><span data-stu-id="5021b-117">Copy a few examples into a file, which you will use as your template:</span></span>

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

<span data-ttu-id="5021b-118">Encierre los datos que quiera extraer con llaves y asígneles un nombre al hacerlo.</span><span class="sxs-lookup"><span data-stu-id="5021b-118">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="5021b-119">Dado que la propiedad **Name** (y sus otras propiedades asociadas) puede aparecer varias veces, use un asterisco (\*) para indicar que se generan varios registros (en lugar de extraer un grupo de propiedades en un único registro):</span><span class="sxs-lookup"><span data-stu-id="5021b-119">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

<span data-ttu-id="5021b-120">De este conjunto de ejemplos, `ConvertFrom-String` puede ahora extraer automáticamente la salida basada en objetos de los archivos de entrada con una estructura similar.</span><span class="sxs-lookup"><span data-stu-id="5021b-120">From this set of examples, `ConvertFrom-String` can now automatically extract object-based output from input files with similar structure.</span></span>

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

<span data-ttu-id="5021b-121">Para manipular datos adicionales en el texto extraído, la propiedad **ExtentText** captura el texto sin formato del que se extrajo el registro.</span><span class="sxs-lookup"><span data-stu-id="5021b-121">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="5021b-122">Para proporcionar comentarios sobre esta característica o compartir contenido que presenta dificultades para escribir ejemplos, envíe un correo electrónico a <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="5021b-122">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>